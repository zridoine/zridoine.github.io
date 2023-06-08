---
title: Algorithm - Sum until it exceeds n
date: 2023-06-08 09:50:30 +09:00
categories: [JavaScript, Algorithm]
tags: [javascript, algorithm] # TAG names should always be lowercase
---

# Problem Solving

## [Sum until it exceeds n](https://school.programmers.co.kr/learn/courses/30/lessons/181884)

You are given an integer array, numbers, and an integer n as parameters. Write a solution function that adds the elements of numbers one by one from the beginning until the sum exceeds n. Return the sum of the elements added up to that point.

---

**_Constraints:_**

- 1 ≤ Length of numbers ≤ 100
- 1 ≤ Elements of numbers ≤ 100
- 0 ≤ n < Sum of all elements in numbers

---

**_Example_**

| numbers n                |  n  | result |
| :----------------------- | :-: | :----: |
| [34, 5, 71, 29, 100, 34] | 123 |  139   |
| [58, 44, 27, 10, 100]    | 139 |  239   |

**_Explanation_**

Example #1

- For the given example, let's go through the process of adding numbers according to the problem description:
  |i |numbers[i]| sum|
  |:--:|:--:|:--:|
  | | | 0|
  |0| 34| 34|
  |1| 5 |39|
  |2 |71 |110|
  |3 |29| 139|

  After adding 29, the sum becomes 139, which is greater than the given n value of 123. Therefore, we return 139.

Example #2

- For the second example, if we add the elements of numbers until the second-to-last element, the sum will be 139. Since 139 is not greater than the given n value of 139, we add the last element, which is 100. The sum becomes 239, which is greater than 139. Therefore, we return 239.

---

## Solution

```js
function solution(numbers, n) {
  let sum = 0;
  for (let i = 0; i <= numbers.length; i++) {
    sum += numbers[i];
    if (sum > n) return sum;
  }
}

// Testing the code
console.log(solution([34, 5, 71, 29, 100, 34], 123));
```

The first code block you provided works fine without any issues. However, the second code block using `forEach` returns `undefined` when using return inside the `forEach` loop.

The problem lies in the usage of `forEach`. When you use return inside a `forEach` loop, it only affects the loop itself and does not impact the enclosing `solution` function.

To resolve this issue, you can modify the code as follows:

```js
function solution(numbers, n) {
  let sum = 0;
  numbers.forEach((i) => {
    sum += i;
    if (sum > n) return sum;
  });
  return "solution return";
}

// Testing the code
console.log(solution([34, 5, 71, 29, 100, 34], 123));
```

By adding a return statement after the `forEach` loop, you can ensure that the desired value is returned from the `solution` function. In this case, the value will be "solution return" since the `forEach` loop does not return a value.

In contrast, when using the `for` loop as in the first code block, the return statement inside the loop will directly exit the function and return the sum value.

The different behaviors of `for` and `forEach` loops lead to this discrepancy.
