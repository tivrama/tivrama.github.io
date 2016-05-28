---
layout: post
title:  "Stack and Queue"
date:   2016-05-06 07:00:17 -0700
categories: jekyll update
---

Stack and Queue are two data structures that look fairly similar.  The obvious difference is that with Stack, the first item placed in it, is the last one taken out (First In Last Out or LIFO).  A Queue is First In First Out (FIFO).  

I actually was familiar with the acronyms FIFO and LIFO from my last job, working in a warehouse.  Pallets were generally stored in a stack and so they followed LIFO.  But if there was a time protocol which had to be followed with the product, then we had to make a sort of Queue and ship by FIFO.  

For a basic Stack to work, one needs to have a method to add an item to the top (push), remove an item (pop), and keep track of the size of the stack with an index.  The index if very important.  In a practical sense, we don't want our computer to send a forklift to a location that is empty.  

Here is a simple representation of a stack.
{% highlight ruby %}
// Stack could be an location in a warehouse. 
// It must have an index that tracks how many 
// pallets are in that location.  

Stack = { index = 0; }

// Size method returns number of pallets in a location
Stack.size = function() { returns count of pallets }

// Push method adds a pallet to the front of the pile.
// It also updates the index
Stack.push = function( newPallet ) { adds pallet to location }

// Pop method removes a pallet from the front of the pile.
// It also updates the index.
Stack.pop = function() { removes pallet from location }
{% endhighlight %}

For a Queue, one would add pallets to one end of a location, and remove from the other end.  This is good for fast moving items that had an expire date.  

Like stack, There is an index which is updated when a pallet is added.  But it helps to have another running index which tracks the first pallet.  This way, the count of the pallets can be determined by subtracting one from the other.  

Here is a simple Queue.
{% highlight ruby %}
Queue = { index = 0, runningIndex = 0; }

// Queue has a size method that subtracts runningIndex from index
Queue.size = function() { returns count of pallets in the location }

// Queue has a method that adds a pallet and updates just the index
Queue.enqueue = function( newPallet ) { adds pallets to the back of the pile }

// Queue has a method that takes a pallet from the front of the pile
// The method then updates only the running index
Queue.dequeue = function() { removes a pallet from the front of the pile }
{% endhighlight %}

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
