---
layout: "post"
title: "More Python Pitfalls"
---
### Parameter Default Madness

Most Python programmers figure this one out fairly early in the game, but, if you don't learn the language from an expert &ndash; 
or have the patience to methodically work through a _good_ text &ndash; you end up deep into the weeds before running afoul of this one.&nbsp; 
The basis for this problem is the combination of Python's useful &ndash; and very necessary &ndash; feature wherein functions can be defined 
with default values for their arguments, the fact that these default values can, themselves, be mutable values, and the way these mutable 
values are scoped.&nbsp; Why and how this is a problem is best illustrated with a basic example.&nbsp; Consider this code:

```python
    def list_bars(bar=[]):
        bar.insert(0, "Your Bars: ")
        return(bar)
```
Now, we'll call this with the following test invocations:
```python
    print( list_bars(["The Korova Milk Bar"]) )
    print( list_bars(["Rick's Cafe Americain", "Tree's Lounge"]) )
    print( list_bars(["Bob's Country Bunker"]) )
```
And, the results are, as we would expect:
```python
    ['Your Bars: ', 'The Korova Milk Bar']
    ['Your Bars: ', "Rick's Cafe Americain", "Tree's Lounge"]
    ['Your Bars: ', "Bob's Country Bunker"]
```
So far, so good.&nbsp; *However*, the parameter of _list_bars_ is, by definition, optional because it is given the default value of _[]_ which is a Python list, which is... wait for it... mutable.&nbsp;
So, what happens if we call it repeatedly without specifying a value for the parameter?&nbsp; Like this:
```python
    print( list_bars() )
    print( list_bars() )
    print( list_bars() )
```
Well, it may not be what your intuition comes up with at first blush.&nbsp; Here t'is:
```python
    ['Your Bars: ']
    ['Your Bars: ', 'Your Bars: ']
    ['Your Bars: ', 'Your Bars: ', 'Your Bars: ']
```
What tha...?&nbsp;

Here's the ticket.&nbsp; Because _list_bars_ returns the _bar_ variable, it takes on a life outside the scope of the function.&nbsp; Each time the function is called with a valid list 
parameter, _*that*_ list becomes the list the function manipulates and returns and all is well.&nbsp;
If, however, the _list_bars_ function is called without a parameter, the default list becomes the one being manipulated; and, whatever value _bar_ had before the call is what it will continue to have.&nbsp; 
Since _list_bars_ alters the value of _bar_ by *appending* a string, (and not overwriting anything), subsequent calls to _list_bars_ that don't have parameters will only 
prepend another string to the front of that default _bar_ list.&nbsp; 
Compounding the trickiness of this process, any call to _list_bars_ that has a valid list as a parameter will work exactly as expected, but further calls without parameters just get worse.&nbsp;
Consider the results of this string of calls:
```python
    print( list_bars() )
    print( list_bars() )
    print( list_bars() )
    print( list_bars(["The Green Dragon"]) )
    print( list_bars() )
    print( list_bars() )
    print( list_bars(["The Winchester"]) )
    print( list_bars() )
    print( list_bars() )
```
Surprise!&nbsp; This yields the output:
```python
    ['Your Bars: ']
    ['Your Bars: ', 'Your Bars: ']
    ['Your Bars: ', 'Your Bars: ', 'Your Bars: ']
    ['Your Bars: ', 'The Green Dragon']
    ['Your Bars: ', 'Your Bars: ', 'Your Bars: ', 'Your Bars: ']
    ['Your Bars: ', 'Your Bars: ', 'Your Bars: ', 'Your Bars: ', 'Your Bars: ']
    ['Your Bars: ', 'The Winchester']
    ['Your Bars: ', 'Your Bars: ', 'Your Bars: ', 'Your Bars: ', 'Your Bars: ', 'Your Bars: ']
    ['Your Bars: ', 'Your Bars: ', 'Your Bars: ', 'Your Bars: ', 'Your Bars: ', 'Your Bars: ', 'Your Bars: ']
```
If you're trying to debug a program's bizarre behavior caused by this, the resulting outputs might not be all that helpful in pinning this down.

Just sayin'

### So, What To Do?

As with all landmines, the best advice is *"Just Don't Step On Them!"*&nbsp; If you must have a _list_bars_ function like this one, it is best to add some internal testing, 
or take advantage of "duck typing" and wrap your "append" action in a "try/except" block.&nbsp; 
In any case, do *NOT* make the default parameter a mutable variable that "jumps scope."&nbsp;
Something like this, for example:
```python
    def list_bars(bar=None):
        results = []
        if bar is not None:
            results.append(bar)
        if len(results) > 0:
            results.insert(0, 'Your Bars: ')
        return(results)
```
Now, ply this with the same series of calls:
```python
    print( list_bars() )
    print( list_bars() )
    print( list_bars() )
    print( list_bars(["The Green Dragon"]) )
    print( list_bars() )
    print( list_bars() )
    print( list_bars(["The Winchester", "The Slaughtered Lamb"]) )
    print( list_bars() )
    print( list_bars() )
    print( list_bars('The Bamboo Lounge') )
```
This time, you get the following output:
```python
    []
    []
    []
    ['Your Bars: ', ['The Green Dragon']]
    []
    []
    ['Your Bars: ', ['The Winchester', 'The Slaughtered Lamb']]
    []
    []
    ['Your Bars: ', 'The Bamboo Lounge']
```
Which is a more reasonable and correct output &ndash; and even works with a list or a plain string.
