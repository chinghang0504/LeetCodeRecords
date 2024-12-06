# [LeetCode Records](../../README.md) - Question 468 Validate IP Address

### Attempt 1: Use two functions to check IPv4 and IPv6 addresses separately
```java
class Solution {
    public String validIPAddress(String queryIP) {
        if (queryIP.contains(".")) {
            if (isValidIPv4(queryIP)) {
                return "IPv4";
            }
        } else {
            if (isValidIPv6(queryIP)) {
                return "IPv6";
            }
        }

        return "Neither";
    }

    private boolean isValidIPv4(String queryIP) {
        String[] splits = queryIP.split("[.]");
        if (splits.length != 4) {
            return false;
        } else if (queryIP.charAt(queryIP.length() - 1) == '.') {
            return false;
        }

        for (int i = 0; i < 4; i++) {
            char[] section = splits[i].toCharArray();
            if (section.length < 1 || section.length > 3) {
                return false;
            }

            int value = 0;
            for (char ch : section) {
                if (!Character.isDigit(ch)) {
                    return false;
                }

                value = value * 10 + ch - '0';
            }

            if (value > 255) {
                return false;
            } else if (value >= 100) {
                if (section.length != 3) {
                    return false;
                }
            } else if (value >= 10) {
                if (section.length != 2) {
                    return false;
                }
            } else {
                if (section.length != 1) {
                    return false;
                }
            }
        }

        return true;
    }

    private boolean isValidIPv6(String queryIP) {
        String[] splits = queryIP.split(":");
        if (splits.length != 8) {
            return false;
        } else if (queryIP.charAt(queryIP.length() - 1) == ':') {
            return false;
        }

        for (int i = 0; i < 8; i++) {
            char[] section = splits[i].toCharArray();
            if (section.length < 1 || section.length > 4) {
                return false;
            }

            for (char ch : section) {
                if (!(ch >= '0' && ch <= '9' || ch >= 'a' && ch <= 'f' || ch >= 'A' && ch <= 'F')) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 92.84%)
- Memory: 41.45 MB (Beats: 72.60%)

<br>
