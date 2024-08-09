# [LeetCode Records](../../README.md) - Question 604 Design Compressed String Iterator

### Attempt 1: Use two List to store the character and its number of times
```java
class StringIterator {

    private List<Character> characterList;
    private List<Integer> timeList;
    private int currChIndex = 0;
    private int currTime = 0;

    public StringIterator(String compressedString) {
        char[] arr = compressedString.toCharArray();

        characterList = new ArrayList<>();
        timeList = new ArrayList<>();
        
        int i = 0;
        while (i < arr.length) {
            characterList.add(arr[i]);

            i++;
            int start = i;
            while (i < arr.length && Character.isDigit(arr[i])) {
                i++;
            }
            int time = Integer.valueOf(compressedString.substring(start, i));
            timeList.add(time);
        }
    }
    
    public char next() {
        if (!hasNext()) {
            return ' ';
        }

        char answer = characterList.get(currChIndex);
        currTime++;

        if (currTime >= timeList.get(currChIndex)) {
            currChIndex++;
            currTime = 0;
        }

        return answer;
    }
    
    public boolean hasNext() {
        return currChIndex != characterList.size();
    }
}
```
- Runtime: 12 ms (Beats: 62.42%)
- Memory: 44.64 MB (Beats: 57.58%)

<br>
