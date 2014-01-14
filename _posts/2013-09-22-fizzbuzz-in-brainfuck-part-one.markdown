---
layout: post
status: publish
published: true
title: fizzbuzz in brainfuck, part one
author: Jeff
author_login: jeffowler
author_email: jeffowler@gmail.com
excerpt: "<blockquote><pre>&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;+&gt;+&gt;+++&gt;&gt;&gt;+++++&gt;&gt;&gt;+&gt;++++++++++&gt;++++++++++&gt;++++++++++&gt;++++++++++++++++++++++++++++++++++++++++++++++++&gt;++++++++++++++++++++++++++++++++++++++++++++++++&gt;++++++++++++++++++++++++++++++++++++++++++++++++&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;+++++++[&lt;&lt;&lt;&lt;&lt;++++++++++&gt;&gt;&gt;&gt;&gt;-]+++++++++++[&lt;&lt;&lt;&lt;++++++++++&gt;&gt;&gt;&gt;-]&lt;&lt;&lt;&lt;-----&gt;&gt;&gt;&gt;+++++++[&lt;&lt;&lt;++++++++++&gt;&gt;&gt;-]&lt;&lt;&lt;----&gt;&gt;&gt;++++++++++++[&lt;&lt;++++++++++&gt;&gt;-]&lt;&lt;---&gt;&gt;++++++++++++[&lt;++++++++++&gt;-]&lt;++&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;[&gt;&gt;&gt;&lt;&lt;[&gt;&gt;&lt;[&gt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&gt;[-]+&gt;[-]&lt;&lt;[&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&gt;[-]&gt;[-]&lt;&lt;[&gt;+&gt;+&lt;&lt;-]&gt;[&lt;+&gt;-]&gt;[&gt;&gt;&gt;&gt;.&gt;.&gt;.&gt;.&lt;&lt;&lt;&lt;&lt;&lt;&lt;[-]]&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&gt;-&lt;[&gt;&gt;+&lt;&lt;-]]&gt;&gt;[&lt;&lt;+&gt;&gt;-]&lt;[&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;.&gt;&gt;&gt;..&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&gt;[-]&gt;[-]&lt;&lt;[&gt;+&gt;+&lt;&lt;-]&gt;[&lt;+&gt;-]+&gt;[&lt;-&gt;[-]]&lt;[&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;.&gt;..&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;[-]&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;-]&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;+++&lt;++++++++++[-]+&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;-]&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&gt;[-]+&gt;[-]&lt;&lt;[&gt;-&lt;[&gt;&gt;+&lt;&lt;-]]&gt;&gt;[&lt;&lt;+&gt;&gt;-]&lt;[&lt;+++++&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;[&lt;[&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;.&gt;..&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;-]+&gt;-]+&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;-]&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;+&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;-&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;-&gt;&gt;&gt;&gt;&gt;&gt;&lt;-]++++++++++&gt;&gt;&gt;&gt;----------&lt;+&lt;&lt;&lt;&lt;-]++++++++++&gt;&gt;&gt;&gt;----------&lt;+&lt;&lt;&lt;&lt;-]&gt;&gt;&gt;.&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;.&gt;..&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;</pre></blockquote>\r\n<span>(</span><a
  href=\"http://replit.com/Kr0/1\" target=\"_blank\">Run that junk.</a><span>)</span>\r\n\r\nA
  couple of weeks ago I got it into my pointy little egg-head that I wanted to write
  a <a href=\"http://www.codinghorror.com/blog/2007/02/fizzbuzz-the-programmers-stairway-to-heaven.html\"
  target=\"_blank\">fizzbuzz</a> in <a href=\"http://www.jeffalanfowler.com/blog/how-brainfuck-works/\"
  target=\"_blank\">brainfuck</a>. As with a lot of the stupid ideas that occur to
  me, I initially dismissed it as a waste of time, as-well-I-had-ought-to-have-done.\r\n\r\n\"Nahhhhhhh,\"
  past me said to himself, chuckling, \"that would be totally, needlessly hard right
  now, and it would take a lot of time, and anyway I don't know how I would even START!
  Unless, maybe, well... I wonder if I could write an if/else... and then if I could
  do that...maybe with a multiples counter cell...and....\"\r\n\r\nAnd so <a href=\"http://esolangs.org/wiki/brainfuck_algorithms\"
  target=\"_blank\">after a quick googling</a>, I was off. I basically <a href=\"http://xkcd.com/356/\">nerd-sniped</a>
  myself.\r\n<p style=\"text-align: center;\">***</p>\r\n<p style=\"text-align: center;\">"
