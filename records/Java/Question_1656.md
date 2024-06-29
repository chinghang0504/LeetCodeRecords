# [LeetCode Records](../../README.md) - Question 1656 Design an Ordered Stream

### Attempt 1: Use a String[] to save the values
```java
class OrderedStream {

    private String[] saved;
    private int curr;

    public OrderedStream(int n) {
        saved = new String[n];
        curr = 0;
    }
    
    public List<String> insert(int idKey, String value) {
        int index = idKey - 1;
        saved[index] = value;

        List<String> result = new ArrayList<>();
        for (int i = curr; i < saved.length; i++) {
            if (saved[i] == null) {
                break;
            } else {
                result.add(saved[i]);
                curr++;
            }
        }

        return result;
    }
}
```
- Runtime: 76 ms (Beats: 97.86%)
- Memory: 45.99 MB (Beats: 29.90%)

<br>
