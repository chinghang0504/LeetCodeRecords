# [LeetCode Records](../../README.md) - Question 384 Shuffle an Array

### Attempt 1: Store the numbers in the LinkedList and randomly remove the numbers from the list
```java
class Solution {

    private int[] arr;
    private Random random;

    public Solution(int[] nums) {
        arr = nums;
        random = new Random();
    }
    
    public int[] reset() {
        return arr;
    }
    
    public int[] shuffle() {
        List<Integer> list = new LinkedList<>();
        for (int num : arr) {
            list.add(num);
        }

        int[] ans = new int[arr.length];
        for (int i = 0; i < arr.length; i++) {
            int target = random.nextInt(list.size());
            ans[i] = list.remove(target);
        }

        return ans;
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * int[] param_1 = obj.reset();
 * int[] param_2 = obj.shuffle();
 */
```
- Runtime: 50 ms (Beats: 90.08%)
- Memory: 50.40 MB (Beats: 52.32%)

<br>
