# [LeetCode Records](../../README.md) - Question 2191 Sort the Jumbled Numbers

### Attempt 1: Use Arrays.sort() to get the new mapping digits and calculate the value of each number using the new mappinng digits
```java
class Solution {
    public int[] sortJumbled(int[] mapping, int[] nums) {
        int[][] values = new int[10][2];
        for (int i = 0; i < 10; i++) {
            values[i][0] = i;
            values[i][1] = mapping[i];
        }
        Arrays.sort(values, (value1, value2) -> value1[1] - value2[1]);

        int[] digits = new int[10];
        for (int i = 0; i < 10; i++) {
            digits[values[i][0]] = i;
        }

        int[][] numValues = new int[nums.length][2];
        for (int i = 0; i < nums.length; i++) {
            numValues[i][0] = nums[i];
            numValues[i][1] = getNumValue(digits, nums[i]);
        }
        Arrays.sort(numValues, (numValue1, numValue2) -> numValue1[1] - numValue2[1]);

        for (int i = 0; i < nums.length; i++) {
            nums[i] = numValues[i][0];
        }

        return nums;
    }

    private int getNumValue(int[] digits, int num) {
        List<Integer> list = new ArrayList<>();

        if (num == 0) {
            list.add(0);
        } else {
            while (num > 0) {
                list.addFirst(num % 10);
                num /= 10;
            }
        }
        
        int value = 0;
        for (int digit : list) {
            value = value * 10 + digits[digit];
        }

        return value;
    }
}
```
- Runtime: 127 ms (Beats: 57.69%)
- Memory: 55.30 MB (Beats: 90.81%)

<br>
