---
layout:             "post"
title:              "External Javascript in Jekyll-based Github Pages"
add_brython:        "/assets/js/brython.js"
add_brython_stdlib: "/assets/js/brython_stdlib.js"
---

This post is a test of using external Javascript code in Jekyll-based Github pages.&nbsp;  As such, credit is due before I even begin.&nbsp; 
Specifically, this material has been derived from similar posts by [Emma Tosch](http://blog.emmatosch.com/2016/03/09/using-custom-javascript-in-jekyll-blogs.html), [Mike Chirico](https://mchirico.github.io/javascript/2016/12/22/JavascriptNetwork.html), and (probably) others.&nbsp;
I thank them for these insights, and added what it took for me to implement their suggestions.

To wit, the procedure that worked for me to use external Javascript sources in this context is, as follows:

(1) Add source link specifications to an *_includes/head.html* file.&nbsp; For example, to include the *vis.js* library in a rendered post page, add the following:

```javascript
    <script src="https://cdnjs.cloudflare.com/ajax/libs/vis/4.15.0/vis.min.js" type="text/javascript"></script>
```

(2) Make certain this file becomes part of the Jekyll rendering chain.&nbsp; For example, you may have a *_layout/post.html* template for your blog posts which uses 
the default layout.&nbsp; Your default layout might be, as mine is, in the *_layout/default.html* template.&nbsp; So, I simply added an,

    {% raw %}
            {% include head.html %}
    {% endraw %}

directive in the the HEAD section of *_layouts/default.html*.

(3) Establish a convenient location for your custom or other locally-served Javascript source files.&nbsp; This could be under an *assets* directory, as mine is.

(4) Modify the front matter of the post in question by adding a variable to contain the qualified name of the Javascript code file to be included.&nbsp; For example:

        my_js_code: /assets/js/awesome.js
 
(5) Modify the content of *_layout/post.html* to load the desired Javascript script files.&nbsp; A good way to do this would be to add the following to the end of the layout:

    {% raw %}
        {% for js in page.my_js_code %}
            <script type="text/javascript">{% include {{ js }} %}</script>
        {% endfor %}
    {% endraw %}

NOTE

When we add the link in *_includes/head.html*, as shown in step #1, it gets loaded into every page in the blog.&nbsp; 
This is certainly less than desirable for pages that do not need this Javascript.&nbsp; 
A good way to solve this problem is to, first, add a variable into the page's front matter, like this:

        load_vis: true

then, "fence in" the lines from Step #1, like this:

    {% raw %}
        {% if page.load_vis %}
            <script src="https://cdnjs.cloudflare.com/ajax/libs/vis/4.15.0/vis.min.js" type="text/javascript"></script>
        {% endif %}
    {% endraw %}

This way, the inclusion of this Javascript link in the final rendering is performed according to the setting of this variable.&nbsp; 
If the variable is absent, (or set to *false*), the link is not included.
