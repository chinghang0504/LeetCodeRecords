# [LeetCode Records](../../README.md) - Question 346 Moving Average from Data Stream

### Attempt 1: Loop for adding all numbers
```java
class MovingAverage {

    private int[] arr;
    private int currIndex = 0;
    private int currSize = 0;

    public MovingAverage(int size) {
        arr = new int[size];
    }

    public double next(int val) {
        if (currSize != arr.length) {
            currSize++;
            arr[currIndex++] = val;
        } else {
            arr[currIndex++ % arr.length] = val;
        }

        double average = 0.0;
        for (int i = 0; i < currSize; i++) {
            average += arr[i];
        }
        return average / currSize;
    }
}
```
- Runtime: 49 ms (Beats: 15.74%)
- Memory: 49.07 MB (Beats: 83.13%)

<br>

### Attempt 2: Save the current sum
```java
class MovingAverage {
    private final int[] arr;
    private int currIndex;
    private int currSize;
    private int currSum;

    public MovingAverage(int size) {
        arr = new int[size];
        currIndex = 0;
        currSize = 0;
        currSum = 0;
    }

    public double next(int val) {
        int index = currIndex % arr.length;

        if (currSize != arr.length) {
            currSize++;
        } else {
            currSum -= arr[index];
        }

        arr[index] = val;
        currIndex++;
        currSum += val;
        return (double) currSum / currSize;
    }
}
```
- Runtime: 39 ms (Beats: 95.47%)
- Memory: 48.95 MB (Beats: 90.58%)

<br>
