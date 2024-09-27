# [LeetCode Records](../../README.md) - Question 950 Reveal Cards In Increasing Order

### Attempt 1: Use Arrays.sort() to sort the array and a LinkedList to store the remaining indices
```java
class Solution {
    public int[] deckRevealedIncreasing(int[] deck) {
        Arrays.sort(deck);

        List<Integer> list = new LinkedList<>();
        for (int i = 0; i < deck.length; i++) {
            list.add(i);
        }
        int[] ans = new int[deck.length];

        for (int i = 0; i < deck.length - 1; i++) {
            int index = list.removeFirst();
            ans[index] = deck[i];
            list.addLast(list.removeFirst());
        }
        int index = list.removeFirst();
        ans[index] = deck[deck.length - 1];

        return ans;
    }
}
```
- Runtime: 3 ms (Beats: 89.76%)
- Memory: 43.94 MB (Beats: 33.26%)

<br>