wordpress_id: 595
wordpress_url: http://www.jeffalanfowler.com/blog/?p=595
date: 2013-09-22 04:27:52.000000000 -04:00
categories:
- Programming
tags: []
comments: []
---
<blockquote><pre>&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;+&gt;+&gt;+++&gt;&gt;&gt;+++++&gt;&gt;&gt;+&gt;++++++++++&gt;++++++++++&gt;++++++++++&gt;++++++++++++++++++++++++++++++++++++++++++++++++&gt;++++++++++++++++++++++++++++++++++++++++++++++++&gt;++++++++++++++++++++++++++++++++++++++++++++++++&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;+++++++[&lt;&lt;&lt;&lt;&lt;++++++++++&gt;&gt;&gt;&gt;&gt;-]+++++++++++[&lt;&lt;&lt;&lt;++++++++++&gt;&gt;&gt;&gt;-]&lt;&lt;&lt;&lt;-----&gt;&gt;&gt;&gt;+++++++[&lt;&lt;&lt;++++++++++&gt;&gt;&gt;-]&lt;&lt;&lt;----&gt;&gt;&gt;++++++++++++[&lt;&lt;++++++++++&gt;&gt;-]&lt;&lt;---&gt;&gt;++++++++++++[&lt;++++++++++&gt;-]&lt;++&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;[&gt;&gt;&gt;&lt;&lt;[&gt;&gt;&lt;[&gt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&gt;[-]+&gt;[-]&lt;&lt;[&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&gt;[-]&gt;[-]&lt;&lt;[&gt;+&gt;+&lt;&lt;-]&gt;[&lt;+&gt;-]&gt;[&gt;&gt;&gt;&gt;.&gt;.&gt;.&gt;.&lt;&lt;&lt;&lt;&lt;&lt;&lt;[-]]&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&gt;-&lt;[&gt;&gt;+&lt;&lt;-]]&gt;&gt;[&lt;&lt;+&gt;&gt;-]&lt;[&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;.&gt;&gt;&gt;..&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&gt;[-]&gt;[-]&lt;&lt;[&gt;+&gt;+&lt;&lt;-]&gt;[&lt;+&gt;-]+&gt;[&lt;-&gt;[-]]&lt;[&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;.&gt;..&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;[-]&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;-]&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;+++&lt;++++++++++[-]+&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;-]&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&gt;[-]+&gt;[-]&lt;&lt;[&gt;-&lt;[&gt;&gt;+&lt;&lt;-]]&gt;&gt;[&lt;&lt;+&gt;&gt;-]&lt;[&lt;+++++&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;[&lt;[&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;.&gt;..&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;-]+&gt;-]+&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;-]&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;+&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;-&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&lt;&lt;&lt;&lt;&lt;&lt;-&gt;&gt;&gt;&gt;&gt;&gt;&lt;-]++++++++++&gt;&gt;&gt;&gt;----------&lt;+&lt;&lt;&lt;&lt;-]++++++++++&gt;&gt;&gt;&gt;----------&lt;+&lt;&lt;&lt;&lt;-]&gt;&gt;&gt;.&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;&gt;.&gt;.&gt;..&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;&lt;</pre></blockquote>
<span>(</span><a href="http://replit.com/Kr0/1" target="_blank">Run that junk.</a><span>)</span>

A couple of weeks ago I got it into my pointy little egg-head that I wanted to write a <a href="http://www.codinghorror.com/blog/2007/02/fizzbuzz-the-programmers-stairway-to-heaven.html" target="_blank">fizzbuzz</a> in <a href="http://www.jeffalanfowler.com/blog/how-brainfuck-works/" target="_blank">brainfuck</a>. As with a lot of the stupid ideas that occur to me, I initially dismissed it as a waste of time, as-well-I-had-ought-to-have-done.

"Nahhhhhhh," past me said to himself, chuckling, "that would be totally, needlessly hard right now, and it would take a lot of time, and anyway I don't know how I would even START! Unless, maybe, well... I wonder if I could write an if/else... and then if I could do that...maybe with a multiples counter cell...and...."

