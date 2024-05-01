# [LeetCode Records](../../README.md) - Question 49 Group Anagrams

### Attempt 1: Use an int array to record the characters
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> result = new ArrayList<>();
        List<int[]> tables = new ArrayList<>();

        for (String str : strs) {
            int[] table = generateTable(str);

            boolean notFound = true;
            int size = tables.size();
            for (int j = 0; j < size; j++) {
                if (Arrays.equals(tables.get(j), table)) {
                    result.get(j).add(str);
                    notFound = false;
                    break;
                }
            }

            if (notFound) {
                List<String> list = new ArrayList<>();
                list.add(str);
                result.add(list);
                tables.add(table);
            }
        }

        return result;
    }

    private int[] generateTable(String str) {
        int[] table = new int[26];

        char[] chars = str.toCharArray();
        for (char ch : chars) {
            table[ch - 'a']++;
        }

        return table;
    }
}
```
- Runtime: 636 ms (Beats: 5.02%)
- Memory: 47.07 MB (Beats: 98.48%)

<br>

### Attempt 2: Use a hash code of an int array to record the characters
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> result = new ArrayList<>();
        List<Integer> tables = new ArrayList<>();

        for (String str : strs) {
            int table = generateTableHashCode(str);

            boolean notFound = true;
            int size = tables.size();
            for (int j = 0; j < size; j++) {
                if (tables.get(j) == table) {
                    result.get(j).add(str);
                    notFound = false;
                    break;
                }
            }

            if (notFound) {
                List<String> list = new ArrayList<>();
                list.add(str);
                result.add(list);
                tables.add(table);
            }
        }

        return result;
    }

    private int generateTableHashCode(String str) {
        int[] table = new int[26];

        char[] chars = str.toCharArray();
        for (char ch : chars) {
            table[ch - 'a']++;
        }

        return Arrays.hashCode(table);
    }
}
```
- Runtime: 85 ms (Beats: 5.02%)
- Memory: 47.53 MB (Beats: 74.45%)

<br>

### Attempt 3: Use a HashMap to record sorted strings
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();

        for (String str : strs) {
            char[] chars = str.toCharArray();
            Arrays.sort(chars);
            String sortedStr = Arrays.toString(chars);

            List<String> list = map.get(sortedStr);
            if (list == null) {
                list = new ArrayList<>();
                map.put(sortedStr, list);
            }
            list.add(str);
        }

        return map.values().stream().toList();
    }
}
```
- Runtime: 12 ms (Beats: 26.50%)
- Memory: 47.45 MB (Beats: 83.98%)

<br>

### Attempt 4: Use computeIfAbsent()
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();

        for (String str : strs) {
            char[] chars = str.toCharArray();
            Arrays.sort(chars);
            String sortedStr = Arrays.toString(chars);

            List<String> list = map.computeIfAbsent(sortedStr, k -> new ArrayList<>());
            list.add(str);
        }

        return map.values().stream().toList();
    }
}
```
- Runtime: 11 ms (Beats: 27.60%)
- Memory: 47.62 MB (Beats: 62.62%)

<br>

### Attempt 5: Use String.valueOf()
```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();

        for (String str : strs) {
            char[] chars = str.toCharArray();
            Arrays.sort(chars);
            String sortedStr = String.valueOf(chars);

            List<String> list = map.computeIfAbsent(sortedStr, k -> new ArrayList<>());
            list.add(str);
        }

        return new ArrayList<>(map.values());
    }
}
```
- Runtime: 6 ms (Beats: 97.16%)
- Memory: 47.80 MB (Beats: 39.20%)

<br>
