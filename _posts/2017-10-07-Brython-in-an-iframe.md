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
(I am usually effusive in erudite English, _impromptu_, in front of audiences of more than one; 
mysteriously, one-on-one interaction is where things begin to go south for me).&nbsp; 
As they like to say in the Perl community: TIMTOWTODI.&nbsp;

That is why I have been excited to find out about Javascript libraries like [Skulpt](http://www.skulpt.org/), [PyPy.js](http://pypyjs.org/), [Transcrypt](http://transcrypt.org/),
and [RapydScript](https://bitbucket.org/pyjeon/rapydscript).&nbsp; 
These are among the most thoroughly developed libraries of their ilk, but there are others out there that do what they do, namely: implement Python2 or Python3 in the browser.&nbsp; 
They integrate the Python language, in one way or another, with the Javascript engine that is already highly optimized in every modern browser.&nbsp; 
Of particular interest to me is the (admittedly massive) [Brython](http://brython.info/) library.

I can hear a gaggle of Javascript specialists out there asking, "Huh?"&nbsp; But, there might a few erstwhile Pythonistas replying, "Makes sense to me."

Try the Brython console for yourself, below.&nbsp; 
You can experiment with it directly to discover how much of the full Python3 language is actually implemented.&nbsp; 
Quite a large number of Python libraries are available for import -- not all, of course, but support is very good.&nbsp; 
Best of all, it makes scripting the browser available to the Python programmer.&nbsp; 
Perhaps using Javascript to replace Javascript with Python is not the most emminently practical thing to do, but is, by all reports, surprisingly capable and responsive.&nbsp; 
Kudos to [Pierre Quentel](https://brythonista.wordpress.com/) and the many others who have made this a reality.&nbsp;
Definitely cool.

<iframe src="/proj/brython-console/brython_console.html" width="800" height="400"></iframe>