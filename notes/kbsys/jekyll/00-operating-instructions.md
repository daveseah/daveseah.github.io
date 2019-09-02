---
SRID: '0000:2019:0901:2241'
---
# io.davidseah.com operations guide

### Running Development Server

* Start the jekyll dev server: `bundle exec jekyll serve --host 0.0.0.0 --incremental --livereload`
* Browse to `localhost:4000`. 
* If you need the local ip: `ipconfig getifaddr en1`

Now you can **create and edit pages** by creating them anywhere in the root folder. Avoid using the `_` underscore character in folder names, as these will be note be processed as content by Jekyll.

To use **images** in pages, see the eponymous section below.

### Deploying Online

The **static site** is deployed to `io.davidseah.com`, which is hosted on **Github Pages** in the `daveseah.github.io` repository. Push the content of the Jekyll files to that repo  with SourceTree or the Git command line. Github will automatically try to deploy the pages. 

To **test** the files, use 

The **image server** that handles image resizing is hosted at `davidseah.net` by a Node ExpressJS app implementing Lazy Image Layout. This is a *SEPARATE* repo from the Jekyll site. To update this site, 

### Assets Directory

Site-wide static assets go into `assets`. 

### Using Images

You can upload image files to `davidseah.net/app/_docroot/images` in either JPEG or PNG format. If you uploaded a file to `images/19/0805-lrc-03.jpg`, use the special LZIL INCLUDE in your page file:

```
{%raw%}
{% include LZIMG src='19/0805-lrc-03.jpg' 
   style='left' nopopup=false
   caption="optional caption goes here"
   alt="a picture of a something"
%}
{%endraw%}
```

Currently the supported `LZIMG` options are:

| param | options | notes 
|:---|:---|:---
| style | 'left', 'right' | (default left) classes defined in `assets/css/style.css`
| imgsize | `integer` | (default 3) image width  as in `1/imgsize * fullWidth`, where fullWidth is defined in `include/LZIMG` as 500.
| nopopup | true, false | (default false) whether to implement popup (unimplemented)
| caption | 'caption string' | set the `title` attribute 
| alt | 'image description' | set the `alt` attribute for screen readers


