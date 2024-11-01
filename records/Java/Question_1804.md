# [LeetCode Records](../../README.md) - Question 1804 Implement Trie II (Prefix Tree)

### Attempt 1: Create a class Node that can store an Node[], the start with count, and the word count
```java
class Trie {

    class Node {

        Node[] nodes;
        int countStartWith;
        int countWord;

        Node() {
            nodes = new Node[26];
            countStartWith = 0;
            countWord = 0;
        }
    }

    private Node head;

    public Trie() {
        head = new Node();
    }
    
    public void insert(String word) {
        Node curr = head;
        for (char ch : word.toCharArray()) {
            curr.countStartWith++;

            Node next = curr.nodes[ch - 'a'];
            if (next == null) {
                next = new Node();
                curr.nodes[ch - 'a'] = next;
            }
            curr = next;
        }

        curr.countStartWith++;
        curr.countWord++;
    }
    
    public int countWordsEqualTo(String word) {
        Node curr = head;
        for (char ch : word.toCharArray()) {
            Node next = curr.nodes[ch - 'a'];
            if (next == null) {
                return 0;
            }
            curr = next;
        }

        return curr.countWord;
    }
    
    public int countWordsStartingWith(String prefix) {
        Node curr = head;
        for (char ch : prefix.toCharArray()) {
            Node next = curr.nodes[ch - 'a'];
            if (next == null) {
                return 0;
            }
            curr = next;
        }

        return curr.countStartWith;
    }
    
    public void erase(String word) {
        Node curr = head;
        for (char ch : word.toCharArray()) {
            curr.countStartWith--;

            Node next = curr.nodes[ch - 'a'];
            if (next == null) {
                return;
            }
            curr = next;
        }

        curr.countStartWith--;
        curr.countWord--;
    }
}

/**
 * Your Trie object will be instantiated and called as such:
 * Trie obj = new Trie();
 * obj.insert(word);
 * int param_2 = obj.countWordsEqualTo(word);
 * int param_3 = obj.countWordsStartingWith(prefix);
 * obj.erase(word);
 */
```
- Runtime: 68 ms (Beats: 100.00%)
- Memory: 57.82 MB (Beats: 42.56%)

<br>
