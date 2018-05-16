Wraith
    
    What was the problem?
        As project scope increased on ChenMed a increased layer of testing was needed before
        deploys.

    How does wraith work?
        Wraith (link to github) is a visual regression tool that is used to crawl websites
        and take screenshots of the webpages at different breakpoints. It is built on ruby and 
        uses different headless browsers as the engine.

    Why was wraith chosen?
        Wraith was chosen because of its recommendation by pantheon(link). The other reason
        wraith was used was an incomming pr with headless chrome(now merged), and because 
        chenmed was built on flexbox. I needed to find VRT with phantomjs beta support.

    How is me building out with wraith help the team?
        This testing layer was using visual regression testing an allowed us to 
        seemlessly trasnistion between integration phase(develop) - testing phase(master) - deployment phase(release) 
        allowing the teammembers to get a headstart on the next sprint.
        It has also been dockerized (link to docker project upgrade to headless chrome?) by myself 
        to simplify spin up time with docker-compose.