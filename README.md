# Morea Version 2.0

This repository contains the code for Version 2.0 of the Morea Framework.

## Improvements in 2.0 include:
  * New Morea sites are created by using this repo as a "template". Although this repository is public, you can make your copy of the repo private.
  * You do not need to maintain a master and gh-page branch in your local file system.
  * Compatible with Jekyll 4.2.0
  * To run site locally, invoke with standard jekyll command: `bundle exec jekyll serve --baseurl '' -q`
  * config.yml file provides flexible output support via log levels.
  * GitHub Action used to automatically deploy site upon commit.

## How to configure deployment for a new site:
 * Edit config.yml to make sure baseurl is the repo name.
 * Settings | Pages, enable github pages.
 * Push the repo.
 * Check to see that the action completed successfully.
 * Check the url (username.github.io/reponame)

## Version 2.0 To Do List
 - [ ] Rebuild documentation using docusaurus.
 - [ ] Fix markup to use Bootstrap 5.
 - [ ] Rebuild custom Bootswatch themes.
 - [ ] Create "realistic" demo site: four modules, one per week, includes prereqs, sets schedule page start month.
 - [ ] Include more include files into template, document in docusaurus.
 - [ ] Remove scrollIfAnchor.js if possible? (core.html).
 - [ ] Deployed template at: https://morea-framework.github.io/morea/index.html


## To check site for HTML link errors etc.

```
$ bundle exec jekyll build --baseurl ''
$
