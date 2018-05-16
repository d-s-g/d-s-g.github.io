Full builds and features
    Go2triad (link to jobs portal)

    Who is Go2triad?
    Go2traid is a talent recruitment agency based in Colorado.
    
    What was the problem?
    Their previous jobs portal would not run, and content had to
    be entered manually. This was a headache for the client.

    How did I solve it?
    I built a Jobs portal that integrates with the bullhorn api.
    This was an existing WordPress site built by another development
    company. 

    We chose liquidweb cloudsites and before building the
    application I had to: 
    
    - Move the site to new hosting
    - Set up staging server
    - Set up production server
    - Update DNS to point to the new production site

    Once this was complete, I could then build the frontend.
    The front end was straight forward, we used facetwp
    to allow for quick ajax searches. Unlike the prodigyr solution
    (link) this solution did not need any state management. Thus, 
    It was a much simpler solution.