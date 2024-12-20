# [LeetCode Records](../../README.md) - Question 635 Design Log Storage System

### Attempt 1: Use a SortedSet to store the data with id and its timestamp
```java
class LogSystem {

    class Data {

        int id;
        String timestamp;

        Data(int id, String timestamp) {
            this.id = id;
            this.timestamp = timestamp;
        }

        int compareTo(Data data) {
            int val = this.timestamp.compareTo(data.timestamp);
            return val != 0 ? val : this.id - data.id;
        }
    }

    private SortedSet<Data> sortedSet;

    public LogSystem() {
        sortedSet = new TreeSet<>((s1, s2) -> s1.compareTo(s2));
    }
    
    public void put(int id, String timestamp) {
        sortedSet.add(new Data(id, timestamp));
    }

    private String getDateString(String date, String granularity) {
        if (granularity.equals("Year")) {
            return date.substring(0, 4);
        } else if (granularity.equals("Month")) {
            return date.substring(0, 7);
        } else if (granularity.equals("Day")) {
            return date.substring(0, 10);
        } else if (granularity.equals("Hour")) {
            return date.substring(0, 13);
        } else if (granularity.equals("Minute")) {
            return date.substring(0, 16);
        } else {
            return date;
        }
    }
    
    public List<Integer> retrieve(String start, String end, String granularity) {
        List<Integer> ans = new ArrayList<>();
        String startDate = getDateString(start, granularity);
        String endDate = getDateString(end, granularity);

        for (Data data : sortedSet) {
            String targetDate = getDateString(data.timestamp, granularity);

            int startDateCompare = startDate.compareTo(targetDate);
            if (startDateCompare > 0) {
                continue;
            } else if (startDateCompare == 0) {
                ans.add(data.id);
            } else {
                int endDateCompare = targetDate.compareTo(endDate);
                if (endDateCompare <= 0) {
                    ans.add(data.id);
                } else {
                    break;
                }
            }
        }

        return ans;
    }
}

/**
 * Your LogSystem object will be instantiated and called as such:
 * LogSystem obj = new LogSystem();
 * obj.put(id,timestamp);
 * List<Integer> param_2 = obj.retrieve(start,end,granularity);
 */
```
- Runtime: 31 ms (Beats: 95.12%)
- Memory: 46.21 MB (Beats: 13.41%)

<br>
