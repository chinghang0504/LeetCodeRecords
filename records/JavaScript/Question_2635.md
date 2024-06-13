# [LeetCode Records](../../README.md) - Question 2635 Apply Transform Over Each Element in Array

### Attempt 1: 
```js
var map = function(arr, fn) {
    const newArr = [];
    for (let i = 0; i < arr.length; i++) {
        newArr.push(fn(arr[i], i));
    }
    return newArr;
};
```
- Runtime: 45 ms (Beats: 87.77%)
- Memory: 49.26 MB (Beats: 8.34%)

<br>
