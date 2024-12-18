# [LeetCode Records](../../README.md) - Question 3119 Maximum Number of Potholes That Can Be Fixed

### Attempt 1: Use an ArrayList to store the number of potholes in each section
```java
class Solution {
    public int maxPotholes(String road, int budget) {
        char[] arr = road.toCharArray();
        List<Integer> list = new ArrayList<>();

        boolean isPrevPothole = false;
        int currLen = 0;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == 'x') {
                isPrevPothole = true;
                currLen++;
            } else if (isPrevPothole && currLen > 0) {
                list.add(currLen);
                currLen = 0;
            }
        }
        if (currLen > 0) {
            list.add(currLen);
        }

        list.sort((num1, num2) -> num2 - num1);
        
        int count = 0;
        for (int num : list) {
            int newBudget = budget - num - 1;
            if (newBudget >= 0) {
                budget = newBudget;
                count += num;
            } else {
                if (budget > 1) {
                    count += budget - 1;
                }
                break;
            }
        }

        return count;
    }
}
```
- Runtime: 77 ms (Beats: 91.90%)
- Memory: 46.09 MB (Beats: 14.58%)

<br>
