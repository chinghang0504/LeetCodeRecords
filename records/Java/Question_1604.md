# [LeetCode Records](../../README.md) - Question 1604 Alert Using Same Key-Card Three or More Times in a One Hour Period

### Attempt 1: Use a HashMap to store the name and its list of times key-value pairs
```java
class Solution {

    class Time {
        int hour;
        int minute;

        Time(String timeStr) {
            char[] arr = timeStr.toCharArray();
            hour = (arr[0] - '0') * 10 + arr[1] - '0';
            minute = (arr[3] - '0') * 10 + arr[4] - '0';
        }

        int compareTo(Time time) {
            return (this.hour - time.hour) * 60 + this.minute - time.minute;
        }
    }

    public List<String> alertNames(String[] keyName, String[] keyTime) {
        Map<String, List<Time>> timeMap = new HashMap<>();
        for (int i = 0; i < keyName.length; i++) {
            List<Time> timeList = timeMap.get(keyName[i]);
            if (timeList == null) {
                timeList = new ArrayList<>();
                timeMap.put(keyName[i], timeList);
            }
            timeList.add(new Time(keyTime[i]));
        }

        List<Map.Entry<String, List<Time>>> entryList = new ArrayList<>(timeMap.entrySet());
        entryList.sort((e1, e2) -> e1.getKey().compareTo(e2.getKey()));

        List<String> ans = new ArrayList<>();
        for (Map.Entry<String, List<Time>> entry : entryList) {
            List<Time> timeList = entry.getValue();
            if (timeList.size() < 3) {
                continue;
            }

            timeList.sort((t1, t2) -> {
                if (t1.hour != t2.hour) {
                    return t1.hour - t2.hour;
                } else {
                    return t1.minute - t2.minute;
                }
            });

            boolean isAlerted = false;
            int size = timeList.size();
            for (int i = 2; i < size; i++) {
                Time currTime = timeList.get(i);
                Time lastTime = timeList.get(i - 2);

                if (currTime.compareTo(lastTime) <= 60) {
                    isAlerted = true;
                    break;
                }
            }

            if (isAlerted) {
                ans.add(entry.getKey());
            }
        }
        
        return ans;
    }
}
```
- Runtime: 57 ms (Beats: 90.11%)
- Memory: 65.20 MB (Beats: 63.44%)

<br>
