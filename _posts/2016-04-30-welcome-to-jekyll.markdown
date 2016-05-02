---
layout: post
title:  "More Recursion Fodder"
date:   2016-04-30 13:10:17 -0700
categories: jekyll update
---

One of the Underscore functions we had to re-create for TGA is _.difference.  It takes multiple arrays and returns the elements on the first array that are unique to that first array.  The solution below works, but falls into the same issues I had when I first solved _.flatten.  There is repeated code and it can only handle as many arrays as you make loops for.  I know this can be made better with recursion. So if I find time, I will do that for next week's blog.  

But... It is the first day of class on Monday.  I think I am going to be pretty busy.  I think of it as boarding a submarine headed out to sea for three months.


{% highlight ruby %}
  _.difference = function(array) {
    //make a cashe to store items
    var cashe = array;

    //loop through argument[1]
    for(var i = 0; i < arguments[1].length; i++) {
      //check if arguments are in cashe
      if(_.contains(cashe, arguments[1][i])){
        //loop through cashe to find value and delete
        for(var j = 0; j < cashe.length; j++) {
          if(cashe[j] === arguments[1][i]){
            cashe.splice(j, j); 
          }
        }
      }
    }

    if(arguments.length > 2){
    for(var k = 0; k < arguments[2].length; k++) {
      //check if arguments are in cashe
      if(_.contains(cashe, arguments[2][k])){
        //loop through cashe to find value and delete
        for(var l = 0; l < cashe.length; l++) {
          if(cashe[l] === arguments[2][k]){
            cashe.splice(l, l+1); 
          }
        }
      }
    }
  }

    return cashe;

  };
{% endhighlight %}





[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
