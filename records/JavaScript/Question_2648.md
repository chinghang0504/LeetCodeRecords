# [LeetCode Records](../../README.md) - Question 2648 Generate Fibonacci Sequence

### Attempt 1: Use yield and save the previous two values
```js
/**
 * @return {Generator<number>}
 */
var fibGenerator = function*() {
    yield 0;
    yield 1;

    let prev1 = 0;
    let prev2 = 1;
    while (true) {
        let prev3 = prev1 + prev2;
        prev1 = prev2;
        prev2 = prev3;
        yield prev3;
    }
};

/**
 * const gen = fibGenerator();
 * gen.next().value; // 0
 * gen.next().value; // 1
 */
```
- Runtime: 43 ms (Beats: 92.07%)
- Memory: 48.87 MB (Beats: 59.71%)

<br>
