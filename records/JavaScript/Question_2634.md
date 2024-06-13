# [LeetCode Records](../../README.md) - Question 2634 Filter Elements from Array

### Attempt 1: 
```js
var filter = function(arr, fn) {
    const newArr = [];

    for (let i = 0; i < arr.length; i++) {
        if (fn(arr[i], i)) {
            newArr.push(arr[i]);
        }
    }

    return newArr;
};
```
- Runtime: 47 ms (Beats: 86.14%)
- Memory: 48.71 MB (Beats: 71.30%)

<br>
