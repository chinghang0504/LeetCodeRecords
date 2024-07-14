# [LeetCode Records](../../README.md) - Question 2610 Convert an Array Into a 2D Array With Conditions

### Attempt 1: Save the count of each number
```java
class Solution {
    public List<List<Integer>> findMatrix(int[] nums) {
        List<List<Integer>> answer = new ArrayList<>();
        int[] counts = new int[201];
        int listSize = 0;

        for (int num : nums) {
            int index = counts[num];

            if (index >= listSize) {
                answer.add(new ArrayList<>());
                listSize++;
            }
            counts[num]++;

            answer.get(index).add(num);
        }
        
        return answer;
    }
}
```
- Runtime: 2 ms (Beats: 90.15%)
- Memory: 44.60 MB (Beats: 77.14%)

<br>
