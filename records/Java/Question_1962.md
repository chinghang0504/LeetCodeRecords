# [LeetCode Records](../../README.md) - Question 1962 Remove Stones to Minimize the Total

### Attempt 1: Store all the piles in the PriorityQueue
```java
class Solution {
    public int minStoneSum(int[] piles, int k) {
        int sum = 0;
        for (int pile : piles) {
            sum += pile;
        }

        PriorityQueue<Integer> priorityQueue = new PriorityQueue<>(Collections.reverseOrder());
        for (int pile : piles) {
            priorityQueue.add(pile);
        }
        
        for (int i = 0; i < k; i++) {
            int max = priorityQueue.poll();
            int reduced = max / 2;
            sum -= reduced;
            priorityQueue.add(max - reduced);
        }

        return sum;
    }
}
```
- Runtime: 414 ms (Beats: 74.37%)
- Memory: 59.25 MB (Beats: 48.50%)

<br>

### Attempt 2: Only store top k piles in the PriorityQueue
```java
class Solution {
    public int minStoneSum(int[] piles, int k) {
        int sum = 0;
        for (int pile : piles) {
            sum += pile;
        }

        Arrays.sort(piles);
        int size = Math.min(piles.length, k);
        PriorityQueue<Integer> priorityQueue = new PriorityQueue<>(size, Collections.reverseOrder());
        for (int i = 0; i < size; i++) {
            priorityQueue.add(piles[piles.length - i - 1]);
        }
        
        for (int i = 0; i < k; i++) {
            int max = priorityQueue.poll();
            int reduced = max / 2;
            sum -= reduced;
            priorityQueue.add(max - reduced);
        }

        return sum;
    }
}
```
- Runtime: 359 ms (Beats: 80.24%)
- Memory: 57.05 MB (Beats: 95.33%)

<br>
