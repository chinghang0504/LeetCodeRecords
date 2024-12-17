# [LeetCode Records](../../README.md) - Question 2933 High-Access Employees

### Attempt 1: Use a HashMap to store the employee and its access times key-value pairs
```java
class Solution {
    public List<String> findHighAccessEmployees(List<List<String>> access_times) {
        Map<String, List<Integer>> employeeMap = new HashMap<>();
        for (List<String> accessTime : access_times) {
            String employee = accessTime.get(0);
            String timeStr = accessTime.get(1);
            
            List<Integer> list = employeeMap.get(employee);
            if (list == null) {
                list = new ArrayList<>();
                employeeMap.put(employee, list);
            }
            list.add(getTime(timeStr));
        }

        List<String> ans = new ArrayList<>();
        for (Map.Entry<String, List<Integer>> entry : employeeMap.entrySet()) {
            List<Integer> list = entry.getValue();
            int size = list.size();
            if (size < 3) {
                continue;
            }

            list.sort(null);

            for (int i = 0; i < size - 2; i++) {
                int time1 = list.get(i);
                int time2 = list.get(i + 2);
                if (time2 - time1 < 60) {
                    ans.add(entry.getKey());
                    break;
                }
            }
        }

        return ans;
    }

    private int getTime(String timeStr) {
        int digit1 = timeStr.charAt(0) - '0';
        int digit2 = timeStr.charAt(1) - '0';
        int digit3 = timeStr.charAt(2) - '0';
        int digit4 = timeStr.charAt(3) - '0';
        return (digit1 * 10 + digit2) * 60 + digit3 * 10 + digit4;
    }
}
```
- Runtime: 7 ms (Beats: 100.00%)
- Memory: 45.04 MB (Beats: 99.65%)

<br>
