# [LeetCode Records](../../README.md) - Question 703 Kth Largest Element in a Stream

### Attempt 1: 
```java
class KthLargest {

    private int[] arr;
    private int kVal;

    public KthLargest(int k, int[] nums) {
        kVal = k;
        
        arr = new int[20001];
        for (int num : nums) {
            arr[num + 10000]++;
        }
    }

    public int add(int val) {
        arr[val + 10000]++;

        int sum = 0;
        for (int i = 20000; i >= 0; i--) {
            sum += arr[i];
            if (sum >= kVal) {
                return i - 10000;
            }
        }

        return -1;
    }
}
```
- Runtime: 128 ms (Beats: 6.19%)
- Memory: 47.02 MB (Beats: 34.95%)

<br>
