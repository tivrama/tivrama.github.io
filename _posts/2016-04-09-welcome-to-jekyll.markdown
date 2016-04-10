---
layout: post
title:  "First Sojourn into Blogging"
date:   2016-04-09 13:10:17 -0700
categories: jekyll update
---

This is my first blog, posted at the beginning of my journey into coding.  Right now my focus is on learning how to build basic helper functions, and how to use them effectively.  TGA is having us create the basic underscore functions.  A few I can solve on my own.  Some required research.  And some are still unsolved.  

One of my concerns is that I will find a solution on some site like stack overflow, tweak it enough to work, but still not fully understand how it works.  When that happens, I use 'debugger' to go step by step through the functions and see what is going on.

Below is a function for flattening multi-dimensional arrays.  It works up to a few layers deep, and I guess I could make it go much deeper.  But I really don't like the repeated code.  So my next step is to see if I can put it in a loop.  

<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets: -->

{% highlight ruby %}
 var _.flatten = function(nestedArray, result) {

    return _.reduce(nestedArray, function(a, b){
      if(Array.isArray(b)){
        b = _.reduce(b, function(c, d){
          if(Array.isArray(d)){
            d = _.reduce(d, function(e, f){
              if(Array.isArray(f)){
                f = _.reduce(f, function(g, h){
                  return g.concat(h);
                }, []);
              }
              return e.concat(f);
            }, []);
          }
          return c.concat(d);
        }, []);
      }
      return a.concat(b);
    }, []);
  }

  var multiDimenArray = [1, [2], [3, [[[4]]]]];
  var testFlatten = _.flatten(multiDimenArray);
  console.log(testFlatten); //-->[1, 2, 3, 4]
{% endhighlight %}



<!-- Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk]. -->

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
