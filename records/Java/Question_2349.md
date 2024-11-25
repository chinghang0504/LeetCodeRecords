# [LeetCode Records](../../README.md) - Question 2349 Design a Number Container System

### Attempt 1: Use a HashMap to store the index and its number key-value pair and a HashMap with SortedSet to store the number and its sorted indices key-value pair
```java
class NumberContainers {

    private Map<Integer, Integer> indexToNumberMap;
    private Map<Integer, SortedSet<Integer>> numberToIndexMap;

    public NumberContainers() {
        indexToNumberMap = new HashMap<>();
        numberToIndexMap = new HashMap<>();
    }
    
    public void change(int index, int number) {
        Integer prevNumber = indexToNumberMap.get(index);
        if (prevNumber != null) {
            SortedSet<Integer> sortedSet = numberToIndexMap.get(prevNumber);
            sortedSet.remove(index);
        }
        indexToNumberMap.put(index, number);

        SortedSet<Integer> sortedSet = numberToIndexMap.get(number);
        if (sortedSet == null) {
            sortedSet = new TreeSet<>();
            numberToIndexMap.put(number, sortedSet);
        }
        sortedSet.add(index);
    }
    
    public int find(int number) {
        SortedSet<Integer> sortedSet = numberToIndexMap.get(number);
        if (sortedSet == null || sortedSet.isEmpty()) {
            return -1;
        } else {
            return sortedSet.first();
        }
    }
}

/**
 * Your NumberContainers object will be instantiated and called as such:
 * NumberContainers obj = new NumberContainers();
 * obj.change(index,number);
 * int param_2 = obj.find(number);
 */
```
- Runtime: 77 ms (Beats: 73.08%)
- Memory: 95.94 MB (Beats: 93.22%)

<br>
