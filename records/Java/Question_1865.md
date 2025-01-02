# [LeetCode Records](../../README.md) - Question 1865 Finding Pairs With a Certain Sum

### Attempt 1: Use two HashMap to store the numbers in the arrays
```java
class FindSumPairs {

    private Map<Integer, Integer> map1;
    private Map<Integer, Integer> map2;
    private int[] nums2;

    public FindSumPairs(int[] nums1, int[] nums2) {
        map1 = new HashMap<>();
        for (int i = 0; i < nums1.length; i++) {
            map1.merge(nums1[i], 1, Integer::sum);
        }

        map2 = new HashMap<>();
        for (int i = 0; i < nums2.length; i++) {
            map2.merge(nums2[i], 1, Integer::sum);
        }

        this.nums2 = nums2;
    }
    
    public void add(int index, int val) {
        map2.merge(nums2[index], -1, Integer::sum);

        nums2[index] += val;
        map2.merge(nums2[index], 1, Integer::sum);
    }
    
    public int count(int tot) {
        int pairCount = 0;

        for (Map.Entry<Integer, Integer> entry : map1.entrySet()) {
            int num1 = entry.getKey();
            int num2 = tot - entry.getKey();

            Integer count2 = map2.get(tot - entry.getKey());
            if (count2 != null) {
                pairCount += entry.getValue() * count2;
            }
        }

        return pairCount;
    }
}

/**
 * Your FindSumPairs object will be instantiated and called as such:
 * FindSumPairs obj = new FindSumPairs(nums1, nums2);
 * obj.add(index,val);
 * int param_2 = obj.count(tot);
 */
```
- Runtime: 166 ms (Beats: 20.00%)
- Memory: 78.97 MB (Beats: 20.00%)

<br>
