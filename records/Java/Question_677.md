# [LeetCode Records](../../README.md) - Question 677 Map Sum Pairs

### Attempt 1: Use Trie to store the sum for each character
```java
class MapSum {

    class Trie {

        class Node {

            int sum;
            Node[] nodes;

            Node() {
                sum = 0;
                nodes = new Node[26];
            }

            Node(int val) {
                sum = val;
                nodes = new Node[26];
            }
        }

        Node head;

        Trie() {
            head = new Node();
        }

        void insert(String str, int val) {
            Node curr = head;
            for (char ch : str.toCharArray()) {
                if (curr.nodes[ch - 'a'] == null) {
                    curr.nodes[ch - 'a'] = new Node(val);
                } else {
                    curr.nodes[ch - 'a'].sum += val;
                }
                curr = curr.nodes[ch - 'a'];
            }
        }

        int getSum(String prefix) {
            Node curr = head;
            for (char ch : prefix.toCharArray()) {
                if (curr.nodes[ch - 'a'] == null) {
                    return 0;
                }
                curr = curr.nodes[ch - 'a'];
            }
            return curr.sum;
        }
    }

    private Trie trie;
    private Map<String, Integer> map;

    public MapSum() {
        trie = new Trie();
        map = new HashMap<>();
    }
    
    public void insert(String key, int val) {
        Integer prevVal = map.get(key);
        if (prevVal == null) {
            trie.insert(key, val);
        } else {
            trie.insert(key, val - prevVal);
        }
        map.put(key, val);
    }
    
    public int sum(String prefix) {
        return trie.getSum(prefix);
    }
}

/**
 * Your MapSum object will be instantiated and called as such:
 * MapSum obj = new MapSum();
 * obj.insert(key,val);
 * int param_2 = obj.sum(prefix);
 */
```
- Runtime: 10 ms (Beats: 100.00%)
- Memory: 42.60 MB (Beats: 53.56%)

<br>
