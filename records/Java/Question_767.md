# [LeetCode Records](../../README.md) - Question 767 Reorganize String

### Attempt 1: Use a PriorityQueue to store the character and its count
```java
class Solution {

    class Item {

        char ch;
        int count;

        Item(char ch, int count) {
            this.ch = ch;
            this.count = count;
        }

        int compareTo(Item item) {
            return item.count - this.count;
        }

        boolean decrease() {
            this.count--;
            return this.count > 0;
        }
    }

    public String reorganizeString(String s) {
        int[] counts = new int[26];
        for (char ch : s.toCharArray()) {
            counts[ch - 'a']++;
        }

        PriorityQueue<Item> priorityQueue = new PriorityQueue<>((item1, item2) -> item1.compareTo(item2));
        for (int i = 0; i < 26; i++) {
            if (counts[i] > 0) {
                priorityQueue.add(new Item((char)(i + 'a'), counts[i]));
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        char prevCh = ' ';
        while (!priorityQueue.isEmpty()) {
            Item firstItem = priorityQueue.poll();
            if (prevCh != firstItem.ch) {
                stringBuilder.append(firstItem.ch);
                if (firstItem.decrease()) {
                    priorityQueue.add(firstItem);
                }
                prevCh = firstItem.ch;
            } else if (priorityQueue.isEmpty()) {
                return "";
            } else {
                Item secondItem = priorityQueue.poll();
                stringBuilder.append(secondItem.ch);
                if (secondItem.decrease()) {
                    priorityQueue.add(secondItem);
                }
                stringBuilder.append(firstItem.ch);
                if (firstItem.decrease()) {
                    priorityQueue.add(firstItem);
                }
                prevCh = firstItem.ch;
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 3 ms (Beats: 72.05%)
- Memory: 41.31 MB (Beats: 93.06%)

<br>
