# [LeetCode Records](../../README.md) - Question 2704 To Be Or Not To Be

### Attempt 1: 
```js
var expect = function(val) {
    return {
        toBe: function(newVal) {
            if (val === newVal) {
                return true;
            } else {
                throw 'Not Equal';
            }
        },
        notToBe: function(newVal) {
            if (val !== newVal) {
                return true;
            } else {
                throw 'Equal';
            }
        }
    }
};
```
- Runtime: 42 ms (Beats: 95.41%)
- Memory: 48.58 MB (Beats: 76.65%)

<br>
