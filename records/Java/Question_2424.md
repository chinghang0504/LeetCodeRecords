# [LeetCode Records](../../README.md) - Question 2424 Longest Uploaded Prefix

### Attempt 1: Use a PriorityQueue to store the nonconsecutive numbers
```java
class LUPrefix {

    private PriorityQueue<Integer> priorityQueue;
    private int currTarget;
    private int count;

    public LUPrefix(int n) {
        priorityQueue = new PriorityQueue<>();
        currTarget = 1;
        count = 0;
    }
    
    public void upload(int video) {
        if (video == currTarget) {
            count++;
            currTarget++;
        } else {
            priorityQueue.add(video);
        }

        while (!priorityQueue.isEmpty() && priorityQueue.peek() == currTarget) {
            priorityQueue.poll();
            count++;
            currTarget++;
        }
    }
    
    public int longest() {
        return count;
    }
}

/**
 * Your LUPrefix object will be instantiated and called as such:
 * LUPrefix obj = new LUPrefix(n);
 * obj.upload(video);
 * int param_2 = obj.longest();
 */
```
- Runtime: 67 ms (Beats: 32.04%)
- Memory: 109.26 MB (Beats: 98.06%)

<br>

### Attempt 2: Use a boolean[] to store the checked numbers
```java
class LUPrefix {

    private boolean[] checked;
    private int count;

    public LUPrefix(int n) {
        checked = new boolean[n];
        count = 0;
    }
    
    public void upload(int video) {
        checked[video - 1] = true;
        for (int i = count; i < checked.length; i++) {
            if (checked[i]) {
                count++;
            } else {
                break;
            }
        }
    }
    
    public int longest() {
        return count;
    }
}

/**
 * Your LUPrefix object will be instantiated and called as such:
 * LUPrefix obj = new LUPrefix(n);
 * obj.upload(video);
 * int param_2 = obj.longest();
 */
```
- Runtime: 30 ms (Beats: 90.29%)
- Memory: 110.47 MB (Beats: 24.27%)

<br>
