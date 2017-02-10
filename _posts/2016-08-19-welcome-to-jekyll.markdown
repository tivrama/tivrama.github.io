---
layout: post
title:  "Palindromes!"
date:   2016-08-17 07:00:17 -0700
categories: jekyll update
---

### Emordnilap!

I love palindromes.  So much so, that I made a site where you can test out letter based, binary, or even genomic palindromes.  [Check out EmordnilaPalindrome here!](http://www.emordnilapalindro.me)  But how do I test?  And what the heck is a binary palindrome or a genomic palindrome?  I'll get to those too in a sec.  First, let's look at letter based palindromes.

Letter based palindromes are by far the most well known.  A famous example is "Go hang a salami, I'm a lasagna hog!"  [Weird Al Yankovic](https://www.youtube.com/watch?v=JUQDzj6R3p4) made an entire Bob Dylan parody written entirely in palindromes.  

For letter based palindromes, the heart of the test is in the code below.  I also check for letters that repeat too many times in a row, and then send all the words to an online dictionary to verify that they are real words.  But essentially, the code below uses regex to remove all non-letter chars, and then make a copy of the user's input, reverses it, and compares the two.  

```

var isItReallyAPalindrome = function(userAttempt) {

  userAttempt = userAttempt.toLowerCase()
    .replace(/[\s`~!@#$%^&*0-9()_|+\-=?;:'",.<>\{\}\[\]\\\/]/gi, '');

  var tpmettAresu = userAttempt.split('').reverse().join('');

  return userAttempt === tpmettAresu;

};      

```
Or perhaps, to save some time - save this onto the String prototype:

```

String.prototype.isItReallyAPalindrome = function() {
  var userAttempt = '';
  userAttempt = this.toLowerCase()
    .replace(/[\s`~!@#$%^&*0-9()_|+\-=?;:'",.<>\{\}\[\]\\\/]/gi, '');

  var tpmettAresu = userAttempt.split('').reverse().join('');

  return userAttempt === tpmettAresu;

};      

```


What about binary?  Simply put, it is  number that reads the same backwards.  For example '101101'.  That isn't too hard to test.  But if you happen to have a reeeally long one, you can test it with a function on on EmordnilaPalindrome.  Quick question:  is there a decimal number that is a palindrome (i.e. 454) which is also a palindrome in binary?  The only ones from 0 to 10 million are '0' and '1'.  But if you want to burn out your processor, you can run this function with as high a range as you may want.  

```

var bothBinAndDecPalindrome = function(runUpToN) {

  // This is the object that we will return
  var palin = {
    number: [],
    binary: [],
    both: []
  };

  // We will increment this number from '0' and check it
  var currentNumber = 0;

  // This will be the currentNumber in binary from
  var bin;

  // This is the actual palindrome checker
  var isPalindrome = function (number) {
    num = number.toString().split('').reverse().join('');
    return num === number.toString();
  };

  // Here we run through all the numbers and run them through 
  // our isPalindrome function
  while (currentNumber <= runUpToN) {
    bin = (currentNumber >>> 0).toString(2);
    if (isPalindrome(currentNumber)) {
      palin.number.push({[currentNumber]: bin})
    }
    if (isPalindrome(bin)) {
      palin.binary.push({[currentNumber]: bin})
    }
    if (palin.number[currentNumber] && palin.binary[currentNumber]) {
      palin.both.push({[currentNumber]: bin})
    }
    currentNumber++;
  }

  return palin;
};    

```


One thing I learned about when researching palindromes, is that they exist in out genetic code.  Important features in our code are sometimes in palindromes.  This may prevent degradation with copying our DNA.  Check out this [wikipedia article](https://en.wikipedia.org/wiki/Palindromic_sequence).  Each nucleotide has a pair or opposite.  It is those pairs, which when read backwards, must match the original. To check that in a function, I just made an object with the pairs. 

```

var isItPalindrome = function(word) {

  var DNA = {
    a: 't',
    c: 'g',
    g: 'c',
    t: 'a'
  };

  var RNA = {
    a: 'u',
    c: 'g',
    g: 'c',
    u: 'a'
  };

  word = word.toLowerCase()
    .replace(/[\s`~!@#$%^&*0-9()_|+\-=?;:'",.<>\{\}\[\]\\\/]/gi, '');
  var match = [];

  var checkFor = DNA;
  for (var i = 0; i < word.length; i++) {
    if (word[i] === 'u') {
      checkFor = RNA;
    }
  }

  for (var j = 0; j < word.length; j++) {
    match.unshift(checkFor[word[j]]);
  }
  match = match.join('');

  return match === word;
}; 

```

So what next?  How about an app that make palindromes.  But we would have to define some parameters.  For example, does it have to make some kind of sense when read?  If so, what kind of grammatical algorithm would be needed?  A good test for this my be to start with word based palindromes (as opposed to letter based).  More on that soon.  

I hope you enjoy palindromes as much as I do.  I'll leave you with this deep thought.

"Do nine men interpret? Nine men, I nod."

