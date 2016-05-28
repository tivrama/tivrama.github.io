---
layout: post
title:  "Quick Reference for Basic Data Structures"
date:   2016-05-27 07:00:17 -0700
categories: jekyll update
---

## Hash Table  

- A collection in which data is stored and retrieved via a hashing function.
- Data is added and retrieved in constant time.
- No need for reassignment of indexes if a value is removed or added.  Time complexity is constant O(1).

{% highlight ruby %}

[  [  ['hello', 'world'], ['foo', 'bar'] ], [ [  ] ], [  ['good', 'night']  ]  ]
1  2  3[0]      [1]       3[0]    [1]       2 3       2  3[0]     [1]

  [0]hashed index                          [1]       [2]       

{% endhighlight %}

1.  The entire hash table as an array.
2.  Bucket which holds a tuple containing input data.  A bucket can have more than one tuple if a collision occurs.  Note: an example of a collision at the first hash index with two tuples in one bucket.  
3.  Tuple that holds the actual key value pairs.

---


## Linked List  

- A collection in which data is stored and retrieved from the head or tail.
- Data is added and retrieved in constant time O(1), but searched in linear time O(n).
- Length of collection changes to suit the number of objects.

{% highlight ruby %}

myList.head = {value: 'hello',
               next:  {value: 'world' 
                       next: {value: 'foo',
                              next: {value: 'bar' 
                                     next: null }}}}

               1       2      2      3

{% endhighlight %}           


1.  Head is the first value and is saved to a var called 'head'.
2.  Can have any number of middle values.  Search is done by loop or recursion.    
3.  Tail always has the next key assigned to null.  

---


## Graph  

- A collection of nodes connected by matching edges.  
- Two nodes with matching edges is a symmetrical match.  
- A node with an edge for another node (whose edge does not match for first node), is an asymmetrical match.  
- The world wide web is a collection of nodes with links acting like edges. 
- Search time complexity is akin to linked list at O(n).  Adding a node is also similar to linked list at constant O(1).

{% highlight ruby %}

1    {value: 'hello', edge: ['world']}


2      {value: 'world', edge: ['hello', 'bar']}


3  {value: 'foo', edge: ['bar']}


4        {value: 'bar', edge: ['foo', 'hello', 'world']}

{% endhighlight %}           


1.  Node with the value 'hello'.  Has and edge for the node with the value of 'world'.
2.  This node has an edge with 'hello', and therefore has a symmetrical match with 'hello'.  It also has an asymmetrical match for bar.  ('Bar' does not have an edge for 'world').
3.  This node has an edge for 'bar'.
4.  'Bar'  has an edge for the other three nodes.   

---


## Binary Search Tree  

- Nodes have a value and 0, 1 or 2 children.  If there is a child on the left branch, its value must be lower than the current node's value.  A branch on the right must have a node with a greater value than the current node.  
- Search time is logarithmic - O(log(n)).

{% highlight ruby %}

1   {value: 6,
2L   left: {value: 4,
3L          left: {value: 2,
                   left: null,
                   right: null
                   }
3R          right: {value: 5,
                    left: null,
                    right: null
                   }
           }
2R   right: {value: 9,
3L           left: {value: 7,
4L                  left: {value: 6,
                           left: null,
                           right: null
                          }
                    right: null
                   }
3R           right: {value: 10,
                     left: null,
                     right: null
                    }
            }
    }


{% endhighlight %}           


1.  Root tree.
2.  Left and right branches of the root.  The left has a lesser value of 4.  The right has a greater value of 9.     
3.  More branches.  
4.  Last branch of this tree with a value of 6.


---


## Set 

- Collection of objects.  The objects can belong to more than one set at a time;
- Objects belonging to more than one set are intersecting.  

{% highlight ruby %}

1   obj1 = {hello: 'world'}
    obj2 = {foo: 'bar'}
    obj3 = {good: 'night'}

2   a = {set: [obj1, obj2]}

    b = {set: [obj2, obj3]}
 
               3
{% endhighlight %}           


1.  Some objects.
2.  Two sets (a and b).    
3.  Obj 2 is a member of both set a and set b.  

---


## Tree

- Similar to Binary Search Tree, A tree is a node which potentially, has children.
- There is no set limit for the number of children a tree can have.
- Searches are done with recursive logarithms.  Time complexity is quadratic O(n3).

{% highlight ruby %}

1    {value: 'hello', 
2     children: [{value: 'world',   {value: 'foo'}]}
3                 children: []}      children: [{value: 'bar', {value: 'baz'}]
                                                 children: []}  children: []}

{% endhighlight %}           


1.  Parent tree has two children, 'world' and 'foo'.
2.  'World' has no children.  But 'foo' does have two children.  
3.  'Bar' and 'baz' are children of 'foo'.  

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
