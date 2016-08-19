---
layout: post
title:  "Palindromes!"
date:   2016-08-17 07:00:17 -0700
categories: jekyll update
---

### Emordnilap!

I love palindromes.  So much so, that I made a site where you can test out user letterbased, binary, or even genomic palindromes.  [Check it out here!](http://palindrome-app.herokuapp.com)  But how do I test?  And what the heck is a binary palindrome or a genomic palindrome?  I'll get to those too in a sec.  First, let's look at letter based palindromes.

Letter based palindromes are by far the most well known.  A famous example is "Go hang a salami, I'm a lasagna hog!"  Weird Al Yankovic made an entire Bob Dylan parady written entirely in palindromes.  

For letter based palindromes, the heart of the test is in the code below.  I also check for letters that repeat too many times in a row, and then send all the words to an online dictionary to varify that they are real words.  But essentially, the code below uses regex to remove all non-letter chars, and then make a copy of the user's input, reverses it, and compares the two.  

{% highlight ruby %}

var isItReallyAPalindrome = function(userAttempt) {

  userAttempt = userAttempt.toLowerCase()
    .replace(/[\s`~!@#$%^&*0-9()_|+\-=?;:'",.<>\{\}\[\]\\\/]/gi, '');

  var tpmettAresu = userAttempt.split('').reverse().join('');

  return userAttempt === tpmettAresu;

};      

{% endhighlight %}

What about binary?  


[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
