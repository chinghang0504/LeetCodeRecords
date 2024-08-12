# [LeetCode Records](../../README.md) - Question 2695 Array Wrapper

### Attempt 1: Use toString()
```js
/**
 * @param {number[]} nums
 * @return {void}
 */
var ArrayWrapper = function(nums) {
    this.nums = nums;
};

/**
 * @return {number}
 */
ArrayWrapper.prototype.valueOf = function() {
    let sum = 0;
    for (let i = 0; i < this.nums.length; i++) {
        sum += this.nums[i];
    }
    return sum;
}

/**
 * @return {string}
 */
ArrayWrapper.prototype.toString = function() {
    return this.nums.length === 0 ? "[]" : `[${this.nums.toString()}]`;
}

/**
 * const obj1 = new ArrayWrapper([1,2]);
 * const obj2 = new ArrayWrapper([3,4]);
 * obj1 + obj2; // 10
 * String(obj1); // "[1,2]"
 * String(obj2); // "[3,4]"
 */
```
- Runtime: 46 ms (Beats: 90.34%)
- Memory: 50.61 MB (Beats: 17.69%)

<br>
