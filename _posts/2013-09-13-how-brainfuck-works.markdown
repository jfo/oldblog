---
layout: post
status: publish
published: true
title: How brainfuck works
author: Jeff
author_login: jeffowler
author_email: jeffowler@gmail.com
excerpt: "<p style=\"text-align: center;\"><img class=\"aligncenter  wp-image-539\"
  alt=\"bf\" src=\"http://www.jeffalanfowler.com/blog/wp-content/uploads/2013/09/bf.jpg\"
  width=\"100%\" /></p>\r\n<p style=\"text-align: center;\"><a href=\"http://en.wikipedia.org/wiki/Brainfuck\"
  target=\"_blank\">brainfuck</a>:\r\n<a href=\"http://mothereff.in/brainfuck-minifier\"
  target=\"_blank\">The ee cummings of esolangs. </a></p>\r\nI got some good advice
  from <a href=\"http://piablumenthal.com/\" target=\"_blank\">Pia</a>, who writes
  and makes such cool, cool  looking stuff, and that advice was to treat a blog not
  like a personal journal, really, but more like a way to provide your future self
  (at least) with documentation on and about the things that you work on, do, make,
  etc. etc. etc. I like that idea, thanks Pia.\r\n\r\nSo here is part one of a two
  part post on brainfuck, an actual name of an actual <a href=\"http://en.wikipedia.org/wiki/Turing_completeness\">Turing
  complete</a> programming language that people use for things. Sort of. Not really
  though.\r\n\r\nI lost my mind last weekend and learned the basics; I wrote a Ruby
  based interpreter and a FizzBuzz, and when I was done I was unable to focus my eyes
  which, according to Gabe, is \"Totally a thing!\".\r\n\r\nAlso, <a href=\"https://soundcloud.com/dawn-of-midi\">Dawn
  of Midi<em></em></a> is really good to listen to on day three of staring at something
  incomprehensible, FYI.\r\n\r\nHere's how it works:\r\n\r\n"
wordpress_id: 461
wordpress_url: http://www.jeffalanfowler.com/blog/?p=461
date: 2013-09-13 12:47:34.000000000 -04:00
categories:
- Programming
tags: []
comments: []
---
<p style="text-align: center;"><img class="aligncenter  wp-image-539" alt="bf" src="http://www.jeffalanfowler.com/blog/wp-content/uploads/2013/09/bf.jpg" width="100%" /></p>
<p style="text-align: center;"><a href="http://en.wikipedia.org/wiki/Brainfuck" target="_blank">brainfuck</a>:
<a href="http://mothereff.in/brainfuck-minifier" target="_blank">The ee cummings of esolangs. </a></p>
I got some good advice from <a href="http://piablumenthal.com/" target="_blank">Pia</a>, who writes and makes such cool, cool  looking stuff, and that advice was to treat a blog not like a personal journal, really, but more like a way to provide your future self (at least) with documentation on and about the things that you work on, do, make, etc. etc. etc. I like that idea, thanks Pia.

So here is part one of a two part post on brainfuck, an actual name of an actual <a href="http://en.wikipedia.org/wiki/Turing_completeness">Turing complete</a> programming language that people use for things. Sort of. Not really though.

I lost my mind last weekend and learned the basics; I wrote a Ruby based interpreter and a FizzBuzz, and when I was done I was unable to focus my eyes which, according to Gabe, is "Totally a thing!".

Also, <a href="https://soundcloud.com/dawn-of-midi">Dawn of Midi<em></em></a> is really good to listen to on day three of staring at something incomprehensible, FYI.

Here's how it works:

<a id="more"></a><a id="more-461"></a>

brainfuck interpreters recognize only 8 characters (<em>sometimes</em> 9, but not really... back to that later):
<blockquote>
<p style="text-align: left;">&lt;   &gt;   +   -   [   ]   .   ,</p>
</blockquote>
&nbsp;

Any and all spaces, extra characters, line breaks, etc, are completely ignored. 100%. The program really looks like a long string with no spaces consisting of just those 8.

How the hell does it work? Well, before moving on, here are some interesting things I learned recently that will make it easier to explain. Also, just as a side note...<i> </i>I <em>loooove</em> little factoids like this, things that I "knew" before, but didn't  really <a href="http://en.wikipedia.org/wiki/Grok">grok</a>. Ok. So:

