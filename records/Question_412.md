# [LeetCode Records](../README.md) - Question 412 Fizz Buzz

### Attempt 1: Use an ArrayList
```java
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> result = new ArrayList<>(n);
        fizzBuzzRecursion(n, result);
        return result;
    }

    private void fizzBuzzRecursion(int n, List<String> result) {
        if (n == 0) {
            return;
        }

        boolean divisible_3 = n % 3 == 0;
        boolean divisible_5 = n % 5 == 0;

        if (divisible_3 && divisible_5) {
            result.addFirst("FizzBuzz");
        } else if (divisible_3) {
            result.addFirst("Fizz");
        } else if (divisible_5) {
            result.addFirst("Buzz");
        } else {
            result.addFirst(String.valueOf(n));
        }

        fizzBuzzRecursion(n - 1, result);
    }
}
```
- Runtime: 5 ms (Beats: 7.88%)
- Memory: 45.08 MB (Beats: 40.81%)

<br>

### Attempt 2: Use a LinkedList
```java
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> result = new LinkedList<>();
        
        while (n > 0) {
            boolean divisible_3 = n % 3 == 0;
            boolean divisible_5 = n % 5 == 0;

            if (divisible_3 && divisible_5) {
                result.addFirst("FizzBuzz");
            } else if (divisible_3) {
                result.addFirst("Fizz");
            } else if (divisible_5) {
                result.addFirst("Buzz");
            } else {
                result.addFirst(String.valueOf(n));
            }

            n--;
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 99.39%)
- Memory: 45.17 MB (Beats: 26.89%)

<br>
