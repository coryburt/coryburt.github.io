---
layout: "post"
title:  "Web page scripting -- with Python3"
---

Creating a Github Pages site blog is all about HTML, CSS, and Javascript -- more than I have done lately, anyway.&nbsp; 
Yes, Github Pages natively supports Jekyll -- and I am certainly in the camp that thinks a file-based framework is a fine idea for the vast majority of websites.&nbsp; 
But, a framework is a framework; there is _always_ a trade-off here and an unexpected price to be paid there when using one.&nbsp;
Yes, the good ones all claim to "stay out of your way," but that is never true until you have hacked and pummelled your way through them and mastered their way of thinking.&nbsp; 
You can't do tricks with your instrument of choice until you've learned to not trip over it.&nbsp; 
That truism is part of the motivation for this entry.

I have, of late, thought of myself as a "systems developer" with an emphasis on Python3.&nbsp; 
I freely confess that my favorite programming language is always the one I've used the most in my most recent activities.&nbsp; 
Several years ago, that would have been Perl, followed by PHP.&nbsp; 
If you have a sadistic turn of mind and decide to inflict the dread whiteboard coding test on me, it still comes out as Perl.&nbsp; 
(I am usually effusive in English, _impromptu_, in front of audiences of more than one; 
mysteriously, one-on-one interaction is where things begin to go south for me).&nbsp; 
Anyway, as they like to say in the Perl community: TIMTOWTODI.&nbsp;

That is why I have been excited to find out about Javascript libraries like [Skulpt](http://www.skulpt.org/), [PyPy.js](http://pypyjs.org/), [Transcrypt](http://transcrypt.org/),
and [RapydScript](https://bitbucket.org/pyjeon/rapydscript), to name just a few.&nbsp; 
These are among the most thoroughly developed libraries of their ilk, but there are others out there that do what they do, namely: implement Python2 or Python3 in the browser.&nbsp; 
They integrate the Python language, in one way or another, with the Javascript engine that is already highly optimized in modern browsers.&nbsp; 
Of particular interest to me (currently) is the massive [Brython](http://brython.info/) library.

Try the Brython console for yourself, below.&nbsp; 
You can experiment with it directly to discover how much of the full Python3 language is actually implemented.&nbsp; 
Quite a large number of Python libraries are available for import -- not all, of course, but support is very good.&nbsp; 
Best of all, it makes scripting the browser available to the Python programmer.&nbsp; 
Of course, this isn't the only game like this being played on the mid-way of the Information Superhighway Strip-mall.&nbsp;
There is [a gaggle](https://github.com/jashkenas/coffeescript/wiki/list-of-languages-that-compile-to-js) of 
"You-name-a-languange-to-Javascript" transpilers, language extensions that completely alter the look-and-feel of Javascript, 
Coffeescript spin-offs, and even tools to help in making the next tool.&nbsp; 
Perhaps using Javascript to replace Javascript with Python is not the most obvious thing to do, but is, by all reports, 
surprisingly capable and responsive -- and comfortingly familiar to some of us.&nbsp;
Kudos to [Pierre Quentel](https://brythonista.wordpress.com/) for Brython, but my admiration extends to the cast of 
thousands that have made this kind of thing into "a thing."&nbsp; Definitely cool.

<iframe src="/proj/brython-console/brython_console.html" width="800" height="400"></iframe>