A "bit" is the <em>smallest possible piece </em>of information. It is simply on or off: 1 or 0, true or false. Bit is short for "binary digit". One bit is one binary digit- and a binary digit, being binary and all that, only has those two possible states.

A "byte" is <em>eight</em> bits. In binary, eight digits provide you with 256 discrete values: 0-255 (0 counts as one of those). Any single byte can have a value anywhere in that range.

Here, I'll count to 10 in binary:
<blockquote>0000 0000
0000 0001
0000 0010
0000 0011
0000 0100
0000 0101
0000 0110
0000 0111
0000 1000
0000 1001</blockquote>
&nbsp;

You might be able to intuit that if 0 looks like the top number, then 255 will look like "1111 1111". Of course, there is no need to have all those leading zeroes, really, except to show that that would be the state of those bits in a byte of memory that was holding those values. We'll just use the decimal numbers for readability, but they can be represented either way and are equivalent. They could also be represented in hex...

This is just like when you go from 0-9 in the ones place and then roll over back to 0 adding 1 to the tens place, except that maximum value in any single spot is "1". I get it now! Base 2! Also this led to an AHA! moment concerning the<a href="http://www.javascripter.net/faq/rgbtohex.htm"> RGB hexcodes</a> that I have been looking at for years in Photoshop- they are simply three concatenated two-digit <a href="http://en.wikipedia.org/wiki/Hexadecimal">hexadecimal numbers! </a>

Traditionally, the brainfuck "workspace" (if I can call it that?) consists of two simple things: An array of 30,000 memory slots, each containing just one byte (8 bits, all initialized to hold 0), and a pointer that points to just one of those slots at any one time (initialized to the very first slot.) It's basically a straight software model of a <a href="http://en.wikipedia.org/wiki/Turing_machine">Universal Turing Machine.</a>

Now we can understand what the first four symbols do.
<blockquote>&lt;    moves the pointer to the left, decreasing-ly.

&gt;    moves the pointer to the right, increasing-ly.</blockquote>
&nbsp;

Usually, the location of the pointer will "roll over" if it goes below 0 or above 30,000... (or above whatever the maximum number available is) effectively making the memory cells act like one long circular tape.
<blockquote>+   increments the value of the byte at the current slot

-    decrements the value of the byte at the current slot</blockquote>
&nbsp;

So far so good. So here's a new brainfuck space, I'll only show 10 spots because I am not going to type 30,000:
<blockquote>[0] 0 0 0 0 0 0 0 0 0 0 ...
^</blockquote>
&nbsp;

Pointer starts at one; everything is zero. Now if we ran this code:
<blockquote>+++&gt;&gt;&gt;+&gt;--</blockquote>
&nbsp;

The memory array would end up looking like this:
<blockquote> 3 0 0 1 [254] 0 0 0 0 0 0 ...</blockquote>
&nbsp;

Notice that the decrementing of the fifth cell wrapped around to 255 instead of going negative. A lot of modern interpreters don't stick to the one byte rule, and can hold any value of any size, negative or not. At its most basic, though, one byte per cell is all you would get. Notice also where the pointer ends up- on the last cell it pointed to.

Two more symbols- the input and output.
<blockquote>,   waits for the user to input a value and places it at the current cell

.   outputs the value at the current cell (prints to screen)</blockquote>
&nbsp;

The values 0-255 are mapped to characters using <a href="http://www.asciichart.com">ASCII</a>- so if I wanted a cell to contain the value "103," I would press "g" (lowercase). Similarly, if the cell had a value of 103 ("0110 0111" in binary, "67" in hexadecimal), and the program read "." it would print "g" to the screen.

So how you might make a brainfuck program output simple text to the screen- you can have it say <i>anything</i> just using +,- and .

Here's a super simple hello world:
<blockquote><pre>++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++.
+++++++++++++++++++++++++++++.
+++++++..+++.
-------------------------------------------------------------------------------.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++.
++++++++++++++++++++++++.+++.------.--------.
-------------------------------------------------------------------.</pre></blockquote>
&nbsp;

