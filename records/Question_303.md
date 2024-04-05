# [LeetCode Records](../README.md) - Question 303 Range Sum Query - Immutable

### Attempt 1: Calculate the sum at each time
```java
class NumArray {

    int[] arr;

    public NumArray(int[] nums) {
        this.arr = nums;
    }
    
    public int sumRange(int left, int right) {
        int sum = 0;
        for (int i = left; i <= right; i++) {
            sum += this.arr[i];
        }
        return sum;
    }
}
```
- Runtime: 55 ms (Beats: 14.57%)
- Memory: 49.81 MB (Beats: 5.92%)

<br>

### Attempt 2: Use an array to store accumulates
```java
class NumArray {

    int[] arr;

    public NumArray(int[] nums) {
        this.arr = new int[nums.length];
        for (int i = 0, sum = 0; i < nums.length; i++) {
            sum += nums[i];
            arr[i] = sum;
        }
    }

    public int sumRange(int left, int right) {
        return left != 0 ? this.arr[right] - this.arr[left - 1] : this.arr[right];
    }
}
```
- Runtime: 7 ms (Beats: 100.00%)
- Memory: 49.57 MB (Beats: 19.42%)

<br>
