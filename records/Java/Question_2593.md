# [LeetCode Records](../../README.md) - Question 2593 Find Score of an Array After Marking All Elements

### Attempt 1: Use an ArrayList to store the item with the value and its index
```java
class Solution {

    class Item {

        int val;
        int index;

        Item(int val, int index) {
            this.val = val;
            this.index = index;
        }

        int compareTo(Item item) {
            if (this.val != item.val) {
                return this.val - item.val;
            } else {
                return this.index - item.index;
            }
        }
    }

    public long findScore(int[] nums) {
        List<Item> list = new ArrayList<>();
        for (int i = 0; i < nums.length; i++) {
            list.add(new Item(nums[i], i));
        }
        list.sort((item1, item2) -> item1.compareTo(item2));

        boolean[] checked = new boolean[nums.length + 2];
        int size = list.size();
        long score = 0;
        for (int i = 0; i < size; i++) {
            Item item = list.get(i);
            if (!checked[item.index + 1]) {
                checked[item.index] = true;
                checked[item.index + 1] = true;
                checked[item.index + 2] = true;
                
                score += item.val;
            }
        }

        return score;
    }
}
```
- Runtime: 95 ms (Beats: 88.83%)
- Memory: 61.60 MB (Beats: 17.88%)

<br>
