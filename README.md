Chaining
------
 
<p> Chaining links 2 or more jQuery actions or methods into a single statement by appending the previous action. e.g.</p>
<pre><code>$(‘p: first’)
	.hide()
    .slideDown(‘slow’)
    .fadeOut();
</code></pre>
    
<hr />

<h4> Deferreds</h4>
The Deferred object, introduced in jQuery 1.5, is a chainable utility object created by calling the jQuery.Deferred() method. It can register multiple callbacks into callback queues, invoke callback queues, and relay the success or failure state of any synchronous or asynchronous function.
<hr />
<h4> jQuery specific optimizations</h4>
*  Optimize selectors to descend from an id if possible.
*  Use tag names when selecting classes and don’t use an excessive number of selectors.
*  Define variables instead of selecting the same object repeatedly.
*  Optimize your code replacing repetition with object oriented functions.

<hr />

<h4> .end()</h4>
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

<hr />
<h4> Namespacing a bound event handler</h4>

<hr />

<h4> Values you can pass to the jQuery method.</h4>
<ul>
	<li>Selector (string)</li>
    <li>HTML (string)</li>
    <li>Callback (function)</li>
    <li>HTMLElement</li>
    <li>object, array, element array, jQuery Object etc.</li>
</ul>
<hr />

<h4>jQuery effects queue</h4>
Queues in jQuery are used for animations. You can use them for any purpose you like. They are an array of functions stored on a per element basis, using jQuery.data(). They are First In, First Out (FIFO). You can add a function to the queue by calling .queue(), and you remove (by calling) the functions using .dequeue().
<hr />
<h4>Differences between .get(), [], and .eq()</h4>
<hr />
<h4>Differences between .bind(), .live(), .delegate() and .on</h4>
<ul>
	<li>Using the <code>.bind()</code> method is very costly as it attaches the same event handler to every item matched in your selector</li>
	<li><code>.live()</code> has been deprecated and has a lot of problems with it</li>
	<li>The <code>.delegate()</code> method gives a lot of "bang for your buck" when dealing with performance and reacting to dynamically added elements</li>
	<li>That the new <code>.on()</code> method is mostly syntax that can mimic <code>.bind()</code>, <code>.live()</code>, or <code>.delegate()</code> depending on how you call it</li>
	<li>The new direction is to use the new <code>.on</code> method</li>
</ul>
<hr />
<h4>Difference between $ and $.fn</h4>
<p>$.fn === $.prototype and is used to extend jQuery with your own methods.</p>
<hr />

<h4>Optimize this selector:</h4>
<pre>$(".foo div#bar:eq(0)")</pre> 
 
<h2>CODE</h2>
<pre>modulo(12, 5) // 2</pre>
<h4> Implement a modulo function that satisfies the above</h4>
<pre>"i'm a lasagna hog".split("").reverse().join("");</pre>
<h4>Question: What value is returned from the above statement?</h4>
Answer: "goh angasal a m'i"
<pre>( window.foo || ( window.foo = "bar" ) );</pre>
window.foo is undefined initially so it becomes “bar”
<h4>Question: What is the value of window.foo?</h4>
Answer: "bar" (only if window.foo was falsey otherwise it will retain its value)
<pre>var foo = "Hello"; (function() { var bar = " World"; alert(foo + bar); })(); alert(foo + bar);</pre>
Question: What is the outcome of the two alerts above?

Answer: "Hello World" &amp; ReferenceError: bar is not defined
<pre>var foo = [];
foo.push(1);
foo.push(2);</pre>
<h4>Question: What is the value of foo.length?</h4>
Answer: 2

&nbsp;</li>

&nbsp;
