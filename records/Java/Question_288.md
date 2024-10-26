# [LeetCode Records](../../README.md) - Question 288 Unique Word Abbreviation

### Attempt 1: Use a HashMap to store the abbreviation and its count key-value pairs and a HashSet to store the words in dictionary
```java
class ValidWordAbbr {

    private Map<String, Integer> map;
    private Set<String> set;

    public ValidWordAbbr(String[] dictionary) {
        map = new HashMap<>();
        set = new HashSet<>();

        for (String word : dictionary) {
            if (!set.contains(word)) {
                String abbreviation = getAbbreviation(word);
                map.merge(abbreviation, 1, Integer::sum);
                set.add(word);
            }
        }
    }

    private String getAbbreviation(String word) {
        int len = word.length();
        if (len <= 2) {
            return word;
        }

        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append(word.charAt(0));
        stringBuilder.append(len - 2);
        stringBuilder.append(word.charAt(len - 1));

        return stringBuilder.toString();
    }

    public boolean isUnique(String word) {
        String abbreviation = getAbbreviation(word);

        Integer count = map.get(abbreviation);

        if (count == null) {
            return true;
        }

        return count == 1 && set.contains(word);
    }
}

/**
 * Your ValidWordAbbr object will be instantiated and called as such:
 * ValidWordAbbr obj = new ValidWordAbbr(dictionary);
 * boolean param_1 = obj.isUnique(word);
 */
```
- Runtime: 66 ms (Beats: 87.50%)
- Memory: 55.29 MB (Beats: 71.76%)

<br>