<a href="http://replit.com/K9B" target="_blank">Check it out here and run it.</a>

Easy, right? You'll notice two things. It works great! and.. only the first time! Why is that? Well, we're only acting on a single cell changing that single value directly until we get to the appropriate ASCII character code for the letter or characterr we want to print, and the cell is not reset between times you run the program, unless you reload the page. Every time you run the code through the interpreter, it starts out at the number the previous instance left it at. In our case: 33 ... which is the value of the exclamation mark. Each time you run the code, that value goes up by 33, printing out gibberish. Notice also that it goes waaaaaaay above 255. This interpreter can hold way more than a single byte, and is printing out Unicode values instead. [Edit: Gabe tells me it's still ASCII, not Unicode...]

Let's fix it!

Add a "&gt;" right at the top, before anything else.

Now the very first thing the program does is to move the pointer over just once to start from a fresh cell. Easy! Notice that the memory slots are all filling up with 33's as well. やった！

But we have two more symbols, and they are the really good ones:
<blockquote>[       if the value of current cell is zero, skip to the matching bracket without executing the code.

]       if the value of the current cell is NOT zero, go back to the opening bracket and execute the code again.</blockquote>
&nbsp;

OMG! LOORPS!

The simplest loop in brainfuck is this one:
<blockquote> [-]</blockquote>
&nbsp;

This code decreases the value of the current cell until it is zero. If you just ran this code and nothing else, it wouldn't do anything because the cell is initialized at 0, thereby making the program skip the internal parts of the bracket. But if we run this code:
<blockquote> <a href="http://replit.com/K9B/1" target="_blank">+++++ [-]</a></blockquote>
&nbsp;

Well, it still <em>looks </em>like it does nothing, but really it increments the value to 5 and then decrements it to zero.

Walk through it:
<blockquote>Increase value of cell to 5
Value of cell is 5 so run the code.
Decrease to 4
Value is not zero so rerun the code
Decrease to 3
Value is not zero so rerun the code
Decrease to 2...</blockquote>
&nbsp;

You get the idea. The loop will run until the value of the cell is zero and then terminate- leaving the final value of everything at zero, leaving no trace, <a href="http://www.burningman.com/environment/resources/lnt.html" target="_blank">like a conscientious burner on the playa</a>.

So in addition to starting each iteration of the program by moving to a "clean" cell, you could also decrement the current cell back to zero (from wherever it might have ended up) by inserting that simple loop before anything else.

<a href="http://replit.com/K9B/2" target="_blank">Like this!</a>

That's what the 8 symbols do. That's it!!! THAT'S ALL IT IS!! But in theory, you can write anything in brainfuck, any kind of program you can possibly write in anything else could be realized. Of course, <a href="http://forum.osdev.org/viewtopic.php?f=2&amp;t=20967">CAN doesn't mean SHOULD</a><em>, </em>and writing an OS in brainfuck, while an insanely challenging and interesting and <em></em> curiosity problem, I'm sure, has been likened to trying to build a car by bolting parts onto a skateboard.

One more thing about loops.

You can use a helper cell to iterate a loop a specified number of times. Consider this:
<blockquote> <a href="http://replit.com/K9H">+++++ +++++ [&gt; +++++ +++++ &lt; -]</a></blockquote>
&nbsp;

This loads the first cell (our counter) to 10, then when the loop starts it moves over to cell two to increment 10 times, before moving back to cell one to decrement once. Just like before, it runs the code until the cell reaches zero- but the code within the brackets is affecting the second cell. That little line is the same as this one:
<blockquote> <a href="http://replit.com/K9H/1">&gt; ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++&lt;</a></blockquote>
&nbsp;

So that's brainfuck. Sort of. This is really basic, but that's how it works. You can write brainfuck code to run if/then statements and if/else statements and all kinds of things.

Oh and PS: some interpreters use "#" as a debugging breakpoint. Whenever the interpreter encounters it, it halts and waits for a signal to continue.

Next time: <a href="http://www.codinghorror.com/blog/2007/02/fizzbuzz-the-programmers-stairway-to-heaven.html">FizzBuzz</a> in brainfuck!

&nbsp;

&nbsp;
