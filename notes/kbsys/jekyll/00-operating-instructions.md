---
SRID: '0000:2019:0901:2241'
---
## Jekyll Operation Guide

### Running Development Server

* Start the jekyll dev server: `bundle exec jekyll server --host 0.0.0.0`^1
* Browse to `localhost:4000`. If you need the local ip: `ipconfig getifaddr en1`

[^1]: why use `bundle exec` instead of just `jekyll` https://yehudakatz.com/2011/05/30/gem-versioning-and-bundler-doing-it-right/)

Now you can **create and edit pages** by creating them anywhere in the root folder. Avoid using the `_` underscore character in folder names, as these will be note be processed as content by Jekyll.

## Deploying Online

The **static site** is deployed to `io.davidseah.com`, which is hosted on **Github Pages** in the `daveseah.github.io` repository. Push the content of the Jekyll files to that repo  with SourceTree or the Git command line. Github will automatically try to deploy the pages. 

To **test** the files, use 

The **image server** that handles image resizing is hosted at `davidseah.net` by a Node ExpressJS app implementing Lazy Image Layout. This is a *SEPARATE* repo from the Jekyll site. To update this site, 

## Assets Directory

Site-wide static assets go into `assets`. 

## Images

Upload files to `davidseah.net/app/_docroot/images`.

* To retrieve the source image, use the normal url as uploaded to the 'images/' directory through an SFTP transfer agent.
* To retrieve a thumbnail, fetch the file from the 'cache/' and append @width before the file extension.

Example for a JPEG file uploaded to images/19/0805-lrc-03.jpg:
`<img src='https://davidseah.net/images/19/0805-lrc-03.jpg'>`

Example for generated thumbbnail of the same file that is scaled to 320px wide:
`<img src='https://davidseah.net/cache/images/19/0805-lrc-03@320.jpg'>`

Note that the thumbnail is always a JPEG file with the extension '.jpg'.

