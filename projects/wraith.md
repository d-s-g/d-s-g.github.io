---
layout: post
title: Wraith Visual Regression Tester
description: 
image: assets/images/wraith.png
nav-menu: true
permalink: projects/wraith
---
    
### What was the problem?
As project scope increased on ChenMed a increased layer of testing was needed before deploys.

### How does wraith work?
[Wraith](https://github.com/BBC-News/wraith){:target="_blank"} is a visual regression tool that is used to crawl websites
and take screenshots of the webpages at different breakpoints. It is built on ruby and 
uses different headless browsers as the engine.

### Why was wraith chosen?
ChenMed was built on flexbox. I needed to find visual regression tester with phantomjs beta support. Wraith was chosen because of a recommendation by 
[pantheon](https://pantheon.io/docs/guides/visual-diff-with-wraith/){:target="_blank"}. Wraith also had an incoming pull request with headless chrome (now merged) which allowed for future frontend technologies to be tested. 

### How is me building out with wraith help the team?
This testing layer was using visual regression testing an allowed us to 
seamlessly transition between integration phase(develop) -> testing phase(master) -> deployment phase(release) allowing the team members to get a head start on the next sprint.