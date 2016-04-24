---
layout: post
title:  "Fibonacci Numbers"
date:   2016-04-22 13:10:17 -0700
categories: jekyll update
---

I mentioned in my last post that we had been working with recursion.  We had a self assessment which required us to find the nth sequence of the Fibonacci numbers.  We were instructed to solve without doing research on the web.  Looking up the mathematical equation was fine, but seeing how other folks put it in code was not.  

After my mind was thoroughly blown by trying to figure it out, I turned in what I had, and began to research in earnest.  There is lots of interesting stuff out there.  It all started with rabbits!  Seriously - look it up!  But while the inspiration for the sequence may be odd, the pattern actualy does exist in nature.  For example, in the branching of a tree, or in the spiral of a shell.  

So the sequence goes like this:  
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144...
The way it works is 0 + 1 = 1, 1 + 1 = 2, 1 + 2 = 3, 2 + 3 = 5, and so on.  If n is the generation, you can find the number after the nth generation by making a loop.  

Here is the version which uses a loop: 
{% highlight ruby %}
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
{% endhighlight %}

But the TGA self assessment specifically wanted us to find the number at the nth generation using recursion.  I tried to do this using recursion, but counting forwards.  That was pretty mis-guided.  Because the formula (Fn = Fn−1 + Fn−2) obviously counts backwards.  Below are some working examples of how to implement the formula in code.  

This is a fairly standard version, and the one I got from CodeAcademy.  
{% highlight ruby %}
var fibonacciNumber = function(n){
    if(n <= 2) {
    return 1;
  }
  return fibonacciNumber(n-1) + fibonacciNumber(n-2);
}
{% endhighlight %}


Here is another version:
{% highlight ruby %}
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
{% endhighlight %}

This is the version I saved after helpful guidance from the folks at TGA.  It has the advantage of logging a count to see where the current depth of the recursion is.  Hint, don't make n higher than 40, or you'll probably be restarting your browser:
{% highlight ruby %}
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
{% endhighlight %}

These all do about the same thing.  They use recursion to count down from n to one, and then add up all the ones.  It works by making trees and then adding up the branches.  Here is what it might look like: 
{% highlight ruby %}
//to the third generation:
(2 + 3 = 5)
(0 + 1 = 1) + (1 + 2 = 3)
1 + (0 + 1 = 1)
//add up the ones
1 + 1 = 2
{% endhighlight %}



[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
