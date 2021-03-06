---
layout: post
title: prodigyR jobs portal
description: 
image: assets/images/pic11.jpg
nav-menu: true
permalink: projects/prodigyr
---

### Who is prodigyR?
prodigyR is a talent recruitment agency based in Colorado, USA.

### What was the problem?
Their previous jobs portal would not run, and content had to
be entered manually. This was a headache for the client.

How did I solve it?
I built a Jobs portal that integrates with the bullhorn api.
This was an existing WordPress site built by another development
company. 

We used a cron task to hit a php file in the wp_bullhorn plugin
that would then make a call to the api and pull in new bullhorn
jobs. We had to move from existing hosting to a new host that
allowed us to run the cron task. 

We chose liquidweb cloudsites and before building the
application I had to: 

- Move the site to new hosting
- Set up staging server
- Set up production server
- Update DNS to point to the new production site

Once this was complete, I could then build the frontend.
The front end was mostly straight forward, we used facetwp
to allow for quick ajax searches. The only tricky thing was
managing state on the front end of the application.

The initial jobs page was on /jobs however, the facetwp plugin
ran on an internal page. So I needed to capture this initial state
and pass it to the facetwp plugin as query variables. This took
some minor reverse engineering, but ended up being successful.


    

