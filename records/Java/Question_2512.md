# [LeetCode Records](../../README.md) - Question 2512 Reward Top K Students

### Attempt 1: Use two HashSet to store the positive and negative words and a HashMap to store the student points
```java
class Solution {
    public List<Integer> topStudents(String[] positive_feedback, String[] negative_feedback, String[] report, int[] student_id, int k) {
        Set<String> positiveSet = new HashSet<>();
        Set<String> negativeSet = new HashSet<>();
        for (String positive : positive_feedback) {
            positiveSet.add(positive);
        }
        for (String negative : negative_feedback) {
            negativeSet.add(negative);
        }

        Map<Integer, Integer> studentMap = new HashMap<>();
        for (int i = 0; i < report.length; i++) {
            int point = getPoints(positiveSet, negativeSet, report[i]);
            studentMap.merge(student_id[i], point, Integer::sum);
        }

        List<Map.Entry<Integer, Integer>> list = new ArrayList<>(studentMap.entrySet());
        list.sort((e1, e2) -> {
            int val1 = e1.getValue();
            int val2 = e2.getValue();
            if (val1 != val2) {
                return val2 - val1;
            } else {
                return e1.getKey() - e2.getKey();
            }
        });

        List<Integer> ans = new ArrayList<>();
        int i = 0;
        for (Map.Entry<Integer, Integer> entry : list) {
            ans.add(entry.getKey());
            i++;

            if (i == k) {
                break;
            }
        }

        return ans;
    }

    private int getPoints(Set<String> positiveSet, Set<String> negativeSet, String feedback) {
        int point = 0;
        String[] splits = feedback.split("\s");

        for (String split : splits) {
            if (positiveSet.contains(split)) {
                point += 3;
            } else if (negativeSet.contains(split)) {
                point--;
            }
        }

        return point;
    }
}
```
- Runtime: 81 ms (Beats: 33.13%)
- Memory: 55.66 MB (Beats: 39.16%)

<br>
