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

What have we learned today:

Having a MoreaPage and a ModulePage as separate things now seems problematic.

The module page has this structure:

```
---
[ModulePage index.html
@site: #<Jekyll::Site:0x00007f935e501c68>
@relative_path:
@content: <div class="breadcrumb-bar bg-primary">
  <div class="container">
    <ol class="breadcrumb">
      {% if site.morea_head_breadcrumb_link %}
      <li...
@data: {"layout"=>"default", "morea_page"=>
---
[MoreaPage module-ethics.md
@site: #<Jekyll::Site:0x00007f935e501c68>
@relative_path:
@content: <p>Ethics: A...
@base: /Users/philipjohnson/github/morea-framework/morea
@dir: modules/ethics
@name: index.html
@path: /Users/philipjohnson/github/morea-framework/morea/ethics/index.html
@ext: .html
@basename: index
---
],
```

It has a morea_page data field where the content is `<p>Ethics...`. Also, unlike regular MoreaPages, there's no output field (maybe because we don't call render?

There is a fundamental question here: why is the textual content of the experience-ethics-technical-essay.md field being output into the modules/ethics/index.html file?

Documentation:
  * https://www.rubydoc.info/gems/jekyll/4.2.0/Jekyll/Page

Does MoreaPage return a new Page, but MoreaModule does not from #initialize()

Looks like what changed is the calculation of relative_path.  We should try setting it manually in MoreaPage.
We should print the state of ALL pages just prior to rendering. Provide a custom "inspector" that shows all fields of all pages. Call it the PageInspector that returns a formatted string.

We want the initializer for MoreaPage and ModulePage to be as close to Page as possible.

The essential question:
  * How do we initialize the state of a Jekyll::Page so that when it is rendered, the right thing happens?
  * We do this via the initialize() method, which needs to mimic the real one as much as possible.
  * We also need a way to detect whether or not we're doing it right. To do that, we need a PageInspector method that shows the state of all pages in site.pages (that helps us compare our pages to regular pages.)

We're getting somewhere:
  * Can run with either 4.1 or 4.2.  Probably within same directory:
    - delete Gemfile.lock.
    - edit Gemfile
    - run bundle install
    - bundle exec jekyll ....

With 4.1, the morea module page does not have a relative_path variable. But in 4.2 it does.

1. Confirm can run 4.1 or 4.2 in same directory.
2. Checkpoint morea.
3. Run 4.1, compare output for experience and module.

Output comparison:

* 4.1: 18 and 11 instance variables, increased to 21 and 12 in 4.2.
* relative_path instance var empty in 4.2 for both experience and module.
* 4.2: module has a "@renderer" instance var and no @output, experience has the @output but no @renderer.

Next step:
  * Update ModulePage#initialize.
  * Revert processMoreaFile to original version.
  * Run to see what happens.
  * Potentially add relative_dir instance var value, although that does not seem like the problem anymore.