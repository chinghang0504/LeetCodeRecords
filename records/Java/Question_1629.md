# [LeetCode Records](../../README.md) - Question 1629 Slowest Key

### Attempt 1: Use an int[] to save all the pressed time
```java
class Solution {
    public char slowestKey(int[] releaseTimes, String keysPressed) {
        char[] arr = keysPressed.toCharArray();
        int[] pressedTime = new int[26];
        
        pressedTime[arr[0] - 'a'] = releaseTimes[0];

        for (int i = 1; i < releaseTimes.length; i++) {
            pressedTime[arr[i] - 'a'] = Math.max(pressedTime[arr[i] - 'a'], releaseTimes[i] - releaseTimes[i - 1]);
        }

        int max = pressedTime[0];
        int maxChIndex = 0;
        for (int i = 1; i < 26; i++) {
            if (pressedTime[i] > max) {
                max = pressedTime[i];
                maxChIndex = i;
            } else if (pressedTime[i] == max) {
                maxChIndex = i;
            }
        }

        return (char)(maxChIndex + 'a');
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.68 MB (Beats: 11.97%)

<br>
