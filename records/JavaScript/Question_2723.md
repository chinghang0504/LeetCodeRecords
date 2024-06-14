# [LeetCode Records](../../README.md) - Question 2723 Add Two Promises

### Attempt 1: 
```js
var addTwoPromises = async function(promise1, promise2) {
    const val1 = await promise1;
    const val2 = await promise2;
    return val1 + val2;
};
```
- Runtime: 50 ms (Beats: 97.46%)
- Memory: 49.69 MB (Beats: 31.43%)

<br>
