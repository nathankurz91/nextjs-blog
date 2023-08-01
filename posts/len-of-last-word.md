---
title: 'Find the Length of the Last Word in a String'
date: '2023-05-31'
---

Let's solve a coding challenge. We will discuss how to find the length of the last word in a string using javascript as our programming language.

First the problem statement:
**Given a string, return the length of the last word in the string.**

To understand how to solve the problem, let's start with an example. Let's say this is our string:

`const str = 'hello i am a string'`

We need to isolate the last word in the string, find its length, and return it. Let's start by isolating the last word. We can separate all of the words in this string and store them in an array. In javascript we use split for this.

`const words = str.split(' ');`

We pass a space into the function as the delimiter. This will separate the words into the array by the spaces. Once we have our array, we need to target the last element of the array and get it's length.

`const lastWordLength = words[words.length - 1].length;`

We can then return this value and our function is complete. There are two edge cases we inspect. What if there are extra spaces in our string?

`str = '   hello i am   a string    '`;

To account for this edge case, we need to trim the extra space from the string before we split it. The code would change to this.

`const words = str.trim().split(' ');`

The other edge case is if the string is an empty string. In this case, we would just return 0;

Now we have accounted for our edge cases and the problem is effectively solved. This is what the completed function could look like.

```
function lengthOfLastWord(s) {
    if (s.length === 0) {
        return 0;
    } else {
        const words = s.trim().split(' ');
        const lengthOfLastWord = words[words.length - 1].length;
        return lengthOfLastWord;
    }
};
```

That's it! Have a wonderful day!
