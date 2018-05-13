---
layout: post
title: Keystone elm portfolio.
description: A portfolio built using a headless keystone js backend with a elm js frontend.
image: assets/images/morina-home.png
permalink: keystone-elm
---

Elm is a front end framework much like react-redux or vue-vuex. These frameworks use unidirectional data binding architectures as a solution for managing application state for more complicated ux. 

These front end frameworks do this by separating the runtime, from the core of the program.
The application uses a store (vuex or redux) and this holds the state of the application. When an event happens on the page the event triggers a prop(react) or a mutation(vue) to update the store. Then this updates the state of the application.

Elm works the same way. The runtime is separated from the elm program. When an event happens on the page a message is sent to an update function which triggers a function that updates the state and changes the application.

The bonus that elm gives is the strong typing and the complied functional language.
The benefit that this is that the data of the application is typed. This means the chance of side effects and bugs happening in the runtime is greatly reduced.

With all this in mind I built a portfolio for a phd student. Talking with the client I was asked to make a site that was easy to add content and could show published works and work interests. I felt that this was a good use case for a headless cms with a custom front end.

The headless cms chosen was keystone js. Get getting the api endpoint was set up was easy and this is consumed by the elm application. 

We will talk about 2 things - How the application displays its initial post list and how the application controls routes. By doing this, we hope to display our knowledge of elm and how  unidirectional data binding works in general. 

## Initial state

The initial state of the application handles the request and consumption of the keystone api endpoint. A list of posts is served as a JSON api by the keystone backend at `api/posts/list`.

On init of the application we fetch this list of posts. These posts are served as an agnostic type. There is no typing in keystone and nothing added to the api to tell elm what sort of data is being served on end point.

So when we get our data from the JSON end point, we need to let elm know what type of data is being consumed, to do this elm has the concept of decoding the type of data into an elm type.

Our Post data type looks like this.

```elm
type alias Content =
    { brief : String
    , extended : String
    }

type alias CloudImage =
    { secure_url : String  
    }
    
type alias PostId = 
    String 

type alias PostSlug =
    String

type alias Post =
    { id : PostId
    , slug : PostSlug
    , image : CloudImage
    , title : String
    , publishedDate : String
    , content : Content
    }
```

Which we decode using this function.

```elm
postsDecoder : Decode.Decoder (List Post) 
postsDecoder =
    Decode.list postDecoder

postDecoder : Decode.Decoder Post
postDecoder = 
    decode Post
        |> required "_id" Decode.string
        |> required "slug" Decode.string
        |> required "image" imageDecoder
        |> required "title" Decode.string
        |> required "publishedDate" Decode.string
        |> required "content" contentDecoder 
```

At this point we have our consumed our api, now we need to display our data on the frontend.
To understand how this works we need to understand how state is managed in elm.

First the program runs with this code

```elm
main : Program Never Model Msg
main =
    Navigation.program Msgs.OnLocationChange
        { init = init
        , update = update
        , view = view
        , subscriptions = subscriptions
        }
```

This program calls the init function below, which takes the location..

```elm
init : Location -> ( Model, Cmd Msg )
init location =
    let
        currentRoute = 
            Routing.parseLocation location
    in 
        ( initialModel currentRoute, fetchPosts )
```
Passes it to a Routing program. Notice that this function contains scope. Where currentRoute is defined as the current location passed to this function. This scope does not leak from this function.

## Routing

A Route is an elm type that is defined like this 

```elm
type Route
    = HomeRoute
    | PostSingleRoute PostSlug
    | ContactRoute
    | NotFoundRoute
```

These are the different routes of our application. As this is the init of the application we are only focusing on the `HomeRoute`
In the init function call above `init : Location -> ( Model, Cmd Msg )` we see that the `Model` of the application is returned.

This uses the `Model` type. A model in elm is the current model (state) of the application. Our `Model` type looks like this

```elm
type alias Model = 
    { posts : WebData (List Post)
    , route : Route
    , changes : Int
    , info : String
    }
```

Our model contains a list of posts decoded from the API. The current route, the number of times the route changed. To parse the route we look at the parseLocation function.

```elm
parseLocation : Location -> Route
parseLocation location = 
    case (parsePath matchers location) of
        Just route ->
            route
        
        Nothing ->
            NotFoundRoute
```
This function returns the route, which in our case is `/` or the `NotFoundRoute` which handles 404s. This finally allows us to call `( initialModel currentRoute, fetchPosts )`

which passes the `homeRoute` `/` to the `initalModel` and also calls `fetchPosts` which was explained in more detail above, 

```elm
fetchPosts : Cmd Msg
fetchPosts =
    Decode.field "posts" postsDecoder
    |> Http.get fetchPostsUrl
    |> RemoteData.sendRequest
    |> Cmd.map Msgs.OnFetchPosts
```

a function that gets the data from the `fetchPostsUrl`. Sends the request and triggers a message or `Msg` to the `update` function,

```elm
update : Msg -> Model -> ( Model, Cmd Msg )
update msg model =
    case msg of
        Msgs.OnFetchPosts response ->
            ( { model | posts = response }, Cmd.none )
        
        Msgs.ChangeLocation path ->
            ( { model | changes = model.changes + 1}, newUrl path )

        Msgs.OnLocationChange location ->
            let
                newRoute = 
                    parseLocation location
            in
                ( { model | route = newRoute }, Cmd.none )
        Msgs.ImageLoaded ->
            ( { model | info = "Image loaded successfully!" }, Cmd.none )
```

Which updates the model to contain the List of posts `{ model | posts = response }`
and finally allows us to call the view function, and begin the rendering of the posts on the page.

```elm
view : Model -> Html Msg
view model = 
    div []
        [ viewHeader model
        , page model
        , viewFooter model
        ]
```

The view function takes the model and passes it to 3 functions. The `viewHeader` and `viewFooter` functions which renders the header and footer and the `page` function which renders the page views. Let us look at the `page` function.

```elm
page : Model -> Html Msg
page model =
    case model.route of
        Models.HomeRoute ->
            Posts.List.viewPosts model.posts

        Models.PostSingleRoute slug ->
            Posts.Single.postSinglePage model slug

        Models.ContactRoute ->
            Contact.View.view

        Models.NotFoundRoute -> 
            notFoundView
```

The page function is passed the model from the view function and using . notation checks the 
route with a case statement. We are rendering `Models.HomeRoute` so we trigger 
`Models.HomeRoute -> Posts.List.viewPosts model.posts` which takes the post list and renders them to the page.

Thus to render our application, our event graph looks like this


This is the common pattern for unidirectional data flows. An event happens, we pass the event to a function that updates the store and based on our new state we render out our new view. My next project will be exploring how vue and vuex work together to handle state on a map.

To view this project please go to my github 
[here](https://github.com/d-s-g/keystone-elm-joe-morina){:target="_blank"}, and view the test domain [here](https://keystone-elm-joe-morina.herokuapp.com/){:target="_blank"}.
