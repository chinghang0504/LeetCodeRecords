# [LeetCode Records](../../README.md) - Question 811 Subdomain Visit Count

### Attempt 1: Use a HashMap to store the subdomains
```java
class Solution {
    public List<String> subdomainVisits(String[] cpdomains) {
        Map<String, Integer> map = new HashMap<>();
        for (String str : cpdomains) {
            String[] words = str.split("[\s.]");
            int count = Integer.valueOf(words[0]);

            String currDomain = words[words.length - 1];
            map.merge(currDomain, count, Integer::sum);
            for (int i = words.length - 2; i >= 1; i--) {
                currDomain = words[i] + "." + currDomain;
                map.merge(currDomain, count, Integer::sum);
            }
        }

        List<String> ans = new ArrayList<>();
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            ans.add(entry.getValue() + " " + entry.getKey());
        }

        return ans;
    }
}
```
- Runtime: 22 ms (Beats: 24.54%)
- Memory: 45.41 MB (Beats: 47.80%)

<br>
