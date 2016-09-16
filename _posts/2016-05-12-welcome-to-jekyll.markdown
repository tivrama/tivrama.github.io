---
layout: post
title:  "Linked List"
date:   2016-05-12 07:00:17 -0700
categories: jekyll update
---






Linked list is a data structure that took me a while to understant exactly what it was all about.  I was confused about why one would simply not just use an array of objects.  And when consturcting one for the first time, I simply maked a collection of objects that were not truely a list.  But my understanding has increased, and I am starting to appreciate Linked List's bennifits.  

- The size can change without having to reassign every item in the list 
- Constant time insertaion and removal
- Lends itself well to recursion

For me, understanding how a Linked List works was dificult because I didn't really see what the individual objects like.

```
var myList = {};
myList.head = null
myList.tail = null
```

Making the first object:

```
myList.head = {value: 'Hello',
               next: null}
myList.tail = {value: 'Hello',
               next: null };
```

Inserting the second object.  The tail is reassigned.  Tail will alway have a 'next' value of null.

```
myList.head = {value: 'Hello',
               next: {value: 'World',    
                      next: null }}
```

Inserting a third object

myList.head = {value: 'Hello',
							 next: {value: 'World' 
											next: {value: 'BackAtchya',
														 next: null }}}




<!-- Working on understanding the four basic data structures in JavaScript and how to work with them.  These are Functional, Functional Sharred, Prototypal, and Pseudoclassical.  I am deffinitly feeling the Pseudoclassical more at this point.  It looks way easier to use.  Fortunately, some of the seniors in in the cohort ahead, directed me to Ryan Atkinson's awsome blog on these very structures: [JavaScript Classes and Instantiation Patterns](http://www.ryanatkinson.io/javascript-instantiation-patterns/)

There's not much point in my repeating what is on his blog.  What I will say is that from my total noob perspective, I would lean towards using Pseudoclassical because it seem way more straight forward than all the others - with the exception of Functional. --> 



[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
