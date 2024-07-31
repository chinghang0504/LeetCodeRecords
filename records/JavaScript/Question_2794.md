# [LeetCode Records](../../README.md) - Question 2794 Create Object from Two Arrays

### Attempt 1: Use hasOwnProperty() to check if the property already exists
```js
/**
 * @param {Array} keysArr
 * @param {Array} valuesArr
 * @return {Object}
 */
var createObject = function(keysArr, valuesArr) {
    const obj = {};

    for (let i = 0; i < keysArr.length; i++) {
        const key = keysArr[i];

        if (!obj.hasOwnProperty(key)) {
            const value = valuesArr[i];
            obj[key] = value;
        }
    }

    return obj;
};
```
- Runtime: 85 ms (Beats: 98.55%)
- Memory: 63.32 MB (Beats: 21.74%)

<br>
