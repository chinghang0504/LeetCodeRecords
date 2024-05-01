# [LeetCode Records](../../README.md) - Question 205 Isomorphic Strings

### Attempt 1: Use two HashMap
```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        int size1 = s.length();
        int size2 = t.length();
        if (size1 != size2) {
            return false;
        }

        HashMap<Character, Character> hashMap1 = new HashMap<>();
        HashMap<Character, Character> hashMap2 = new HashMap<>();

        for (int i = 0; i < size1; i++) {
            char ch1 = s.charAt(i);
            char ch2 = t.charAt(i);
            Character value1 = hashMap1.get(ch1);

            if (value1 == null) {
                if (hashMap2.get(ch2) != null) {
                    return false;
                }
                hashMap1.put(ch1, ch2);
                hashMap2.put(ch2, ch1);
            } else {
                if (value1 != ch2) {
                    return false;
                } else if (hashMap2.get(ch2) != ch1) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 11 ms (Beats: 53.86%)
- Memory: 42.49 MB (Beats: 33.46%)

<br>

### Attempt 2: Use two
```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        int size1 = s.length();
        int size2 = t.length();
        if (size1 != size2) {
            return false;
        }

        char[] saved1 = new char[128];
        char[] saved2 = new char[128];
        for (int i = 0; i < size1; i++) {
            char ch1 = s.charAt(i);
            char ch2 = t.charAt(i);
            char value1 = saved1[ch1];

            if (value1 == 0) {
                if (saved2[ch2] != 0) {
                    return false;
                }
                saved1[ch1] = ch2;
                saved2[ch2] = ch1;
            } else {
                if (value1 != ch2) {
                    return false;
                } else if (saved2[ch2] != ch1) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 4 ms (Beats: 97.26%)
- Memory: 42.66 MB (Beats: 17.06%)

<br>

### Attempt 3: Convert a String to a char array
```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
        int size = s.length();

        char[] saved1 = new char[128];
        char[] saved2 = new char[128];
        char[] arr1 = s.toCharArray();
        char[] arr2 = t.toCharArray();
        for (int i = 0; i < size; i++) {
            char ch1 = arr1[i];
            char ch2 = arr2[i];
            char value1 = saved1[ch1];
            char value2 = saved2[ch2];

            if (value1 == 0 && value2 == 0) {
                saved1[ch1] = ch2;
                saved2[ch2] = ch1;
            } else if (value1 != ch2 || value2 != ch1) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 98.67%)
- Memory: 42.51 MB (Beats: 23.54%)

<br>
