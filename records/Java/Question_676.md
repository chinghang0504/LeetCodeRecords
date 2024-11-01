# [LeetCode Records](../../README.md) - Question 676 Implement Magic Dictionary

### Attempt 1: Use a HashMap to store the length and all the strings with the same length key-value pairs
```java
class MagicDictionary {

    private Map<Integer, List<String>> map;

    public MagicDictionary() {
        map = new HashMap<>();    
    }
    
    public void buildDict(String[] dictionary) {
        for (String word : dictionary) {
            int len = word.length();
            List<String> list = map.get(len);
            if (list == null) {
                list = new ArrayList<>();
                map.put(len, list);
            }

            list.add(word);
        }
    }
    
    public boolean search(String searchWord) {
        List<String> list = map.get(searchWord.length());
        if (list == null) {
            return false;
        }

        char[] arr1 = searchWord.toCharArray();
        for (String word : list) {
            char[] arr2 = word.toCharArray();
            if (isValid(arr1, arr2)) {
                return true;
            }
        }

        return false;
    }

    private boolean isValid(char[] arr1, char[] arr2) {
        int count = 0;
        for (int i = 0; i < arr1.length; i++) {
            if (arr1[i] != arr2[i]) {
                count++;

                if (count == 2) {
                    return false;
                }
            }
        }

        return count == 1;
    }
}

/**
 * Your MagicDictionary object will be instantiated and called as such:
 * MagicDictionary obj = new MagicDictionary();
 * obj.buildDict(dictionary);
 * boolean param_2 = obj.search(searchWord);
 */
```
- Runtime: 24 ms (Beats: 88.00%)
- Memory: 45.24 MB (Beats: 86.46%)

<br>
