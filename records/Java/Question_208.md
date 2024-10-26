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

### Attempt 2: Create a suffix tree
```java
class Trie {

    class Node {
        Node[] nodes;
        boolean isWord;

        Node() {
            nodes = new Node[26];
            isWord = false;
        }
    }

    private Node head;

    public Trie() {
        head = new Node();
    }

    public void insert(String word) {
        Node curr = head;
        for (char ch : word.toCharArray()) {
            Node node = curr.nodes[ch - 'a'];
            if (node == null) {
                node = new Node();
                curr.nodes[ch - 'a'] = node;
            }
            curr = node;
        }

        curr.isWord = true;
    }

    public boolean search(String word) {
        Node curr = head;
        for (char ch : word.toCharArray()) {
            Node node = curr.nodes[ch - 'a'];
            if (node == null) {
                return false;
            }
            curr = node;
        }

        return curr.isWord;
    }

    public boolean startsWith(String prefix) {
        Node curr = head;
        for (char ch : prefix.toCharArray()) {
            Node node = curr.nodes[ch - 'a'];
            if (node == null) {
                return false;
            }
            curr = node;
        }

        return true;
    }
}

/**
 * Your Trie object will be instantiated and called as such:
 * Trie obj = new Trie();
 * obj.insert(word);
 * boolean param_2 = obj.search(word);
 * boolean param_3 = obj.startsWith(prefix);
 */
```
- Runtime: 31 ms (Beats: 98.71%)
- Memory: 55.38 MB (Beats: 43.46%)

<br>
