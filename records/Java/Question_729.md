# [LeetCode Records](../../README.md) - Question 729 My Calendar I

### Attempt 1: Use an ArrayList to store the time
```java
class MyCalendar {

    private List<int[]> list;

    public MyCalendar() {
        list = new ArrayList<>();
    }
    
    public boolean book(int startTime, int endTime) {
        for (int[] time : list) {
            if (time[0] < endTime && startTime < time[1]) {
                return false;
            }
        }

        list.add(new int[]{ startTime, endTime });
        return true;
    }
}

/**
 * Your MyCalendar object will be instantiated and called as such:
 * MyCalendar obj = new MyCalendar();
 * boolean param_1 = obj.book(startTime,endTime);
 */
```
- Runtime: 77 ms (Beats: 25.75%)
- Memory: 46.08 MB (Beats: 6.99%)

<br>
