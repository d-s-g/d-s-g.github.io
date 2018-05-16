What is ChenMed?

ChenMed is a senior healthcare provider in the US healthcare market.
They have 3 main brands that serve different markets in the united states.
JenCare Senior medical centers (Virginia, Georgia, Illinois, Kentucky and Louisiana)
Chen Senior medical centers (Miami Florida)
Dedicated Medical centers (Tampa Bay Florida, Lakeland Florida)
ChenMed also has 3 internal business sites that were worked on.

Development Environment
ChenMed is a large Drupal 8 project, with 2 different multi-sites at its core.
1 external and 1 internal as well as supporting apis.
The frontend of the site is sass - es6 - twig. 

My Role in the project 2016 - 2017
My role in the project was a support and feature developer.
This includes everything from small sass fixes to building and
consuming apis.

The highlights
In chronological order
Leadership Team (screenshot)
    I built and architected the implementation of a leadership team by market.
    This includes a leadership content type. Rendering content by leadership taxonomy name
    linking to the page from the Market landing page. Templating with twig and styling the content
    with sass.
News Feature (screenshot)
    I built and architected the implementation of a newsroom.
    This uses the defualt Article content type. Rendering content by sub taxonomies
    Templating with twig and styling the content
    with sass.
Our Locations Map Paragraph (our centers map)
    I built and architected a paragraph module. This module has 2 states. A locations state
    where each location is displayed in list view and the 
    link directs the user to the 'brands relevant location page'
    The second state is the one displied at "link to winning physicains"
    where the map shows as a view and the links direct the user to jobs.
    Moreover, to make things a little more challanging. The map needed to pull in correct location
    data from the correct brand. That is locations on JenCare display jencare locations, chenmed 
    displays all etc. To do this I needed to accessed a locations api built by a senoir dev
    and pulled in the correct location data by brand. Then based on the what state the user passed 
    to the drupal backed. This would trigger a different display state, styling and use different data
    from the internal api.
Api which pulls care provider data from all brands to an internal resource.
    architected by a senoir dev but implemented by me. This interal api uses the drupal module
    json api, which creates a simple paginated json api from a drupal content type. Using this
    api endpoint I implemented (find node create hook) to create new care providers in an internal
    drupal 8 site. This program checked (find things that it checked maybe add psudocode?)
    and then created a list of care providers that then were listed out in a prebuilt frontend list.
Moved Landing page paragraphs to internal resource
    ???
Events List rebuild
    I built and architected the implementation of a newsroom.
    This uses the defualt Article content type. Rendering content by sub taxonomies
    Templating with twig and styling the content
    with sass.
