# [LeetCode Records](../../README.md) - Question 605 Can Place Flowers

### Attempt 1: Check from the left to the right
```java
class Solution {
    public boolean canPlaceFlowers(int[] flowerbed, int n) {
        if (n == 0) {
            return true;
        } else if (flowerbed.length == 1) {
            return flowerbed[0] == 0;
        }

        if (flowerbed[0] == 0 && flowerbed[1] == 0) {
            flowerbed[0] = 1;
            n--;

            if (n == 0) {
                return true;
            }
        }

        if (flowerbed[flowerbed.length - 2] == 0 && flowerbed[flowerbed.length - 1] == 0) {
            flowerbed[flowerbed.length - 1] = 1;
            n--;

            if (n == 0) {
                return true;
            }
        }

        int i = 1;
        while (i < flowerbed.length - 1) {
            if (flowerbed[i - 1] == 0 && flowerbed[i] == 0 && flowerbed[i + 1] == 0) {
                flowerbed[i] = 1;
                i += 2;
                n--;

                if (n == 0) {
                    return true;
                }
            } else {
                i++;
            }
        }

        return false;
    }
}
```
- Runtime: 1 ms (Beats: 97.57%)
- Memory: 45.65 MB (Beats: 24.92%)

<br>
