# [LeetCode Records](../../README.md) - Question 2690 Infinite Method Object

### Attempt 1: Use Proxy()
```js
/**
 * @return {Object}
 */
var createInfiniteObject = function() {
    const proxy = new Proxy({}, {
        get: (_, key) => {
            return () => key;
        }
    });
    
    return proxy;
};

/**
 * const obj = createInfiniteObject();
 * obj['abc123'](); // "abc123"
 */
```
- Runtime: 43 ms (Beats: 87.81%)
- Memory: 49.04 MB (Beats: 7.32%)

<br>
