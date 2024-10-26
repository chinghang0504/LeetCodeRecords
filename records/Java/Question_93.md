# [LeetCode Records](../../README.md) - Question 93 

### Attempt 1: Use recursion that passes the current index of a string, the current IP address, and the current section
```java
class Solution {

    private String str;
    private int len;
    private List<String> ans;

    public List<String> restoreIpAddresses(String s) {
        str = s;
        len = str.length();
        ans = new ArrayList<>();

        getIpAddresses(0, "", 0);

        return ans;
    }

    private void getIpAddresses(int currIndex, String ipAddress, int currSection) {
        if (currIndex == len && currSection == 4) {
            ans.add(ipAddress);
            return;
        } else if (currIndex >= len || currSection >= 4) {
            return;
        }

        for (int i = 1; i <= 3; i++) {
            int endIndex = currIndex + i;
            if (endIndex > len) {
                return;
            }

            String section = str.substring(currIndex, endIndex);
            int address = Integer.valueOf(section);
            if (address >= 0 && address <= 9) {
                if (section.length() != 1) {
                    return;
                }
            } else if (address >= 10 && address <= 99) {
                if (section.length() != 2) {
                    return;
                }
            }

            if (address >= 0 && address < 256) {
                String nextIpAddress = currSection == 0 ? section : ipAddress + "." + section;
                getIpAddresses(endIndex, nextIpAddress, currSection + 1);
            }
        }
    }
}
```
- Runtime: 4 ms (Beats: 50.17%)
- Memory: 42.50 MB (Beats: 57.23%)

<br>
