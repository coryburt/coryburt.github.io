---
layout: "post"
title: "More Python Pitfalls"
---
### Parameter Default Madness

Most Python programmers figure this one out fairly early in the game, but, if you don't learn the language from an expert &ndash; 
or have the patience to methodically work through a _good_ text &ndash; you end up deep into the weeds before running afoul of this one.&nbsp; 
The basis for this problem is Python's useful &ndash; and very necessary &ndash; feature wherein functions can be defined 
with default values for their arguments, and what happens when the rules of Python variable scoping are applied to them.&nbsp; 
The mystery takes shape when parameters are given defaults that are _mutable_ values.&nbsp; 
Why and how this is a problem is best illustrated with a basic example.&nbsp; Consider this code:

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
Still not entirely bulletproof, but does give a more reasonable and correct output &ndash; and even works with a list or a plain string.&nbsp;
If "plain string" is not to be permitted, you might simply include further test criteria, like so:
```python
    def list_bars(bar=None):
        results = []
        if bar is not None and isinstance(bar, list):
            results.append(bar)
        if len(results) > 0:
            results.insert(0, 'Your Bars: ')
        return(results)
```
Whereupon you get only an empty list if the parameter is not an instance of a list, (which might be cause to raise an exception... or not... fielders choice).

## Is This A "Ginned-up" Example?

You might look at this and wonder what good this code is in any reasonable use-case.&nbsp; I would remind you that, when considering 
escoteric programming code and exploring its behavior, such practical considerations are snobbishly derided as being "beside the point," (but
I digress...).&nbsp; In truth, you might be thinking of such code as an "accumulator" of things &ndash; in this case, bars.&nbsp;

To that end, a thoroughly modern programmer might start thinking of objects with getters and setters.&nbsp; I forgive you for your eagerness to plunge 
down that rabbit-hole, but, if you're really trying to do a basic job of work and not re-write all the control systems for the Space Shuttle, I suggest
a KISS-able approach.&nbsp; Perhaps this:
```python
    def accumulate_bars(new_bars=[], accumulator=[]):
        if len(accumulator) == 0:
            accumulator.insert(0, 'Your Bars: ')
        if isinstance(new_bars, list) and len(new_bars) > 0:
            for b in new_bars:
                accumulator.append(b)
        elif isinstance(new_bars, str):
            accumulator.append(new_bars)
        return(accumulator)
```
This code ignores anything that isn't a list or string, (rather than raise an exception, which is always an option &ndash; and preferrable if it's important
that the program chokes on data errors).&nbsp; It also has the added benefit/side-effect of flattening the accumulated list.&nbsp; 
If plied with the following:
```python
    print( accumulate_bars(None) )
    print( accumulate_bars() )
    print( accumulate_bars(["The Green Dragon"] ) )
    print( accumulate_bars(["The Winchester", "The Slaughtered Lamb"] ) )
    print( accumulate_bars("Bob's Country Bunker") )
    print( accumulate_bars([]) )
```
The result looks like this:
```python
    ['Your Bars: ']
    ['Your Bars: ']
    ['Your Bars: ', 'The Green Dragon']
    ['Your Bars: ', 'The Green Dragon', 'The Winchester', 'The Slaughtered Lamb']
    ['Your Bars: ', 'The Green Dragon', 'The Winchester', 'The Slaughtered Lamb', "Bob's Country Bunker"]
    ['Your Bars: ', 'The Green Dragon', 'The Winchester', 'The Slaughtered Lamb', "Bob's Country Bunker"]
```
Note: the "accumulator" parameter _must_ have a default value of the empty string in this case, and nothing
should be passed in; this will cause the first call to create the implicit list that will populated by subsequent calls.&nbsp;
So, we're now taking advantage of this scoping pitfall; having a mutable value for a default is useful here.&nbsp;

This code makes it possible to have multiple "accumulators;" you simply define an empty list for one in the calling code and add it as the
second parameter in the call to _accumulate_bars_.&nbsp; Consider this sequence of calls to _accumulate_bars_:
```python
    print( accumulate_bars() )
    print( accumulate_bars(["The Green Dragon", 'Bob\'s Country Bunker'] ) )
    print( accumulate_bars(["The Winchester", "The Slaughtered Lamb"] ) )

    joes_bars = ["Joe's Bars :"]

    print( accumulate_bars(["The Korova Milk Bar"], joes_bars) )
    print( accumulate_bars(["Rick's Cafe Americain", "Tree's Lounge"], joes_bars ))
    print( accumulate_bars('The Bamboo Lounge', joes_bars ))

    print( accumulate_bars() )

    print( "joes bars = ", joes_bars )
```
The resulting output will look like this:
```python
    ['Your Bars: ']
    ['Your Bars: ', 'The Green Dragon', "Bob's Country Bunker"]
    ['Your Bars: ', 'The Green Dragon', "Bob's Country Bunker", 'The Winchester', 'The Slaughtered Lamb']
    ["Joe's Bars: ", 'The Korova Milk Bar']
    ["Joe's Bars: ", 'The Korova Milk Bar', "Rick's Cafe Americain", "Tree's Lounge"]
    ["Joe's Bars: ", 'The Korova Milk Bar', "Rick's Cafe Americain", "Tree's Lounge", 'The Bamboo Lounge']
    ['Your Bars: ', 'The Green Dragon', "Bob's Country Bunker", 'The Winchester', 'The Slaughtered Lamb']
    joes bars =  ["Joe's Bars: ", 'The Korova Milk Bar', "Rick's Cafe Americain", "Tree's Lounge", 'The Bamboo Lounge']
```
Inter-mixing calls to _accumulate_bars_ with and without the second parameter did not cause the explicit accumulator 
and "implicit" one to interfere with one another at all.&nbsp; Now we're on to something interesting &ndash; it just isn't obvious from
the code, (which is the best definition of a language pitfall I can think of right now).

Also, the "for-loop" could be dispensed with if we don't care about flattening the list.&nbsp; 
As such, it could be replaced with a list comprehension &ndash; or even a powerful obfustication using "reduce," or something from "itertools.chain" &ndash; 
but that begs a whole new question about obfustication being a language pitfall... when should you _really_ go there?
