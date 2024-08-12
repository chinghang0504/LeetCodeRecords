# [LeetCode Records](../../README.md) - Question 2715 Timeout Cancellation

### Attempt 1: Use setTimeout() and clearTimeout()
```js
/**
 * @param {Function} fn
 * @param {Array} args
 * @param {number} t
 * @return {Function}
 */
var cancellable = function(fn, args, t) {
    const timer = setTimeout(() => {
        fn(...args);
    }, t);

    return () => {
        clearTimeout(timer);
    }
};

/**
 *  const result = [];
 *
 *  const fn = (x) => x * 5;
 *  const args = [2], t = 20, cancelTimeMs = 50;
 *
 *  const start = performance.now();
 *
 *  const log = (...argsArr) => {
 *      const diff = Math.floor(performance.now() - start);
 *      result.push({"time": diff, "returned": fn(...argsArr)});
 *  }
 *       
 *  const cancel = cancellable(log, args, t);
 *
 *  const maxT = Math.max(t, cancelTimeMs);
 *           
 *  setTimeout(cancel, cancelTimeMs);
 *
 *  setTimeout(() => {
 *      console.log(result); // [{"time":20,"returned":10}]
 *  }, maxT + 15)
 */
```
- Runtime: 60 ms (Beats: 82.15%)
- Memory: 49.74 MB (Beats: 17.05%)

<br>
