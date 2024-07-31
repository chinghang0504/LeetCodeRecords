# [LeetCode Records](../../README.md) - Question 929 Unique Email Addresses

### Attempt 1: Use a HashSet to save the minimized emails
```java
class Solution {
    public int numUniqueEmails(String[] emails) {
        Set<String> set = new HashSet<>();

        for (String email : emails) {
            set.add(getMinimizedEmail(email));
        }

        return set.size();
    }

    private String getMinimizedEmail(String email) {
        StringBuilder stringBuilder = new StringBuilder();
        char[] arr = email.toCharArray();

        int i = 0;
        for (; arr[i] != '@'; i++) {
            if (arr[i] == '+') {
                while (arr[i] != '@') {
                    i++;
                }
                break;
            } else if (arr[i] == '.') {
                continue;
            } else {
                stringBuilder.append(arr[i]);
            }
        }
        stringBuilder.append(arr, i, arr.length - i);
        
        return stringBuilder.toString();
    }
}
```
- Runtime: 5 ms (Beats: 99.73%)
- Memory: 43.95 MB (Beats: 94.04%)

<br>
