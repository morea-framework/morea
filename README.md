# Morea Version 2.0

This repository contains the code for Version 2.0 of the Morea Framework.

Differences include:

  * New Morea sites are created by using this repo as a "template". Although this repository is public, you can make your copy of the repo private.

  * You do not need to maintain a master and gh-page branch in your local file system.

Things to do:

 - [ ] Docusaurus documentation
 - [ ] GitHub Action to build the site.
 - [ ] Bootstrap latest version 5
 - [ ] Bootswatch latest version
 - [ ] Don't print warnings unless -warnings in site config?
 - [ ] Don't print "processing file" unless verbose in site config?
 - [ ] Consider jekyll hooks (https://jekyllrb.com/docs/plugins/hooks/) to get rid of warning on build regarding schedule-info.js.
 - [ ] Demo site should be four weeks, one module per week, with prerequisites.
 - [ ] Include all include files into template, document in docusaurus.
 - [ ] Do we still need scrollIfAnchor.js? (core.html).


Advantages of 2.0:

 - [ ] No scripts
 - [ ] Runs on Windows as well as Unix.
 - [ ] Simpler install and development cycle.
 - [ ] Less need to understand git and git branching.


Deployment:

 * Edit config.yml to make sure baseurl is the repo name.
 * Settings | Pages, enable github pages.
 * Push the repo.
 * Check to see that the action completed successfully.
 * Check the url (username.github.io/reponame)
