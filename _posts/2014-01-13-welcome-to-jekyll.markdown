---
layout: post
title:  "First!"
date:   2014-01-13 23:02:36
---

Ok. So. Here we go with this. Here is a test of some stuff. And now I'll drop in some ruby code 

```ruby
    @rows[0..2].each do |this|
      this[0..2].each {|e| squares[0] << e}
    end
    @rows[0..2].each do |this|
      this[3..5].each {|e| squares[1] << e}
    end
    @rows[0..2].each do |this|
      this[6..8].each {|e| squares[2] << e}
    end

    @rows[3..5].each do |this|
      this[0..2].each {|e| squares[3] << e}
    end
    @rows[3..5].each do |this|
      this[3..5].each {|e| squares[4] << e}
    end
    @rows[3..5].each do |this|
      this[6..8].each {|e| squares[5] << e}
    end

    @rows[6..8].each do |this|
      this[0..2].each {|e| squares[6] << e}
    end
    @rows[6..8].each do |this|
      this[3..5].each {|e| squares[7] << e}
    end
    @rows[6..8].each do |this|
      this[6..8].each {|e| squares[8] << e}
    end
```


is this going to look good? 
