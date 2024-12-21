# [LeetCode Records](../../README.md) - Question 2671 Frequency Tracker

### Attempt 1: Use two HashMap to store the numbers and frequencies
```java
class FrequencyTracker {

    private Map<Integer, Integer> numberToFrequencyMap;
    private Map<Integer, Integer> frequencyToCountMap;

    public FrequencyTracker() {
        numberToFrequencyMap = new HashMap<>();
        frequencyToCountMap = new HashMap<>();
    }
    
    public void add(int number) {
        Integer frequency = numberToFrequencyMap.get(number);
        numberToFrequencyMap.merge(number, 1, Integer::sum);
        if (frequency == null) {
            frequencyToCountMap.merge(1, 1, Integer::sum);
        } else {
            frequencyToCountMap.merge(frequency, -1, Integer::sum);
            frequencyToCountMap.merge(frequency + 1, 1, Integer::sum);
        }
    }
    
    public void deleteOne(int number) {
        Integer frequency = numberToFrequencyMap.get(number);
        if (frequency == null || frequency == 0) {
            return;
        } else {
            numberToFrequencyMap.merge(number, -1, Integer::sum);
            frequencyToCountMap.merge(frequency, -1, Integer::sum);
            frequencyToCountMap.merge(frequency - 1, 1, Integer::sum);
        }
    }
    
    public boolean hasFrequency(int frequency) {
        Integer count = frequencyToCountMap.get(frequency);
        return count != null && count > 0;
    }
}

/**
 * Your FrequencyTracker object will be instantiated and called as such:
 * FrequencyTracker obj = new FrequencyTracker();
 * obj.add(number);
 * obj.deleteOne(number);
 * boolean param_3 = obj.hasFrequency(frequency);
 */
```
- Runtime: 39 ms (Beats: 77.14%)
- Memory: 113.90 MB (Beats: 42.14%)

<br>