And so <a href="http://esolangs.org/wiki/brainfuck_algorithms" target="_blank">after a quick googling</a>, I was off. I basically <a href="http://xkcd.com/356/">nerd-sniped</a> myself.
<p style="text-align: center;">***</p>
<p style="text-align: center;"><a id="more"></a><a id="more-595"></a></p>
<p style="text-align: left;">I decided the easiest way to go about it was to write fizzbuzz in Ruby, first, and then translate it into brainfuck. Aww Ruby, <a href="http://replit.com/Kr2/1" target="_blank">you so pretty with your little modulos and all that ish.</a> But of course I couldn't use anything more complicated than an if/else statement, and I had to do everything incrementally by 1, as well... and I could only stop loops by allowing their index counter to reach zero, not when it got to a certain high number like 100... hmmmmmm.</p>
<p style="text-align: left;">It looks a little unwieldy, but I used numbers spelled out as variable names to stand for the address of the memory cell that I would eventually use in brainfuck. The variables could only be set to numbers, and until loops can only be set to terminate at zero. I started by writing a program that simply counts to 100 without any of the divisor logic.</p>
<p style="text-align: left;">First I needed to mark how high I was going to count. We're going to 100, so I need a 1 in the hundreds loop counter, a 10 in the tens loop counter, and a 10 in the ones loop counter to start with:</p>

<blockquote>seven = 1
eight = 10
nine = 10</blockquote>
Those are the indices; they are going to be going down. Now I need the memory slots holding the actual numerals that are going to be printed... including one slot that holds a new line character I can access so not everything comes out all smashed together, because I can't use <code>puts</code>:
<blockquote>ten = "/n"
eleven = 0
twelve = 0
thirteen = 0</blockquote>
Now I'll just create some nested loops to do the counting (up in the printed slots' case and down in the index slots' case):
<blockquote>
<pre>until seven == 0
    until eight == 0
        until nine == 0
            print ten       #prints the newline
            print eleven    #prints the hundreds place
            print twelve    #prints the tens place
            print thirteen  #prints the ones place

            nine -= 1       #decrements the ones index slot
            thirteen += 1   #increments the ones print slot
        end

        nine = 10           #resets the ones place index slot
        eight -=1           #decrements the tens place index slot

        twelve += 1         #increments the tens place print slot
        thirteen = 0        #resets the ones place print slot
    end

  eight = 10                  #resets the tens place index slot
  seven -= 1                  #decrements the hundreds place index slot

  eleven += 1                 #increments the hundreds place print slot
  twelve = 0                  #resets the tens place print slot
end</pre>
</blockquote>
<a href="http://replit.com/Kr7" target="_blank">Okay- still Ruby... ugly, non-Rubyish Ruby, but now it is nothing I can't do in brainfuck. </a>

But we haven't done the hard part yet- implementing the logic that will filter out the multiples of 3 and 5 and replace them with "Fizz" and "Buzz." In Ruby or any other higher level language, this program practically writes itself with a <a href="http://en.wikipedia.org/wiki/Modulo_operation" target="_blank">modulo operation</a>, which returns zero if a number is evenly divisible by another number and leaves no remainder. But brainfuck, of course, doesn't have this operation, and remember- it's conditional loops can only be triggered by a "0" in the memory slot that is being evaluated, anyway.

