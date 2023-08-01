---
title: 'Decompress Run-Length Encoded List'
date: '2020-07-24'
---

Hello everyone!

Practicing LeetCode is one of my favorite ways to keep my mind and coding skills sharp. I don't think I would have been able to pass my interview questions without the help of LeetCode. I believe they provide a great service for developers everywhere. Without further ado, let's solve this thing!

## The official problem statement:

We are given a list nums of integers representing a list compressed with run-length encoding.

Consider each adjacent pair of elements `[freq, val] = [nums[2*i], nums[2*i+1]]` with `i >= 0` For each such pair, there are freq elements with value val concatenated in a sublist. Concatenate all the sublists from left to right to generate the decompressed list.

Return the decompressed list.

## Analysis

At first, this sounded a bit confusing to me, but it's basically just saying each pair of elements in the array represents a frequency and a value that needs to be stored in the new array. So if we were given an array `nums = [1, 2, 4, 6]` then our first pair would be (1, 2) and our second pair would be (4, 6). So from our first pair, we would store the value 2, one time. We would store the value 4, six times from the second pair.

## The solution

The way I went about solving this was straightforward. We need to go through the list one pair at a time, get the values for each pair, and append the appropriate values the correct amount of times. We will go through it step by step!

### Iterate over the list

We need to iterate over the given list of numbers one pair at a time. To do this, we can use a for loop that increments by two every iteration.

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var decompressRLElist = function (nums) {
    for (let i = 0; i < nums.length; i = i + 2) {}
};
```

### Grab 'freq' and 'val' from the corresponding indices.

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var decompressRLElist = function (nums) {
    for (let i = 0; i < nums.length; i = i + 2) {
        let freq = nums[i];
        let val = nums[i + 1];
    }
};
```

### Store 'val' in a new array 'freq' amount of times

I approached this portion by adding another loop (nested) to add the value the appropriate amount of times!

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var decompressRLElist = function (nums) {
    // create new array (decompressed list)
    let dcomList = [];
    for (let i = 0; i < nums.length; i = i + 2) {
        let freq = nums[i];
        let val = nums[i + 1];

        while (freq !== 0) {
            dcomList.push(val);
            freq--;
        }
    }
};
```

### Return the new decompressed list

The last thing to do is to return dcomList!

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var decompressRLElist = function (nums) {
    // create new array (decompressed list)
    let dcomList = [];
    for (let i = 0; i < nums.length; i = i + 2) {
        let freq = nums[i];
        let val = nums[i + 1];

        while (freq !== 0) {
            dcomList.push(val);
            freq--;
        }
    }

    return dcomList;
};
```

## Thoughts

My solution is a basic one, but it definitely gets the job done. I always like to solve these problems the simplest way I can, and then I go and look at the discussion page to see all the different ways other people go about solving them. This is probably what helps me grow most as a problem solver. It allows me to work through problems on my own, and then I can expand that knowledge through the work of others!

## Bonus solution

Here is a solution written by LeetCode user _ahmedengu_ that drastically reduces the number of lines of code (to just one)!

```javascript
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var decompressRLElist = function (nums) {
    return nums.reduce(
        (acc, v, i) =>
            i % 2 == 0 ? acc.concat(_.times(v, _.constant(nums[i + 1]))) : acc,
        []
    );
};
```

I see this type of solution to these problems on LeetCode all the time. I want to keep practicing and memorize the builtin javascript methods so that I can better utilize them to come up with unique solutions like this!

Happy Coding!
