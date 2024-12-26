# [LeetCode Records](../../README.md) - Question 91 Decode Ways

### Attempt 1: Use a HashMap to store the previous calculated count
```java
class Solution {

    private Map<String, Integer> map = new HashMap<>();

    public int numDecodings(String s) {
        Integer prevCount = map.get(s);
        if (prevCount != null) {
            return prevCount;
        }

        if (s.length() <= 2) {
            int count = getCount(s);
            map.put(s, count);
            return count;
        }

        int count = 0;
        if (isValid(s.substring(0, 1))) {
            String str1 = s.substring(1);
            Integer count1 = map.get(str1);
            if (count1 == null) {
                count1 = numDecodings(str1);
                map.put(str1, count1);
            }
            count += count1;
        }
        if (isValid(s.substring(0, 2))) {
            String str2 = s.substring(2);
            Integer count2 = map.get(str2);
            if (count2 == null) {
                count2 = numDecodings(str2);
                map.put(str2, count2);
            }
            count += count2;
        }

        map.put(s, count);
        return count;
    }

    private boolean isValid(String s) {
        int len = s.length();
        char ch1 = s.charAt(0);
        if (len == 1) {
            return ch1 != '0';
        } else {
            if (ch1 == '0') {
                return false;
            } else if (ch1 == '1') {
                return true;
            } else if (ch1 == '2') {
                char ch2 = s.charAt(1);
                return ch2 <= '6';
            } else {
                return false;
            }
        }
    }

    private int getCount(String s) {
        int len = s.length();
        char ch1 = s.charAt(0);
        if (len == 1) {
            return ch1 == '0' ? 0 : 1;
        } else {
            if (ch1 == '0') {
                return 0;
            } 
            
            char ch2 = s.charAt(1);
            if (ch1 == '1') {
                return ch2 == '0' ? 1 : 2;
            } else if (ch1 == '2') {
                return ch2 == '0' || ch2 >= '7' ? 1 : 2;
            } else {
                return ch2 == '0' ? 0 : 1;
            }
        }
    }
}
```
- Runtime: 2 ms (Beats: 19.56%)
- Memory: 42.48 MB (Beats: 7.24%)

<br>
