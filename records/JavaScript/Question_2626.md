# [LeetCode Records](../../README.md) - Question 2626 Array Reduce Transformation

### Attempt 1: 
```js
var reduce = function(nums, fn, init) {
    let accum = init;

    for (let i = 0; i < nums.length; i++) {
        accum = fn(accum, nums[i]);
    }

    return accum;
};
```
- Runtime: 44 ms (Beats: 95.15%)
- Memory: 49.20 MB (Beats: 55.59%)

<br>
