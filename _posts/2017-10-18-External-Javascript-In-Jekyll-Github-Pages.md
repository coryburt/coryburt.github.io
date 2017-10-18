---
layout: "post"
title:  "External Javascript in Jekyll-based Github Pages"
brython: true
brython_stdlib: true
---

The procedure for using any external Javascript sources:

1) Add source link specifications to your *_includes/head.html* file.&nbsp; For example, to include the *vis.js* library in a rendered post page, add the following:

```javascript
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vis/4.15.0/vis.min.js" type="text/javascript"></script>
```

2) Establish a convenient location for your custom or other locally-served Javascript source files.&nbsp; This could be under an *assets* directory, for example.&nbsp; 
If you create a directory under the *_includes* directory for this, your specifications in *_includes/head.html* can specify URLs relative to *_includes*.

3) Modify the front matter of the post in question by adding a variable to contain the qualified name of the Javascript code file to be included.&nbsp; For example:

        my_js_code: /assets/js/awesome.js
 
4) Modify the content of _layout/post.html to load the desired Javascript script files.&nbsp; A good way to do this would be to add the following to the of the layout:

        {% for js in page.my_js_code %}
            <script type="text/javascript">{% include {{ js }} %}</script>
        {% endfor %}
 
NOTE

When we add the link in *_includes/head.html*, as shown in step #1, it gets loaded into every page in the blog.&nbsp; 
This is certainly less than desirable for pages that do not need this Javascript to be loaded.&nbsp; 
To get around this, we first add a variable into the page's front matter, like this:

        load_vis: true

then, "fence in" the lines from Step #1 as below:

        {% if page.load_vis %}
            <script src="https://cdnjs.cloudflare.com/ajax/libs/vis/4.15.0/vis.min.js" type="text/javascript"></script>
        {% endif %}
         
This way, a page can be told to load this Javascript by setting this variable.&nbsp; Otherwise, it is ignored.
