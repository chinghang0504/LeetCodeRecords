# [LeetCode Records](../../README.md) - Question 2797 Partial Function with Placeholders

### Attempt 1: Save the args in the function and use a for loop to replace the underscores
```js
/**
 * @param {Function} fn
 * @param {Array} args
 * @return {Function}
 */
var partial = function(fn, args) {
    this.args = args;
    
    return function(...restArgs) {
        let index = 0;
        for (let i = 0; i < this.args.length && index < restArgs.length; i++) {
            if (this.args[i] == "_") {
                this.args[i] = restArgs[index];
                index++;
            }
        }

        while (index < restArgs.length) {
            this.args.push(restArgs[index]);
            index++;
        }

        return fn(...this.args);
    }
};
```
- Runtime: 58 ms (Beats: 88.68%)
- Memory: 54.54 MB (Beats: 67.92%)

<br>
