---
layout: post
status: publish
published: true
title: Rubyks, the solver methods
author: Jeff
author_login: jeffowler
author_email: jeffowler@gmail.com
excerpt: "&nbsp;\r\n<p style=\"text-align: center;\"><img class=\"aligncenter\" alt=\"\"
  src=\"http://communities.ptc.com/servlet/JiveServlet/showImage/2-172419-27077/puzzles_rubiks_cube-13771.jpg\"
  width=\"400\" height=\"268\" /></p>\r\nSo now I have a software model of a rubik's
  cube. But how would I go about writing a program that can manipulate that model
  from any legal position and solve it?\r\n\r\n"
wordpress_id: 779
wordpress_url: http://www.jeffalanfowler.com/blog/?p=779
date: 2013-11-12 16:19:36.000000000 -05:00
categories:
- Programming
tags: []
comments: []
---
&nbsp;
<p style="text-align: center;"><img class="aligncenter" alt="" src="http://communities.ptc.com/servlet/JiveServlet/showImage/2-172419-27077/puzzles_rubiks_cube-13771.jpg" width="400" height="268" /></p>
So now I have a software model of a rubik's cube. But how would I go about writing a program that can manipulate that model from any legal position and solve it?

<!--break-->

This was also a major nerd snipe on myself, much like the fizzbuzz in brainfuck that ate up a full weekend a few weeks ago. At first, I figured that this was out of my paygrade-- so many better solvers have been written. I'm not even that good of a cuber! I learned to solve it in college but only ever learned one method- it works every time but is not the most efficient solution by any means. I would have to learn new algorithms and strategies if I wanted to write a program that would work well. But then...

Really, the point of the exercise was not to write a fast, efficient program- but rather to attempt to model my own logical process when I solve an "analog" cube. For that- this was a perfect test problem, so that's what I did.

As I said in the last post, implementing the basic transformations was pretty easy. Using those methods in series to build helper methods that perform even complex algorithms was as simple as stringing them together on a single Cube object and then returning that object. Like this:
<blockquote>
<pre>  #Re-orients cubies of [0][4], [0][6], and [0][8] without affecting anything else.
  def last_move
    self.rr.d.d.r.f.d.d.fr.ur.f.d.d.fr.rr.d.d.r.u
    self
  end</pre>
</blockquote>
That's the most long winded combination in my repertoire, used to reorient the final cubies to their proper faces.

I planned out the solution by thinking of the steps I use normally:
<ol>
	<li>top cross</li>
	<li>corners next to the top cross</li>
	<li>second level middles</li>
	<li>last level cross</li>
	<li>last level corners</li>
</ol>
So I implemented solving methods for each of these. Basically, each step repeats a set of motions that don't change the effects of the previous step until some condition is satisfied. Here is the top cross method for an example:
<blockquote>
<pre>  #Solves for cross on first layer. Affects all other layers. 
  def cross_solve 
    downcross = []
    i = 1
    until @cube[0][1] == @cube[0][0] &amp;&amp; @cube[0][3] == @cube[0][0]  &amp;&amp; @cube[0][5] == @cube[0][0] &amp;&amp; @cube[0][7] == @cube[0][0]

      until downcross.include?(@cube[0][0]) 
         downcross = []
         self.rr.d.r.l.dr.lr.turn
         downcross = [@cube[5][1],@cube[5][3],@cube[5][5], @cube[5][7]]
         i += 1
         if i &gt; 10
           self.turn until @cube[0][1] != @cube[0][0] 
           self.l.b 
           i = 1
         end
      end

      until @cube[5][3] == cube[0][0]
        i =0
        self.d

        if i &gt; 59 
          self.print
          gets
          end
          i+=1
      end

      until @cube[0][7] != @cube[0][0]
        self.u
      end
     self.f.f
     downcross = []
    end

    until @cube[4][3] == @cube[4][0] &amp;&amp; @cube[1][5] == @cube[1][0]
      until @cube[1][5] == @cube[1][0]        
        self.u
      end
      self.turn if @cube[4][3] != @cube[4][0]
      i += 1

      if i &gt; 10   
        self.cross_swap
        i = 1
      end
    end

    if @cube[2][7] != @cube[2][0]
      self.cross_swap
    end

    self
  end</pre>
</blockquote>
It is a very dumb, brute force solving method. I also included several conditionals that trip if the loop has iterated a certain number of times; these act like a tilt- jogging things around just enough to change whatever was causing the loop to lock up.

And so on down the line, until the cube is solved.

The final method to call all of these layers in sequence looks something like this:
<blockquote>
<pre>  #solve invokes all layer solving methods in sequence, solving from any legal state 
  def simple_solve
    testarray = [] 
    @cube.each {|side| testarray &lt;&lt; side.uniq}
    return self if testarray.flatten.length == 6

    self.cross_solve.corners_solve.second_layer_solve.top_cross.top_corners
    self
  end</pre>
</blockquote>
Note that it always checks to see if the cube is ALREADY solved before mucking it up!

Going through the process of modeling my own behavior was enlightening. The computer is very, very stupid, but if you give it explicit enough instructions that are able to handle any possible cases, it can do almost any logical process.

&nbsp;
