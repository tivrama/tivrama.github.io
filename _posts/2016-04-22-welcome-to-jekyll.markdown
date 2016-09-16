---
layout: post
title:  "Fibonacci Numbers"
date:   2016-04-22 13:10:17 -0700
categories: jekyll update
---

I mentioned in my last post this I had been working with recursion.  One common demonstration of its use is with the Fibonacci Numbers.  

In case you didn't know, there is lots of interesting stuff out there on the Fibonacci Numbers.  It all started with rabbits!  Seriously - look it up!  But while the inspiration for the sequence may be odd, the pattern actually does exist in nature.  For example, in the branching of a tree, or in the increasing spiral arch of a shell.  

So the sequence goes like this:  
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144...
The way it works is 0 + 1 = 1, 1 + 1 = 2, 1 + 2 = 3, 2 + 3 = 5, and so on.  If n is the generation, you can find the number after the nth generation by making a loop.  

Here is the version which uses a loop: 
```
  var fibonacciNumber= function(n){
    var counter,
        first = 0,
        second = 1,
        next = 0;

    for(counter = 0; counter < n; counter++) {

      next = first + second;
      first = second;
      second = next;

    }
    return next;
  }
```

But a more interesting way of doing it (to me, anyways), is to use the original formula from which the sequence gets its name.  (Fn = Fn−1 + Fn−2).  Below are some working examples of how to implement the formula in code.  

This is a fairly standard version, and the one I got from CodeAcademy.  
```
  var fibonacciNumber = function(n){
      if(n <= 2) {
      return 1;
    }
    return fibonacciNumber(n-1) + fibonacciNumber(n-2);
  }
```


Here is another version:
```
  var fibonacciNumber = function(n){
    if(n === 0) {
      return 0;
    }
    else if(n === 1){
      return 1;
    }
    else {
      return fibonacciNumber(n-1) + fibonacciNumber(n-2);
    }
  }
```

This is the version I saved after helpful guidance from the folks at TGA.  It has the advantage of logging a count to see where the current depth of the recursion is.  Hint, don't make n higher than 40, or you'll probably be restarting your browser:
```
  var fibonacciNumber= function(n){
    var count = 0;
    var fibo = function(n){
      
      console.log("depth of recursion:", count);
      console.log("current number", n);
      
      if(n <= 1){
        return n;
      }
      count++
      return fibo(n-1) + fibo(n-2);
    } 
    
    return fibo(n);
    
  };
```

These all do about the same thing.  They use recursion to count down from n to one, and then add up all the ones.  It works by making trees and then adding up the branches.  Here is what it might look like: 
```
  //to the third generation:
  (2 + 3 = 5)
  (0 + 1 = 1) + (1 + 2 = 3)
  1 + (0 + 1 = 1)
  //add up the ones
  1 + 1 = 2
```



[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
