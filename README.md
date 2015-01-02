Chaining
------
 
Chaining links 2 or more jQuery actions or methods into a single statement by appending the previous action. e.g.
<pre><code>$(‘p: first’)
	.hide()
    .slideDown(‘slow’)
    .fadeOut();
</code></pre>
    
Deferreds
------

The Deferred object, introduced in jQuery 1.5, is a chainable utility object created by calling the jQuery.Deferred() method. It can register multiple callbacks into callback queues, invoke callback queues, and relay the success or failure state of any synchronous or asynchronous function.

jQuery specific optimizations

*  Optimize selectors to descend from an id if possible.
*  Use tag names when selecting classes and don’t use an excessive number of selectors.
*  Define variables instead of selecting the same object repeatedly.
*  Optimize your code replacing repetition with object oriented functions.

.end()
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

Values you can pass to the jQuery method
------

* Selector (string)
* HTML (string)
* Callback (function)
* HTMLElement
* object, array, element array, jQuery Object etc.

jQuery effects queue
------

Queues in jQuery are used for animations. You can use them for any purpose you like. They are an array of functions stored on a per element basis, using jQuery.data(). They are First In, First Out (FIFO). You can add a function to the queue by calling .queue(), and you remove (by calling) the functions using .dequeue().

Differences between .bind(), .live(), .delegate() and .on
------

* Using the <code>.bind()</code> method is very costly as it attaches the same event handler to every item matched in your selector
* <code>.live()</code> has been deprecated and has a lot of problems with it
* The <code>.delegate()</code> method gives a lot of "bang for your buck" when dealing with performance and reacting to dynamically added elements
* That the new <code>.on()</code> method is mostly syntax that can mimic <code>.bind()</code>, <code>.live()</code>, or <code>.delegate()</code> depending on how you call it
* The new direction is to use the new <code>.on</code> method

Difference between $ and $.fn
------

$.fn === $.prototype and is used to extend jQuery with your own methods.

Optimize this selector:
<pre>$(".foo div#bar:eq(0)")</pre> 
 
Differences between .get(), [], and .eq()
------ 
 
Namespacing a bound event handler
------
