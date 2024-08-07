# [LeetCode Records](../../README.md) - Question 2822 Inversion of Object

### Attempt 1: Use Object.keys(), hasOwnProperty(), Array.isArray(), push()
```js
/**
 * @param {Object|Array} obj
 * @return {Object}
 */
var invertObject = function(obj) {
    answer = {};

    for (let key of Object.keys(obj)) {
        let val = obj[key];
        if (answer.hasOwnProperty(val)) {
            if (Array.isArray(answer[val])) {
                answer[val].push(key);
            } else {
                answer[val] = [answer[val], key];
            }
        } else {
            answer[val] = key;
        }
    }

    return answer;
};
```
- Runtime: 144 ms (Beats: 95.35%)
- Memory: 64.12 MB (Beats: 67.44%)

<br>
