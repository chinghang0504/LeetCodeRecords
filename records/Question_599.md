# [LeetCode Records](../README.md) - Question 599 Minimum Index Sum of Two Lists

### Attempt 1: Use a HashMap to store the strings in list2
```java
class Solution {
    public String[] findRestaurant(String[] list1, String[] list2) {
        Map<String, Integer> map = new HashMap<>();
        for (int i = 0; i < list2.length; i++) {
            map.put(list2[i], i);
        }

        String[] saved = new String[list1.length];
        int count = 0;
        int minIndexSum = Integer.MAX_VALUE;

        for (int i = 0; i < list1.length; i++) {
            String str = list1[i];
            Integer index = map.get(str);
            
            if (index != null) {
                int indexSum = i + index;
                if (indexSum <= minIndexSum) {
                    if (indexSum < minIndexSum) {
                        minIndexSum = indexSum;
                        count = 0;
                    }
                    saved[count++] = str;
                }
            }
        }

        return Arrays.copyOf(saved, count);
    }
}
```
- Runtime: 7 ms (Beats: 87.30%)
- Memory: 45.95 MB (Beats: 6.52%)

<br>
