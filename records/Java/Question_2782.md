# [LeetCode Records](../../README.md) - Question 2782 Number of Unique Categories

### Attempt 1: Use an ArrayList to store the unique items
```java
/**
 * Definition for a category handler.
 * class CategoryHandler {
 *     public CategoryHandler(int[] categories);
 *     public boolean haveSameCategory(int a, int b);
 * };
 */
class Solution {
	public int numberOfCategories(int n, CategoryHandler categoryHandler) {
    	List<Integer> list = new ArrayList<>();

        for (int i = 0; i < n; i++) {
            boolean isUnique = true;

            for (int item : list) {
                if (categoryHandler.haveSameCategory(i, item)) {
                    isUnique = false;
                    break;
                }
            }

            if (isUnique) {
                list.add(i);
            }
        }

        return list.size();
	}
}
```
- Runtime: 57 ms (Beats: 18.60%)
- Memory: 44.54 MB (Beats: 95.35%)

<br>
