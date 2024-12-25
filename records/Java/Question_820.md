# [LeetCode Records](../../README.md) - Question 820 Short Encoding of Words

### Attempt 1: Use a Trie to store the words 
```java
class Solution {

    class Trie {

        class Node {

            Node[] nodes;
            boolean isWord;

            Node() {
                nodes = new Node[26];
                isWord = false;
            }
        }

        Node head;
        int count;

        Trie() {
            head = new Node();
            count = 0;
        }

        void insert(String str) {
            char[] arr = str.toCharArray();

            boolean isNewWord = false;
            Node curr = head;
            for (int i = arr.length - 1; i >= 0; i--) {
                if (curr.nodes[arr[i] - 'a'] == null) {
                    curr.nodes[arr[i] - 'a'] = new Node();
                    curr = curr.nodes[arr[i] - 'a'];
                    isNewWord = true;
                } else {
                    curr = curr.nodes[arr[i] - 'a'];
                    if (curr.isWord) {
                        count -= arr.length - i + 1;
                        curr.isWord = false;
                    }
                } 
            }
            curr.isWord = true;

            if (isNewWord) {
                count += arr.length + 1;
            }
        }
    }

    public int minimumLengthEncoding(String[] words) {
        Set<String> set = new HashSet<>();
        for (String word : words) {
            set.add(word);
        }

        Trie trie = new Trie();
        for (String word : set) {
            trie.insert(word);
        }

        return trie.count;
    }
}
```
- Runtime: 11 ms (Beats: 93.30%)
- Memory: 48.07 MB (Beats: 29.05%)

<br>
