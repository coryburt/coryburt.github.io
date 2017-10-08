---
layout: "post"
title:  "Web page scripting -- with Python3"
---

Creating a Github Pages site blog is all about more HTML, CSS, and Javascript than I have done in a while.&nbsp; I have, of late, thought of myself as 
a "systems developer" with an emphasis on Python3.&nbsp; I freely confess that my favorite programming language is always the one I've used the most 
in my most recent activities.&nbsp; Several years ago, that was Perl and then PHP.&nbsp; 
If you have a sadistic turn of mind and decide to inflict the dread whiteboard coding test on me, it still comes out as Perl.&nbsp; 
(I am usually effusive in erudite English, _impromptu_, in front of audiences of more than one; 
mysteriously, one-on-one interaction is where things begin to go south for me).&nbsp; 
As they like to say in the Perl community: TIMTOWTODI.&nbsp;

That is why I have been excited to find out about tools like [Skulpt](http://www.skulpt.org/), [PyPy.js](http://pypyjs.org/), [Transcrypt](http://transcrypt.org/),
and [RapydScript](https://bitbucket.org/pyjeon/rapydscript).&nbsp; 
These are among the most thoroughly developed, but there are others out there that do what they do, namely: implement Python2 or Python3 in the browser.&nbsp; 
They are Javascript libraries that integrate the Python language, in one way or another, with the Javascript engine that is already there.&nbsp; 
Of particular interest to me is the (admittedly massive) [Brython](http://brython.info/) library.

I can hear a gaggle of Javascript specialists out there saying, "Huh?"&nbsp; But, there might a few erstwhile Pythonistas replying, "Makes sense to me."

I wanted to demonstrate this remarkable accomplishement by including the Brython console, in the big empty space below.&nbsp; 
However, I can't yet figure out how to make it show up on the Github site, (works fine at home).&nbsp; 
Rather than simply withdraw this post, I'll leave it and work some more on the problem; if I find the solution, I'll make another post.

<iframe src="http://brython.info/console.html" frameborder="no" border="0" marginwidth="0" marginheight="0" width="670" height="450"></iframe>

If it actually showed up above, you could try it out right here and demonstrate to yourself how much of the full Python3 language is actually implemented.&nbsp; 
Quite a large number of Python libraries, (not all, as you might expect), are available for import.&nbsp; 
Best of all, it makes scripting the browser available to the Python programmer.&nbsp; 
Perhaps not the most emminently practical thing to do, but surprisingly capable and responsive.&nbsp; Definitely amazing.&nbsp; 
Just not on Jekyll-generated Github Pages.&nbsp; Yet.

