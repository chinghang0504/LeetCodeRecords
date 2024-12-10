# [LeetCode Records](../../README.md) - Question 1452 People Whose List of Favorite Companies Is Not a Subset of Another List

### Attempt 1: Use a HashMap to convert the company name to a unique number
```java
class Solution {
    public List<Integer> peopleIndexes(List<List<String>> favoriteCompanies) {
        Map<String, Integer> map = new HashMap<>();
        List<Set<Integer>> list = new ArrayList<>();
        int nextVal = 0;
        for (List<String> companyList : favoriteCompanies) {
            Set<Integer> set = new HashSet<>();
            list.add(set);
            
            for (String name : companyList) {
                Integer index = map.get(name);
                if (index == null) {
                    index = nextVal;
                    nextVal++;
                    map.put(name, index);
                }
                set.add(index);
            }
        }

        List<Integer> ans = new ArrayList<>();
        for (int i = 0; i < list.size(); i++) {
            Set<Integer> targetSet = list.get(i);
            boolean isNotSubset = true;

            for (int j = 0; j < list.size(); j++) {
                if (i == j) {
                    continue;
                }

                Set<Integer> testSet = list.get(j);
                if (targetSet.size() > testSet.size()) {
                    continue;
                }

                if (isSubset(targetSet, testSet)) {
                    isNotSubset = false;
                    break;
                }
            }

            if (isNotSubset) {
                ans.add(i);
            }
        }
        

        return ans;
    }

    private boolean isSubset(Set<Integer> set1, Set<Integer> set2) {
        for (int item : set1) {
            if (!set2.contains(item)) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 271 ms (Beats: 66.47%)
- Memory: 56.43 MB (Beats: 79.43%)

<br>
