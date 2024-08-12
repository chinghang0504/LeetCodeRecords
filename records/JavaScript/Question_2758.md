# [LeetCode Records](../../README.md) - Question 2758 Next Day

### Attempt 1: Use setDate(), getFullYear(), getMonth(), getDate(), and padStart()
```js
/** 
 * @return {string}
 */
Date.prototype.nextDay = function() {
    this.setDate(this.getDate() + 1);

    let year = this.getFullYear();
    let month = (this.getMonth() + 1).toString().padStart(2, '0');
    let day = (this.getDate()).toString().padStart(2, '0');

    return `${year}-${month}-${day}`;
}

/**
 * const date = new Date("2014-06-20");
 * date.nextDay(); // "2014-06-21"
 */
```
- Runtime: 45 ms (Beats: 84.75%)
- Memory: 49.76 MB (Beats: 16.95%)

<br>
