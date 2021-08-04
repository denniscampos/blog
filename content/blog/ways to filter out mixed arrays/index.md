---
title: Ways to Filter Out Numbers and Strings in a Mixed Array.
date: "2021-08-04T22:12:03.284Z"
description: "Here are some ways I found to filter out numbers and strings in a mixed array."
---

# Introduction

I think the best way to learn about certain methods is to write about them! I encountered this problem on codewars and thought to share my experience.

## Instructions from Codewars

Simple enough this one - you will be given an array. The values in the array will either be numbers or strings, or a mix of both. You will not get an empty array, nor a sparse one.

Your job is to return a single array that has first the numbers sorted in ascending order, followed by the strings sorted in alphabetic order. The values must maintain their original type.

Note that numbers written as strings are strings and must be sorted with the other strings.

Now fair warning, this is to help beginners. I am aware this can be solved in soooo many ways.

![oh gosh...](https://media.giphy.com/media/H1BVR4DZG01KUWRXpV/giphy.gif)

When I read codewars problems, I try to find a "pattern". Many instructions on codewars are very vague to me. So I tend to look for keywords in the problem and having a look at the test cases. Now, if you are interviewing, your job is to ask as many questions as possible to get clarification before you try to solve the problem.

![questions](https://media.giphy.com/media/yRwYYk8Z7o3IY/giphy.gif)

## Let's Think

Let's check this out. The first thing they want us to do is to return a single array that has the numbers _sorted_ in ascending order. Anytime, I see the word sorted, I always think about the sort() method. Read more about it here: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

The way sort numbers in ascending order is by using the following method:

`arr.sort((a, b) => a - b)`

The sort method above will look at the first element and second element and sort them in ascending order. (Pssst, if you want it descending then do `b - a` instead)

So if we had something like `[4,5,3,2,4]` the result will log `[2,3,4,4,5]`

Great but let's look at the problem again. It's asking to sort the numbers followed by sorting the strings in alphabetic order.

Let's use this test case as an example from now on: `[4, 3, 6, 0, 7, "hello", "johnny", "new", "computer"]`

The goal is to turn the array into: `[0, 3, 4, 6, 7, "computer", "hello", "johnny", "new"]`

When we sort the numbers it will not mess with the string. So we can filter out the numbers and strings on their own array, and then sort them. In the end, we should concat to get the results above.

Here are two ways(my way) to filter out numbers.

`arr.filter(Number.isFinite).sort((a,b) => a - b)`

The reason I am using Number.isFinite as opposed to Number is because Number will not pick up the number 0 as 0 is falsy in JavaScript.
![clever](https://media.giphy.com/media/ZC0ATzzJnKqn2SNDHR/giphy.gif)

Read about _falsy_ here: https://developer.mozilla.org/en-US/docs/Glossary/Falsy

Read about Number.isFinite() method here: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isFinite)

Another way to grab the numbers in the filter method is using the typeof method (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/typeof)

`arr.filter(el => typeof el === "number").sort((a, b) => a - b)`

The filter will now filter out numbers only in a new array and sort them in ascending order.

You can now use the same method above but with a string this time.

`arr.filter(el => typeof el === "string").sort()`

If you noticed, I eliminated the parameters in the sort method. Honestly, depending on the question and test cases, this may differ depending where you are trying to solve the problem - ie. _leetcode_, _hackerrank_ or _codewars_.

To finish the problem, I used the concat method. You can read more about it here: (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

Here is the final result

```
function doubleSort(arr) {
    const sortNums = arr.filter(Number.isFinite).sort((a, b) => a - b);
    const sortStrings = arr.filter(str => typeof str === "string").sort();

    return sortNums.concat(sortStrings)
}

```

`doubleSort([4, 3, 6, 0, 7, "hello", "johnny", "new", "computer"])`
Results to `[0, 3, 4, 6, 7, "computer", "hello", "johnny", "new"]`

And there it is! If you enjoyed my content or want to share other cool ways of doing this problem, please do not hesitate to contact me!

<img src="https://media.giphy.com/media/ZfK4cXKJTTay1Ava29/giphy.gif" alt="Thank you" width="300"/>

Follow me on Twitter [@dnbull](https://www.twitter.com/dnbull)

Look forward to chatting with you!
