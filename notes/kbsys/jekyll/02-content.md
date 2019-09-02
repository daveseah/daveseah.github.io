---
SRID: '0000:2019:0902:0050'
---
# io.davidseah.com content guide

### Adding a Page

Just create a markdown file with the `.md` extension anywhere in a folder/file with `_` characters. Also add a `SRID` to the front matter for the future.

### Adding a Multi-Page Job Description

Multi-page jobs are created by creating a `.yml` file in the `_data/jobmeta/` directory. This is the format of the `001.yml` file.
``` yaml
---
header: "Javascript Coders Wanted"
posted: "Job posted August 4, 2019"
canonical: "/bulletin/001-job"
email: "someone@someplace.com"
twitter: "@twitterhandle"
nav: 
-   title: 1. Job Description
    url: /bulletin/001-job/page1-description
-   title: 2. Project Details
    url: /bulletin/001-job/page2-details
-   title: 3. Extras
    url: /bulletin/001-job/page3-extra
-   title: Contact Dave
    url: /bulletin/001-job/page4-contact
---
```

You then create the set of files specified in the `nav` section. 

* Create a folder and add your pages (e.g. `bulletin/001-job`)
* Create pages with the front matter property `layout: job` and `jobmeta: "001"`. The `jobmeta` property refers to the file in `_data/jobmeta` which is used to generate the page navigation.

The **canonical url** in the jobmeta .yml file is the folder that contains the .html files. You can have this redirect to a specific file by creating an `index.md` file containing this front matter:
``` yaml
---
layout: redirect
redirectTo: "page1-description"
---
```

### Assets Directory

Site-wide static assets go into `assets`. For images, see below.

### Adding Images

I can upload image files to `davidseah.net` in the `images` directory in either JPEG or PNG format. (see the Plesk NodeJS configuration for the upload directory).

If you uploaded a file to `images/19/0805-lrc-03.jpg`, use the special LZIL INCLUDE in your page file:

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

| param | options | notes |
|:---|:---|:---
| style | 'left', 'right' | (default left) classes defined in `assets/css/style.css` 
| imgsize | `integer` | (default 3) image width  as in `1/imgsize * fullWidth`, where fullWidth is defined in `include/LZIMG` as 500. 
| nopopup | true, false | (default false) whether to implement popup (unimplemented) 
| caption | 'caption string' | set the `title` attribute 
| alt | 'image description' | set the `alt` attribute for screen readers 
