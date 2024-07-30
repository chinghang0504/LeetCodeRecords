# [LeetCode Records](../../README.md) - Question 2726 Calculator with Method Chaining

### Attempt 1: Save the value in the calculator
```js
class Calculator {
    
    /** 
     * @param {number} value
     */
    constructor(value) {
        this.value = value;
    }
    
    /** 
     * @param {number} value
     * @return {Calculator}
     */
    add(value){
        this.value += value;
        return this;
    }
    
    /** 
     * @param {number} value
     * @return {Calculator}
     */
    subtract(value){
        this.value -= value;
        return this;
    }
    
    /** 
     * @param {number} value
     * @return {Calculator}
     */  
    multiply(value) {
        this.value *= value;
        return this;
    }
    
    /** 
     * @param {number} value
     * @return {Calculator}
     */
    divide(value) {
        if (value === 0) {
            throw new Error("Division by zero is not allowed");
        }

        this.value /= value;
        return this;
    }
    
    /** 
     * @param {number} value
     * @return {Calculator}
     */
    power(value) {
        this.value = Math.pow(this.value, value);
        return this;
    }
    
    /** 
     * @return {number}
     */
    getResult() {
        return this.value;
    }
}
```
- Runtime: 42 ms (Beats: 93.62%)
- Memory: 48.59 MB (Beats: 75.53%)

<br>
