---
layout: "post"
title: "Practical Applications of Python Landmines"
---
## The Practical Application of Python Landmines

Before you get your hair in the air, this isn't about snakes with explosive devices strapped to their slithery hides.&nbsp; It's about the Python programming language.&nbsp; (And it isn't meant to push buttons at the NSA whose robots have already flagged the words "explosives" and "landmines" before you even got this far into the article; no harm intended here, and my apologies, but it cannot be helped).

So, what sadist would put "landmines" and "practical application" in the same sentence?

After all, Python.org says,

> Python's simple, easy to learn syntax emphasizes readability and therefore reduces the cost of program maintenance.

It also says,

> Fortunately an experienced programmer in any programming language (whatever it may be) can pick up Python very quickly. It's also easy for beginners to use and learn, so jump in!

Jump in, indeed.&nbsp; How charmingly enticing.&nbsp; Could anything so obviously wonderful provoke a phrase like "Python Landmines?"&nbsp; Must be the work of a troll &ndash; some professional nay-sayer with a personal ax to grind.

In the course of trying (futilely) to get a job as a Python programmer, I stumbled upon, (or, rather, was shoved into), the craters formed by actual Python Landmines in the course of an interview coding test, (otherwise known as **"whiteboard waterboarding"**).&nbsp; I was, I'll freely admit, surprised to discover that, not only do Python Landmines exist, but their practical application is to demolish posers in a job interview.&nbsp; (Consider me weeded from the garden).

I thought it only fair to put some of these volatile gems in a blog post so that other posers like myself can avoid the risk to life and limb they represent.&nbsp; Speaking of shattered limbs, here's one that really sticks out.&nbsp; Consider the innocent looking assignment statement, (this is all Python 3, by-the-by):

```python
    x = [[]*3]*2
    print(x)
```
Put this in your favorite REPL, (or IDLE, if you must), and observe what the _print_ statement yields:

```python
    [[], []]
```
I you're really new to Python, you have to be gobsmacked by this.&nbsp;  If you have programmed in another language, you might recognize what's happening here.&nbsp; The asterisk operator in Python has three secret identities; in this case, it acts as a "replicator" that causes the assignment of more than one of whatever is on the right-side of the equation.&nbsp; In the case above, the "thing" on the right side that gets replicated is **the content** of a list.&nbsp; You still get only one list, but it's contents are magically replicated -- in this case, twice.&nbsp; Go figure.&nbsp; If you still think Python's syntax is simple and easy to learn, I suggest you have your intuition patented before Microsoft finds it.

If you're really paying attention, I can hear you object that there is also a _\*3_ in there somewhere.&nbsp; Doesn't that also act as a replicator?&nbsp; We're not seeing _three_ of anything.&nbsp; The answer is "yes, it is but calm down and don't get ahead of me."&nbsp; Consider this modification to the above code:

```python
    y = {'Bob':'Carol'}
    x = [[y]*3]*2
    print(x)
```
If you guessed the output of this would be:
```python
    [[{'Bob': 'Carol'}, {'Bob': 'Carol'}, {'Bob': 'Carol'}], 
	[{'Bob': 'Carol'}, {'Bob': 'Carol'}, {'Bob': 'Carol'}]]
```
Then you are a natural, on your way to Pythonista-hood.&nbsp; Your _\*3_ has made it's presence known!&nbsp; Hold on, however, there's more.&nbsp; What if we add Ted and Alice to the dict that is _y_?

```python
    y['Ted'] = 'Alice'
    print(x)
```
Note that we haven't added anything else in the REPL &ndash; just the new assignment to the dict in _y_.&nbsp;
Any guesses as to what the output of this _print_ statement will be?&nbsp; How about:
```python
    [[{'Bob': 'Carol', 'Ted': 'Alice'}, 
      {'Bob': 'Carol', 'Ted': 'Alice'}, 
      {'Bob': 'Carol', 'Ted': 'Alice'}], 
     [{'Bob': 'Carol', 'Ted': 'Alice'},
      {'Bob': 'Carol', 'Ted': 'Alice'}, 
      {'Bob': 'Carol', 'Ted': 'Alice'}]]
```
Now are you gobsmacked?&nbsp; Try to not step on the detonator of that landmine.&nbsp;
The reason all this stuff showed up is that, when you "replicated" the _y_ three times in the inner list, 
you didn't create *copies* or *clones* of the original dictionary, you simply got copies of **a reference to _y_** each time &ndash; 
three times in the inner list, which was then, itself, replicated twice in the outer list.&nbsp; 
Change _y_ after the assigment to _x_, and _x_ will dutifully reflect that change in each of its neatly nested references.&nbsp;

Totally obvious, right?


