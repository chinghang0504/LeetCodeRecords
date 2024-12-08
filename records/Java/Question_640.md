# [LeetCode Records](../../README.md) - Question 640 Solve the Equation

### Attempt 1: Calculate the coefficient of x and the constant on both side
```java
class Solution {
    public String solveEquation(String equation) {
        int[][] values = new int[2][2];
        String[] splits = equation.split("=");

        for (int i = 0; i < 2; i++) {
            char[] arr = splits[i].toCharArray();
            boolean isPositive = true;
            int value = -1;
            boolean isX = false;

            for (int j = 0; j < arr.length; j++) {
                if (arr[j] == '+') {
                    updateValues(values[i], isPositive, isX, value);

                    isPositive = true;
                    value = -1;
                    isX = false;
                } else if (arr[j] == '-') {
                    updateValues(values[i], isPositive, isX, value);

                    isPositive = false;
                    value = -1;
                    isX = false;
                } else if (arr[j] == 'x') {
                    isX = true;
                } else {
                    if (value == -1) {
                        value = arr[j] - '0';
                    } else {
                        value = value * 10 + arr[j] - '0';
                    }
                }
            }

            updateValues(values[i], isPositive, isX, value);
        }

        int coefficient = values[0][0] - values[1][0];
        int constant = values[1][1] - values[0][1];

        if (coefficient == 0) {
            return constant == 0 ? "Infinite solutions" : "No solution";
        } else {
            return "x=" + (constant / coefficient);
        }
    }

    private void updateValues(int[] values, boolean isPositive, boolean isX, int value) {
        if (value == -1) {
            if (!isX) {
                return;
            } else {
                value = 1;
            }
        }

        if (!isPositive) {
            value *= -1;
        }

        values[isX ? 0 : 1] += value;
    }
}
```
- Runtime: 2 ms (Beats: 87.30%)
- Memory: 41.25 MB (Beats: 88.68%)

<br>
