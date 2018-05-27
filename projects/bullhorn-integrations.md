---
layout: post
title: Bullhorn Wordpress api integrations
description: 
# image: assets/images/pic11.jpg
nav-menu: true
permalink: projects/bullhorn-integrations
---

### What is a bullhorn integration?
Bullhorn is a staffing and recruitment software platform. This platform helps clients with the creating and managing of jobs. It is used mostly by recruitment agencies.

### What was the problem?
Clients often ask for bullhorn to be integrated with their wordpress sites, or for an existing integration to be fixed or upgraded.

This involves either integrating with a bullhorn client service, or integrating with the api and building a custom solution. I have done both, the first can be seen
[here](http://www.toplawjobs.com/search-jobs/#/jobs){:target ="_blank"}

The second example is below. I have done two of these api integrations. One for prodigyR and one for go2triad. Both are Denver based IT recruiting firms and use the same development workflow, therefore, I have shown the work flow below.

### How was bullhorn integrated into these sites?
For both sites, I built a Jobs portal that integrates with the bullhorn api.
These were existing WordPress sites built by other development
companies.

We used a cron task to hit a php file in the wp_bullhorn plugin
that would then make a call to the api and pull in new bullhorn
jobs. We had to move from existing hosting to a new host that
allowed us to run the cron task. 

We chose liquidweb cloudsites and prior to building the
application I needed to: 

- Move the site to new hosting
- Set up staging server
- Set up production server
- Update DNS to point to the new production site

Once this was complete, I could then build the frontend.
This was mostly straight forward and so we used facetwp
to allow for quick ajax searches. The only tricky component was
managing the state on the front end of the application.

The initial jobs page was on /jobs, however, the facetwp plugin
ran on an internal page. I needed to capture this initial state
and pass it to the facetwp plugin as query variables. This took
some minor reverse engineering, but ended up being successful.

You can view an example of a completed integration for prodigyR below:

<a href="https://prodigyr.com/featured-jobs/" class="button" target="_blank" rel="noreferrer">View prodigyR</a>