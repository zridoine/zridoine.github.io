---
title: Algorithm - Babbling
date: 2023-05-28 20:39:30 +09:00
categories: [JavaScript, Algorithm]
tags: [javascript, algorithm] # TAG names should always be lowercase
---

# Problem Solving

## [Babbling](https://school.programmers.co.kr/learn/courses/30/lessons/120956)

Mukju is taking care of his 6-month-old nephew who can only make combinations of the four pronunciations "aya", "ye", "woo", and "ma". Given a string array called "babbling", complete the solution function to return the number of words that Mukju's nephew can pronounce.

---

**_Constraints:_**  
1 ≤ Length of babbling ≤ 100  
1 ≤ Length of babbling[i] ≤ 15

Each string in babbling contains "aya", "ye", "woo", and "ma" only once.
In other words, among all possible substrings of each string, "aya", "ye", "woo", and "ma" appear only once.
The strings consist of lowercase alphabets only.

---

**_Example_**

| babbling                                    | result |
| :------------------------------------------ | :----: |
| ["aya", "yee", "u", "maa", "wyeoo"]         |   1    |
| ["ayaye", "uuuma", "ye", "yemawoo", "ayaa"] |   3    |

**_Explanation_**

- Example #1

  - Among the strings in ["aya", "yee", "u", "maa", "wyeoo"], only "aya" can be pronounced. Therefore, the function should return 1.

- Example #2
  - Among the strings in ["ayaye", "uuuma", "ye", "yemawoo", "ayaa"], the following combinations can be pronounced: "aya" + "ye" = "ayaye", "ye", and "ye" + "ma" + "woo" = "yemawoo". So, the function should return 3.

---

**_Note_**  
It is considered that only the pronunciations formed by combining the four given pronunciations are possible. For example, "woowo" cannot be pronounced because it contains "woo" but lacks "wo".

---

## Solution

```js
function solution(babbling) {
  let result = [];
  let answer = [];
  let count = 0;
  babbling.forEach((element) => {
    let temp = element.replace(/(aya|ye|woo|ma)/g, "1");
    if (element != temp) {
      result.push(temp);
    }
  });
  result.forEach((i) => {
    answer.push(i.replace(/(1)/g, ""));
  });
  answer.forEach((i) => {
    if (i == "") count += 1;
  });
  return count;
}
```

Replace the occurrences of "aya", "ye", "woo", and "ma" in the `babbling` string with "1".  
For example, ["aya", "yee", "u", "maa", "wyeoo"] becomes ["1", "1e", "u", "1a", "w1oo"].

Select the modified elements and store them in the `result` array.

Replace all occurrences of "1" in the `result` array with an empty string.  
For example, ["1", "1e", "u", "1a", "w1oo"] becomes ["", "e", "u", "a", "woo"].

Count the number of empty strings in the `result` array and store the count in the `count` variable.

Return the `count`.

---

## Comment

I came across another person's solution and I was astonished.  
They were able to solve the problem so simply using just regular expressions.  
It's incredible how concise it is.

```js
function solution(babbling) {
  var answer = 0;
  const regex = /^(aya|ye|woo|ma)+$/;

  babbling.forEach((word) => {
    if (regex.test(word)) answer++;
  });

  return answer;
}
```

It's similar to my solution, but there is no overlapping code, making it much cleaner.  
It seems like they have a better understanding of regular expressions.

I also encountered the test() method for the first time, which checks for a match in a string.

I realized that I need to study regular expressions more in order to solve algorithm problems effectively.
