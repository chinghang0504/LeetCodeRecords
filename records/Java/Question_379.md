# [LeetCode Records](../../README.md) - Question 379 Design Phone Directory

### Attempt 1: Use a boolean array
```java
class PhoneDirectory {

    private final boolean[] occupied;

    public PhoneDirectory(int maxNumbers) {
        occupied = new boolean[maxNumbers];
    }

    public int get() {
        for (int i = 0; i < occupied.length; i++) {
            if (!occupied[i]) {
                occupied[i] = true;
                return i;
            }
        }
        
        return -1;
    }

    public boolean check(int number) {
        return !occupied[number];
    }

    public void release(int number) {
        occupied[number] = false;
    }
}
```
- Runtime: 10 ms (Beats: 54.59%)
- Memory: 46.33 MB (Beats: 82.61%)

<br>
