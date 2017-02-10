---
layout: post
title:  "Approaches to Flattening and Array, An Object, and Both at the Same Time"
date:   2016-04-09 13:10:17 -0700
categories: jekyll update
---
<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`,  or jekyll serve -' (which actually worked - j.s.)  /blog'which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets: -->

Flatten is a method on the Array object that removes any nested array so that the result is only one level deep.  Below is is an example of what this is doing in the most simple way.  But what if we want it to flatten objects as well?  What might that look like, and how would we go about it?  

Here is flatten in its simplest form:


```
  [].flatten = function(nestedArray) {
    return nestedArray.reduce(function(a, b){
      if(Array.isArray(b)){
        return a.concat(b.flatten());
      }
      return a.concat(b); 
    }, []);

  };

  var multiDimenArray = [1, [2], [3, [[[4]]]]];
  var testFlatten = multiDimenArray.flatten();
  console.log(testFlatten); //-->[1, 2, 3, 4]
```

Here is a way we might flatten an object:

```

var flatten = function(obj) {
  var returnObj = {};
  var currentKey = '';
  
  var sub = function(ob) {
    for (var key in ob) {
      if (typeof ob[key] === 'string') {
        if (currentKey === '') {
          returnObj[key] = ob[key];
        } else {
          returnObj[currentKey + '.' + key] = ob[key];
        }
      } else if (currentKey === '') {
        currentKey = key;
      } else {
        currentKey = currentKey + '.' + key;
      }
      if (typeof ob[key] !== 'string') {
        sub(ob[key]);
      }
    }
    currentKey = '';
  }
  sub(obj);

  return returnObj;
}

```


<!-- Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk]. -->

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
