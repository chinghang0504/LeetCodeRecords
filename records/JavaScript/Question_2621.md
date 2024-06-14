# [LeetCode Records](../../README.md) - Question 2621 Sleep

### Attempt 1: 
```js
async function sleep(millis) {
    return new Promise(resolve => setTimeout(resolve, millis));
}
```
- Runtime: 42 ms (Beats: 95.52%)
- Memory: 49.18 MB (Beats: 11.17%)

<br>
