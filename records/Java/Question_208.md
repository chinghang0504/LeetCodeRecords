# [LeetCode Records](../../README.md) - Question 208 Implement Trie (Prefix Tree)

### Attempt 1: Use a HashSet
```java
class Trie {

    private HashSet<String> container;

    public Trie() {
        this.container = new HashSet<>();
    }

    public void insert(String word) {
        this.container.add(word);
    }

    public boolean search(String word) {
        return this.container.contains(word);
    }

    public boolean startsWith(String prefix) {
        for (String str : this.container) {
            if (str.startsWith(prefix)) {
                return true;
            }
        }
        return false;
    }
}
```
- Runtime: 248 ms (Beats: 5.02%)
- Memory: 52.33 MB (Beats: 98.52%)

<br>
