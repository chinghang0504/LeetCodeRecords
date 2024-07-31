# [LeetCode Records](../../README.md) - Question 1507 Reformat Date

### Attempt 1: Use split() to date strings
```java
class Solution {

    public String reformatDate(String date) {
        String[] dateSplits = date.split("\s");
        String year = dateSplits[2];
        String month = getMonth(dateSplits[1]);
        String dayOfMonth = getDayOfMonth(dateSplits[0]);

        return String.format("%s-%s-%s", year, month, dayOfMonth);
    }

    private String getMonth(String month) {
        switch (month) {
            case "Jan":
                return "01";
            case "Feb":
                return "02";
            case "Mar":
                return "03";
            case "Apr":
                return "04";
            case "May":
                return "05";
            case "Jun":
                return "06";
            case "Jul":
                return "07";
            case "Aug":
                return "08";
            case "Sep":
                return "09";
            case "Oct":
                return "10";
            case "Nov":
                return "11";
            case "Dec":
                return "12";
            default:
                return "";
        }
    }

    private String getDayOfMonth(String dayOfMonth) {
        char ch2 = dayOfMonth.charAt(1);

        return ch2 >= '0' && ch2 <= '9' ? dayOfMonth.substring(0, 2) : "0" + dayOfMonth.charAt(0);
    }
}
```
- Runtime: 5 ms (Beats: 47.20%)
- Memory: 41.62 MB (Beats: 53.22%)

<br>
