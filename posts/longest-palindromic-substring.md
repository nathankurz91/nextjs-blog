---
title: 'Longest Palindromic Substring: JavaScript'
date: '2022-04-13'
---

A palindrome is any set of characters that read the same forwards and backwards. For example: 'noon' is a palindrome, and 'loon' is not. Both of these strings contain palindromic substrings 'oo'.

## Objective

Find the longest set of characters in a string that is a palindrome, or the 'longest palindromic substring'.

## Solutions

### Solution 1

There are a few different ways to solve this, but I am going to stick to the two that I used personally. My initial thoughts were to get every possible substring and check if they were palindromes. If the string is a palindrome, check the length. If the length is greater than the length of the current longest, set the current longest equal to the current string.

This solution is straightforward and definitely works, however there is a glaring issue. It's very slow for large strings. You have a nested loop to get every possible substring which has a O(n^2) runtime, and you have to check each substring to see if it is a palindrome which is O(n) giving you a total runtime of O(n^3). I tested this solution using node on my terminal and it worked fine, but when I went to submit the solution it failed because it exceeded the time limit. Just in case you are curious I will show a copy of this solution below, but we will be looking at a much faster option next.

```js
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function (s) {
    // check base case
    // examine every possible substring
    // if substring and length is longer than current longest, set to longest
    // return longest
    if (isPalindrome(s)) {
        return s;
    }

    let current = '';

    for (let i = 0; i < s.length; i++) {
        for (let j = i + 1; j <= s.length; j++) {
            let ss = s.substring(i, j);
            if (isPalindrome(ss)) {
                if (ss.length > current.length) {
                    current = ss;
                }
            }
        }
    }
    return current;
};

function isPalindrome(s) {
    let reverse = s.split('').reverse().join('');
    if (s === reverse) {
        return true;
    } else {
        return false;
    }
}
```

### Solution 2

I had to research a few different ways of solving this problem. I chose to research an algorithm that appeared to be the least convoluted. I wrote out some pseudocode and went through a few iterations by hand to better understand the algorithm.

There is no need to check every possible substring. Instead, we can iterate through the string once. At each index, we check to see if the positions to the left and right of the current index are equal. If they are equal, then the substring is a palindrome. We continue incrementing and decrementing the left and right pointers until the substring is no longer a palindrome. If the substring is not a palindrome, we exit the inner loop and continue to the next index in the string (outer loop).

Below is a snippet of the code used in this solution.

```js
var longestPalindrome = function (s) {
    let longest = '';

    // loop through string once
    for (let i = 0; i < s.length; i++) {
        // use two different starting positions to
        // account for even or odd strings
        checkLeftAndRight(i, i);
        checkLeftAndRight(i, i + 1);
    }

    function checkLeftAndRight(left, right) {
        while (left >= 0 && right < s.length && s[left] === s[right]) {
            // subtract left from right and add one to get current
            // length of substring
            if (right - left + 1 > longest.length) {
                // set longest to current substring
                longest = s.slice(left, right + 1);
            }
            left--;
            right++;
        }
    }

    return longest;
};
```

## Conclusion

This was an interesting problem. My goal in practicing and analyzing these solutions is to one day have a big enough toolkit that I can think of multiple solutions for many of the problems I come across without having to research them. Hope this helps someone out there :)
