# Developer Documentation

Developer documentation for AllSeen released projects are located under the developer tab on http://allseenalliance.org (hereafter referred to as the Developer Website). The source content (text, images, source of images) used to render this html content is stored in the [webdocs git project](https///git.allseenalliance.org/cgit/extras/webdocs.git/).

As such, content in the webdocs project need to be updated when releasing a new feature or project. This page describes the workflow and details for accomplishing this.

## Overview

The entire Developer Website can be built from the webdocs project. The standard [AllSeen Gerrit-based review workflow](https///wiki.allseenalliance.org/develop/contributing_source_code) is used to upload and approve contributions to the webdocs project, just like code contributions. Like code contributions, anyone can upload commits, but only webdocs project approvers can approve. The list of approvals is listed below.

The current content in the master branch is imported into the Developer Website on a daily basis.  Feature branches are used to hold documentation on yet-to-be-released code, and merged into master when released. Staging branches may be created to assist in coalescing all changes for an upcoming release. Email the documentation team (see below) if you'd like a feature or staging branch created.

The webdocs project contains scripts to preview the content changes before committing to Gerrit. Refer to the README.md file at the root of the webdocs project for information about running these scripts.

## Developer content

The organization of content is not fixed. As the project grows, so must the organization of the developer content. Take a look at the content to get a better feel of the organization. As of Nov 2014, here are some highlights of the current organization. The bolded sections are areas that most likely will need to be updated when a new feature/service is added.


*  Learn -- describes the software and projects concepts at the high level.
    * Use Cases -- describes use cases
    * Architecture -- describes the AllJoyn architecture
    * Core Framework -- info about the core framework and concepts
    * Base Services -- info about base services and concepts, including interface definitions
    * `<new WG/Services>` -- for each new service, follow the conventions in base services, include **interface definition**.
    * Glossary -- the glossary

*  Download -- provides information about downloading software

*  Develop -- info on using the software
    * **Building** -- info on how to build
    * **Running Sample Apps** -- info on how to run the sample apps
    * **API Guides** -- info on how to use the API 
    * **API Reference** -- specific info about each API
    * ​​Debug -- info on how to debug
    * Tutorial -- soup to nuts tutorials to do specific things
    * Ask -- link to the Ask forums

*  Contribute -- info about how to contribute to this project

When adding a new feature or service, update the above listed sections as appropriate for a developer to learn and use the new service or feature.  In general, follow the organization as a guideline and propose changes to the documentation mailing list (see below) if the organization needs adjustments.

## webdocs project details

The webdocs project contains:

*  docs/ -- each html page in the Developer Website corresponds to a markdown formatted text file in the docs/ dir. Files are organized in directories to mirror its URL path when imported.

*  files/ -- stores images used on the Developer Website

*  images_src/ - stores the source of abovementioned images

*  docs/nav.yaml -- defines navigation/organization, in yaml format.

*  scripts/ -- scripts to preview html generated content

All content is written in github flavored Markdown format. Refer to [online tutorials](https///help.github.com/articles/markdown-basics/) for examples on how to format, including examples of how to link to other pages, add and link to images, creating tables, annotate text as code, headers, bold, italics, etc. 

docs/path/to/dir/index.md is special.  It is what will be rendered at http://server/path/to/dir/.

When adding new pages, be sure to update docs/nav.yaml so that your page is exposed on the navigation system.

A good workflow is to edit in your favorite editor (note, many popular editors like vim, emacs, and Sublime Text properly format Markdown files), run the preview scripts, and review in a browser. Refer to the [README.md (in the project)](http://git-seattle.quicinc.com/?p=allseen/extras/webdocs.git;a=blob;f=README.md) for more information about running the scripts.

## API Reference

API Reference documentation are special. They are generated from code annotations using various tools depending on platform, like Doxygen, javadocs, and appledocs and uploaded to the Drupal webserver. If you need to make changes to these docs, email the mailing list.

## Staging Server

The webdocs content gets first pushed to a Staging server before being pushed to the Production server. The staging server is https://stage.allseenalliance.org with the below credentials.


*  username: allseenstg

*  password: ASAStageSiteAccess!!!

## Approvers

Here is the list of approvers.


*  George Nash, Qualcomm Connected Experiences

*  Brian Spencer, Qualcomm Connected Experiences

*  Jan Lissens, Technicolor

## Need Help?

If you have questions, send email to [tech-documentation@allseenalliance.org](mailto/tech-documentation@allseenalliance.org)