This one took a little bit of thought, but a solution was forthcoming. I add two more index cells:
<blockquote>
<pre>five = 3
six = 5</pre>
</blockquote>
and decrement both of those each time I print a number out- when the "3" index slot reaches zero, I know I have found a multiple of 3 and can use that spot to trigger the code to print "Fizz" (and to reset the index back to 3- or rather 2 actually, since that accounts for the<a href="http://en.wikipedia.org/wiki/Off-by-one_error" target="_blank"> ol' off by one</a>) instead of the code to print the number. Ditto for "Buzz."

<a href="http://replit.com/Kr9/1" target="_blank">Here is what all this looks like... </a>now, before printing the number, the program checks to see if it is a multiple of three or five...only when it is not  divisible by either does it print the number itself.

This totally works! But there are some issues- I can't use elsifs in brainfuck- the algorithms I've researched aren't that sophisticated, and I haven't implemented "FizzBuzz" for the numbers that are multiples of both- the logic catches them on "Fizz" and skips over the other bits. Also there is some needless repetition with the newlines, though I'm actually going to need some of that later on so I'll leave it for now.

Ok so I can't use elsifs to evaluate mutliple possible states... but I CAN do that evaluation in series. I need it to think the following, which I have decided to draw a flow chart for because it is late and I want to play with photoshop for a minute...

<a href="http://www.jeffalanfowler.com/blog/wp-content/uploads/2013/09/bffb.bmp"><img class="wp-image-640 alignnone" alt="bffb" src="http://www.jeffalanfowler.com/blog/wp-content/uploads/2013/09/bffb.bmp" width="480" height="480" /></a>
God, that's butt-ugly. I almost didn't put it up, it's so ugly. Whatever, you get the idea. It's two nested if/else statements. I can deal with those<a href="http://replit.com/Kr9/2" target="_blank">! Now it looks like this.</a>

Aside from the repetition we are ignoring- there are three problems left. Still no "FizzBuzz," and when it should make "FizzBuzz," it throws off the 5's counter into negative numbers so it never prints Buzz after 15. And it's not evaluating 100. The first and second problem can be fixed with just one more "if" statement, nuzzled way down in the bowels of our<a href="http://en.wikipedia.org/wiki/Spaghetti_code" target="_blank"> increasingly italian </a>program. We know we'll only have to write "FizzBuzz" if we've already written "Fizz," so anytime we print "Fizz," we just throw in an extra check against whether or not we need to write "Buzz." Now, if we write "FizzBuzz", we will also be resetting the 5's counter.

Oh and as for the last problem, I just hardcoded printing "Buzz" out at the end instead of "100", bypassing all the logic, because I'm a filthy, cheating, dirty fraud. YOLO####33<a href="http://knowyourmeme.com/memes/the-1-phenomenon" target="_blank">3</a>. Also because it will always end up on a multiple of 100, so at least the "Buzz" part will be right. Screw you, 300, 600, and 900!!

Click here to run all this crap ----&gt;   <a href="http://replit.com/Kr9/4" target="_blank">TAH-DAH! </a>
<blockquote>
<pre>five = 3
six = 5

seven = 1
eight = 10
nine = 10

ten = "\n"
eleven = 0
twelve = 0
thirteen = 0

 until seven == 0
    until eight == 0
        until nine == 0

            if five == 0

                print ten      #don't forget the newline!
                print "Fizz"

                if six == 0
                    print "Buzz"
                    six = 5
                end

                five = 2
                six -= 1
                nine -= 1       #decrements the ones index slot
                thirteen += 1   #increments the ones print slot

            else

                if six == 0

                    print ten
                    print "Buzz"
                    six = 4
                    five -= 1
                    nine -= 1       #decrements the ones index slot
                    thirteen += 1   #increments the ones print slot

                else

                    print ten       #prints the newline
                    print eleven    #prints the hundreds place
                    print twelve    #prints the tens place
                    print thirteen  #prints the ones place

                    nine -= 1       #decrements the ones index slot
                    thirteen += 1   #increments the ones print slot

                    five -= 1       #decrements the multiple of 3 tracker
                    six -= 1        #decrements the multiple of 5 tracker
                end
            end    
        end

        nine = 10           #resets the ones place index slot
        eight -=1           #decrements the tens place index slot

        twelve += 1         #increments the tens place print slot
        thirteen = 0        #resets the ones place print slot
    end

eight = 10                  #resets the tens place index slot
seven -= 1                  #decrements the hundreds place index slot

eleven += 1                 #increments the hundreds place print slot
twelve = 0                  #resets the tens place print slot
end

#since the above loop is set to terminate at the top after it reaches 100, that
#final number won't get printed. I'll print it below:

print ten
print "Buzz" #dirty cheater.</pre>
</blockquote>
So I've written the whole program in a way that brainfuck can accommodate. The next step is to translate it. Bleep, bloop, bleep! I'm going to write that in a separate post, because this is getting pretty long. Also if you want to increase the maximum number that you're evaluating, try changing the initial index of the hundreds place in the above code! It will go for as long as you want it to, because it will just continue to print higher numbers because it is Ruby! brainfuck wouldn't be able to do that past 999, because we would need to implement a new loop to print the thousands place, because it is printing strings of digits instead of numbers. We'll get to that next time.

<a href="https://www.google.com/search?q=cats&amp;source=lnms&amp;tbm=isch&amp;sa=X&amp;ei=1Kk-UsXeBYq88wSZi4CABg&amp;ved=0CAkQ_AUoAQ&amp;biw=1916&amp;bih=919&amp;dpr=1#imgdii=_" target="_blank">If you got this far, you deserve this.</a> Come back soon!
