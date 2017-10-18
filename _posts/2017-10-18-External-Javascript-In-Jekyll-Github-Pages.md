---
layout:             "post"
title:              "External Javascript in Jekyll-based Github Pages"
add_brython:        "true"
add_brython_stdlib: "true"
---

{% include header.html %}

This post is a test of using external Javascript code in Jekyll-based Github pages.&nbsp;  As such, credit is due before I even begin.&nbsp; 
Specifically, this material has been shamelessly copied from a similar post by [Emma Tosch](http://blog.emmatosch.com/2016/03/09/using-custom-javascript-in-jekyll-blogs.html).&nbsp; 
Thanks to her for the insights

To wit, the procedure for using any external Javascript sources is, as follows:

(1) Add source link specifications to your *_includes/head.html* file.&nbsp; For example, to include the *vis.js* library in a rendered post page, add the following:

```javascript
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vis/4.15.0/vis.min.js" type="text/javascript"></script>
```

(2) Establish a convenient location for your custom or other locally-served Javascript source files.&nbsp; This could be under an *assets* directory, for example.&nbsp; 
If you create a directory under the *_includes* directory for this, your specifications in *_includes/head.html* can specify URLs relative to *_includes*.

(3) Modify the front matter of the post in question by adding a variable to contain the qualified name of the Javascript code file to be included.&nbsp; For example:

        my_js_code: /assets/js/awesome.js
 
(4) Modify the content of *_layout/post.html* to load the desired Javascript script files.&nbsp; A good way to do this would be to add the following to the end of the layout:

```
        {% for js in page.my_js_code %}
            <script type="text/javascript">{% include {{ js }} %}</script>
        {% endfor %}
```
 
NOTE

When we add the link in *_includes/head.html*, as shown in step #1, it gets loaded into every page in the blog.&nbsp; 
This is certainly less than desirable for pages that do not need this Javascript.&nbsp; 
A good way to solve this problem is to, first, add a variable into the page's front matter, like this:

        load_vis: true

then, "fence in" the lines from Step #1, like this:

```
        {% if page.load_vis %}
            <script src="https://cdnjs.cloudflare.com/ajax/libs/vis/4.15.0/vis.min.js" type="text/javascript"></script>
        {% endif %}
```         
This way, the inclusion of this Javascript link in the final rendering is performed according to the setting of this variable.&nbsp; 
If the variable is absent, (or set to *false*), the link is not included.
