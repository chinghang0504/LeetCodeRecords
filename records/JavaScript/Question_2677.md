# [LeetCode Records](../../README.md) - Question 2677 Chunk Array

### Attempt 1: 
```js
var chunk = function(arr, size) {
    let result = [];

    let i = 0;
    while (i < arr.length) {
        let part = [];

        for (let j = i; (j < i + size) && (j < arr.length); j++) {
            part.push(arr[j]);
        }

        result.push(part);
        i += size;
    }

    return result;
};
```
- Runtime: 49 ms (Beats: 86.88%)
- Memory: 51.95 MB (Beats: 23.30%)

<br>
