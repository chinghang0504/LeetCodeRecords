# [LeetCode Records](../../README.md) - Question 2666 Allow One Function Call

### Attempt 1: 
```js
var once = function(fn) {
    let isCalled = false;
    
    return function(...args){
        if (isCalled) {
            return undefined;
        }

        isCalled = true;
        return fn(...args);
    }
};
```
- Runtime: 43 ms (Beats: 94.57%)
- Memory: 48.90 MB (Beats: 42.54%)

<br>
