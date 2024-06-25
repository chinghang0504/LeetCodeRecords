# [LeetCode Records](../../README.md) - Question 1108 Defanging an IP Address

### Attempt 1: Use replaceAll
```java
class Solution {
    public String defangIPaddr(String address) {
        return address.replaceAll("[.]", "[.]");
    }
}
```
- Runtime: 1 ms (Beats: 28.14%)
- Memory: 41.49 MB (Beats: 33.25%)

<br>

### Attempt 2: Use StringBuilder
```java
class Solution {
    public String defangIPaddr(String address) {
        StringBuilder stringBuilder = new StringBuilder();

        for (char ch : address.toCharArray()) {
            if (ch != '.') {
                stringBuilder.append(ch);
            } else {
                stringBuilder.append("[.]");
            }
        }
        
        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.54 MB (Beats: 22.48%)

<br>
