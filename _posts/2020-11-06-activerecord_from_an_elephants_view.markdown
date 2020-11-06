---
layout: post
title:      "ActiveRecord From an Elephants View!"
date:       2020-11-06 20:04:39 +0000
permalink:  activerecord_from_an_elephants_view
---


As my personal Software Engineering education journey continues, I've been fortunate enough to gather advice from the very informed.  I say this because we all tend to look at whats in front of us without really getting the clear view of it.  It's like looking at an elephant close up and when you are that close you can't see much but only the thick grey skin, which can be intestering and fun.  But, stepping back, one can see the amazing complexity it is we call an elephant with everything that surrounds it.  

In comes Active Record.  At close glance it is easy to miss the bigger picture.  Active Record is an ORM(Object Relational Mapping) system.  In plain terms for us newbies, it carries the weight of processes perfromed by SQL along with data manipulation.  Traditional SQL is as such:

```
CREATE TABLE products (
   id int(15) NOT NULL auto_increment,
   name varchar(255),
   PRIMARY KEY  (id)
);
```

With Active Record, implementation is as such:

```
class Product < ApplicationRecord
end
```

This code allows us Tech students to use a great deal of code helpers to facilitate a simplier and more cohesive structure in regards to application creation. 

But why is this relevant?  For me personally, understanding the particular intricate portions of Active Record is vital.  While live coding I tripped up on a few ideas related to scope.  Scope essentially is the method of drilling down on the particulates of what you need your application to return to the user or for application funtionality and so on (specifying queries.  While live coding I didn't quite get to where I needed to go effectively enough and it was only because I somewhat misrepresented how and when to utilize scope.  Eventually, I understood and completed the task (on my own), but in order to get there I had to refresh myself with Active Record Query Interface.  In the end I completed my personal task of creating a search bar with a scope as such:

```
def self.search(search)
    self.where("make like ?", "%#{search}%" )
end
```

This scope method looks for the make of a vehicle by letter or by fully spelling out the actual name. 

Here's the take away for all of what I am saying.  Querying an object is only a portion of what Active Record is capable of and is only looking at the Elephant up close.  If you look at it only up close, you will surely miss the beauty of it from the full picuture.  This was one of my personal challenges but am pushing forward to gain deeper understanding and a deeper level of effective efficient use of the Active Record tool.  And, if you are a newby like me, try stepping back and getting the full Active Record picture.
