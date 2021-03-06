---
SRID: '0000:2019:0810:0542'
---
# How to do UNIFIED NAVIGATION

_site/bulletin/001-job.html
turns into
_site/bulletin/001/
.. index.html 
.. work.html
.. extra.html
.. contact.html

page.url variable holds the currenturl
can compare to data in an item.url to add a class on loop.

index.html
navigation section on left
content section on right

layout.html is called from page
  #nav includes page variable that (1) is NAVIGATION
  #content gets {{ content }} for normal content
   
  data could come from
  [=] page.var - but page var changes on each page
  [ ] _data directory 
  [ ] _include `


REFERENCES BELOW

# VARIABLES

site
page
layout
content

includes have include.* inside of them, used to access passed variables
can also access site and page content, but not 


# INCLUDE
{% raw %}

FROM INCLUDES FOLDER (_includes)
{% include footer.html %}

FROM RELATIVE FOLDER
{% include_relative somedir/footer.html %}

FROM PAGE VARIABLE
---
title: My page
my_variable: footer_company_a.html
---
{% if page.my_variable %}
  {% include {{ page.my_variable }} %}
{% endif %}

INSERT PARAMETER
html in include template
<div markdown="span" class="alert alert-info" role="alert">
<i class="fa fa-info-circle"></i> <b>Note:</b>
{{ include.content }}
</div>
call from page
{% include note.html content="This is my sample note." %
{% endraw %}

# TEMPLATE

FROM LAYOUT (_layout)
use `layout:` front matter and specify name of file

The layout will receive {{content}} global variable from the calling page or post, which is everything after front matter.

Layouts can access page object front matter, site object, and 

# CAPTURING OUTPUT
this is how you do stringconcat

{% raw %}

capture
{% capture my_variable %}I am being captured.{% endcapture %}

emit variable
{{ my_variable }}

{% assign my_variable = false %} also works

# MISC
filters
{{ "/my/fancy/url" | append: ".html" }}
comments
{% comment %} and {% endcomment %} 
{% endraw %}

# DATA

FROM DATA (_data)
in _data/folder/blah (YAML, JSON, CSV, and TSV)
e.g. _data/members.yml
access with (if there are subdirectories, will get a 'hash'
of all filenames)
{% raw %}
{% for member in site.data.members %}
    <a href="https://github.com/{{ member.github }}">
      {{ member.name }}
    </a>
{% endfor %}

access element inside the data
{{ site.data.people['dave']}} 
{% endraw %}


# NAVIGATION

DATA FILE

docs_list_title: ACME Documentation
docs:

- title: Introduction
  url: introduction.html

- title: Configuration
  url: configuration.html

- title: Deployment
  url: deployment.html

LIQUID

{% raw %}
<ul>
   {% for item in site.data.samplelist.docs %}
      <li><a href="{{ item.url }}">{{ item.title }}</a></li>
   {% endfor %}
</ul>

adding hilighting

<ul>
    {% for item in site.data.samplelist.docs %}
    <li class="{% if item.url == page.url %}active{% endif %}">
      <a href="{{ item.url }}">{{ item.title }}</a>
    </li>
    {% endfor %}
</ul>
{% endraw %}
