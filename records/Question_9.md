# [LeetCode Records](../README.md) - Question 9 Palindrome Number

### Attempt 1: Use ArrayList
```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0) {
            return false;
        }

        ArrayList<Integer> list = new ArrayList<Integer>();
        while (x > 0) {
            list.add(x % 10);
            x /= 10;
        }

        while (list.size() > 1) {
            int val1 = list.removeFirst();
            int val2 = list.removeLast();

            if (val1 != val2) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 7 ms (Beats: 18.94%)
- Memory: 43.85 MB (Beats: 62.97%)

<br>

### Attempt 2: Use ArrayList without remove()
```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0) {
            return false;
        }

        ArrayList<Integer> list = new ArrayList<Integer>();
        while (x > 0) {
            list.add(x % 10);
            x /= 10;
        }

        int size = list.size();
        for (int i = 0; i < size / 2; i++) {
            if (list.get(i) != list.get(size - i - 1)) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 6 ms (Beats: 37.08%)
- Memory: 44.11 MB (Beats: 28.72%)

<br>

### Attempt 3: Use String.valueOf()
```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0) {
            return false;
        }

        String s = String.valueOf(x);
        int size = s.length();
        for (int i = 0; i < size / 2; i++) {
            if (s.charAt(i) != s.charAt(size - i - 1)) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 6 ms (Beats: 37.08%)
- Memory: 44.22 MB (Beats: 20.24%)

<br>

### Attempt 4: Check the Palindrome Integer value
```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0) {
            return false;
        }

        int orgValue = x;
        int value = 0;
        while (x > 0) {
            value = value * 10 + x % 10;
            x /= 10;
        }

        return orgValue == value;
    }
}
```
- Runtime: 4 ms (Beats: 100.00%)
- Memory: 43.71 MB (Beats: 75.55%)

<br>
