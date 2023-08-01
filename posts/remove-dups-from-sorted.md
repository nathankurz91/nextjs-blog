---
title: 'Remove Duplicates from Sorted Array'
date: '2022-04-08'
---

Let's talk about removing duplicates. Normally, removing duplicates from a sorted array would be quick work. You just add each value to a set. Since all values in sets must be unique you simply return the values contained in the set. This was not a valid solution for this problem.

The problem states that you have to modify the array in place. That means I can't create another data structure to store my values when I find any duplicates. Admittedly, the solution is still straightforward. I have not had the pleasure of using the splice() function in JavaScript too many times, so it took me a bit longer than I would have liked until I rediscovered it.

Now we will build the solution. I'll explain it first with some pseudocode, and then present the actual code below.

-   Loop through the array
-   The array size will change when we remove an element, so we need to use a variable to store the initial array length
-   check if i is greater than or equal to array.length
-   break if true
-   check if i equals i+1
-   if true, remove element at index i with splice()
-   decrement i to recheck that same position in case of further duplicates

Like I said, pretty straightforward. I tend to overthink these algorithm problems. That's why I'm practicing!

Solution:

```js
var removeDuplicates = function (nums) {
    let numsLength = nums.length;
    for (let i = 0; i < numsLength; i++) {
        if (i >= nums.length) {
            break;
        }
        if (nums[i] === nums[i + 1]) {
            nums.splice(i, 1);
            i--;
        }
    }
};
```

Hope you learned something!! Have a great day and remember to GO OUTSIDE :)
