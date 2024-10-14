# [LeetCode Records](../../README.md) - Question 1233 Remove Sub-Folders from the Filesystem

### Attempt 1: Check all the parent folders for each subfolder
```java
class Solution {
    public List<String> removeSubfolders(String[] folder) {
        Set<String> set = new HashSet<>();
        for (String name : folder) {
            set.add(name);
        }

        List<String> ans = new ArrayList<>();
        for (String name : folder) {
            int lastIndex = name.lastIndexOf('/');
            if (lastIndex == 0) {
                ans.add(name);
            } else {
                boolean noParent = true;
                String currName = name;

                while (lastIndex != 0) {
                    lastIndex = currName.lastIndexOf('/');
                    currName = currName.substring(0, lastIndex);
                    if (set.contains(currName)) {
                        noParent = false;
                        break;
                    }
                };
                
                if (noParent) {
                    ans.add(name);
                }
            }
        }

        return ans;
    }
}
```
- Runtime: 32 ms (Beats: 97.83%)
- Memory: 56.35 MB (Beats: 30.16%)

<br>
