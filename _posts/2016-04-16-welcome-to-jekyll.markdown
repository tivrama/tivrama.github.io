---
layout: post
title:  "Using Recursion"
date:   2016-04-16 13:10:17 -0700
categories: jekyll update
---

Last week I sorta replicated underscore's _.flatten function.  But it used lots of repeated code and only worked as deep as the repetition went (if that makes sense...).  I was planning on tightening it up with a loop.  But this week, TGA's pre-course work focused on recursion.  So I tried it, and my new version works much better.  (Check last week’s blog for my original version.)   

<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`,  or jekyll serve -' (which actually worked - j.s.)  /blog'which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets: -->

{% highlight ruby %}
  _.flatten = function(nestedArray, result) {
    // use reduce to concat each element together
    return _.reduce(nestedArray, function(a, b){
      // check if an element is a nested array
      if(Array.isArray(b)){
        // use recursion to cycle through the nested layers
        return a.concat(_.flatten(b));
      }
      // otherwise, concat
      return a.concat(b); 
    }, []);

  };

  var multiDimenArray = [1, [2], [3, [[[4]]]]];
  var testFlatten = _.flatten(multiDimenArray);
  console.log(testFlatten); //-->[1, 2, 3, 4]
{% endhighlight %}



<!-- Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk]. -->

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
