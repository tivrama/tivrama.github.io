---
layout: post
title:  "Re-creating Underscore's _.Flatten"
date:   2016-04-09 13:10:17 -0700
categories: jekyll update
---

One thing that I have found interesting is nested collections.  I got into this on [Reactivex.oi](http://reactivex.io/learnrx/).  That site guides users through the use of functions such as forEach, map, reduce and filter to get access to nested arrays and objects.  And it actually has you build versions of some of these functions.  

Below is a function for flattening multi-dimensional arrays.  It works up to a few layers deep, and I guess I could make it go much deeper.  But I really don't like the repeated code.  So my next step is to see if I can put it in a loop or find some other clever means of getting rid of re-invoking reduce.  

<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`,  or jekyll serve -' (which actually worked - j.s.)  /blog'which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets: -->

```
  var _.flatten = function(nestedArray) {

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
```



<!-- Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk]. -->

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
