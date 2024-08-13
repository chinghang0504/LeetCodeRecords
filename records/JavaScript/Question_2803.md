# [LeetCode Records](../../README.md) - Question 2803 Factorial Generator

### Attempt 1: Use yield
```js
/**
 * @param {number} n
 * @yields {number}
 */
function* factorial(n) {
    if (n === 0) {
        yield 1;
    } else {
        let curr = 1;
        for (let i = 1; i <= n; i++) {
            curr *= i;
            yield curr;
        }
    }
};

/**
 * const gen = factorial(2);
 * gen.next().value; // 1
 * gen.next().value; // 2
 */
```
- Runtime: 43 ms (Beats: 92.68%)
- Memory: 48.53 MB (Beats: 78.05%)

<br>
