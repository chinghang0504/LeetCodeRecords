# [LeetCode Records](../../README.md) - Question 211 Design Add and Search Words Data Structure

### Attempt 1: Use a suffix tree
```java
class WordDictionary {

    class Node {
        Node[] nodes;
        boolean isWord;

        Node() {
            nodes = new Node[26];
            isWord = false;
        }
    }

    private Node head;

    public WordDictionary() {
        head = new Node();
    }
    
    public void addWord(String word) {
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
        char[] arr = word.toCharArray();

        return search(arr, 0, head);
    }

    private boolean search(char[] arr, int currIndex, Node curr) {
        char ch = arr[currIndex];
        if (currIndex == arr.length - 1) {
            if (ch == '.') {
                for (Node node : curr.nodes) {
                    if (node != null && node.isWord) {
                        return true;
                    }
                }

                return false;
            } else {
                Node node = curr.nodes[ch - 'a'];
                return node != null && node.isWord;
            }
        }

        if (ch == '.') {
            for (Node node : curr.nodes) {
                if (node != null) {
                    if (search(arr, currIndex + 1, node)) {
                        return true;
                    }
                }
            }

            return false;
        } else {
            Node node = curr.nodes[ch - 'a'];
            if (node == null) {
                return false;
            } else if (search(arr, currIndex + 1, node)) {
                return true;
            }

            return false;
        }
    }
}

/**
 * Your WordDictionary object will be instantiated and called as such:
 * WordDictionary obj = new WordDictionary();
 * obj.addWord(word);
 * boolean param_2 = obj.search(word);
 */
```
- Runtime: 158 ms (Beats: 99.11%)
- Memory: 86.54 MB (Beats: 91.11%)

<br>
