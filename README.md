<a name='toc'>Table of Contents</a>
------

1. [Chaining](#chaining)
1. [Deferreds](#deferreds)
1. [jQuery specific optimizations](#optimizations)
1. [.end()](#end)
1. [Values you can pass to the jQuery method](#values)
1. [jQuery effects queue](#effects)
1. [Differences between .bind(), .live(), .delegate() and .on](#bindlive)
1. [Difference between $ and $.fn](#fn)
1. [Differences between .get() and .eq()](#geteq)
1. [Namespacing a bound event handler](#namespacing)

<a name='chaining'>Chaining<a/>
------
 
Chaining links 2 or more jQuery actions or methods into a single statement by appending the previous action. e.g.
<pre><code>$(‘p: first’)
	.hide()
    .slideDown(‘slow’)
    .fadeOut();
</code></pre>
    
<a name='deferreds'>Deferreds<a/>
------

The Deferred object, introduced in jQuery 1.5, is a chainable utility object created by calling the jQuery.Deferred() method. It can register multiple callbacks into callback queues, invoke callback queues, and relay the success or failure state of any synchronous or asynchronous function.

<a name='optimizations'>jQuery specific optimizations<a/>
------

*  Optimize selectors to descend from an id if possible.
*  Use tag names when selecting classes and don’t use an excessive number of selectors.
*  Define variables instead of selecting the same object repeatedly.
*  Optimize your code replacing repetition with object oriented functions.

<a name='end'>.end()<a/>
------

When you have one jQuery chain going and modify it with, say,<code>.find()</code>, <em>you’re actually pushing the new chained set of elements onto a stack</em>. <code>.end()</code> pops the current jQuery chain off the stack, which lets you do stuff like this:
<pre><code>$("#container")
    .show()
    .find(".error")
        .hide()
        .end()
    .find(".zoo")
        .css("background-color", "white")
        .find(".monkeys")
            .empty()
            .end()
        .find(".title")
            .text("The zoo is empty")
            .end()
        .find("input")
            .val("")
            .end()
        .animate({height: 250});
</code></pre>
It’s easy to read, because the indentation is significant and matches up with DOM nesting levels. It gets rid of unnecessary DOM lookups. But most importantly for me, it feels natural to indent in and out as I write the code, using small additional selectors to step deeper into the DOM and .end() to find my way back out.

<a name='values'>Values you can pass to the jQuery method<a/>
------

* Selector (string)
* HTML (string)
* Callback (function)
* HTMLElement
* object, array, element array, jQuery Object etc.

<a name='effects'>jQuery effects queue<a/>
------

Queues in jQuery are used for animations. You can use them for any purpose you like. They are an array of functions stored on a per element basis, using jQuery.data(). They are First In, First Out (FIFO). You can add a function to the queue by calling .queue(), and you remove (by calling) the functions using .dequeue().

<a name='bindlive'>Differences between .bind(), .live(), .delegate() and .on<a/>
------

* Using the <code>.bind()</code> method is very costly as it attaches the same event handler to every item matched in your selector
* <code>.live()</code> has been deprecated and has a lot of problems with it
* The <code>.delegate()</code> method gives a lot of "bang for your buck" when dealing with performance and reacting to dynamically added elements
* That the new <code>.on()</code> method is mostly syntax that can mimic <code>.bind()</code>, <code>.live()</code>, or <code>.delegate()</code> depending on how you call it
* The new direction is to use the new <code>.on</code> method

<a name='fn'>Difference between $ and $.fn<a/>
------

$.fn === $.prototype and is used to extend jQuery with your own methods.

<a name='geteq'>Differences between .get(), [], and .eq()<a/>
------ 
 
<a name='namespacing'>Namespacing a bound event handler</a>
------
