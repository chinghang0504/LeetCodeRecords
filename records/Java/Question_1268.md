# [LeetCode Records](../../README.md) - Question 1268 Search Suggestions System

### Attempt 1: Use Arrays.sort() to sort the products
```java
class Solution {
    public List<List<String>> suggestedProducts(String[] products, String searchWord) {
        Arrays.sort(products);

        int size = searchWord.length();
        List<List<String>> ans = new ArrayList<>();
        for (int i = 1; i <= size; i++) {
            List<String> list = new ArrayList<>();
            String word = searchWord.substring(0, i);

            int count = 0;
            for (int j = 0; j < products.length && count < 3; j++) {
                if (products[j].startsWith(word)) {
                    list.add(products[j]);
                    count++;
                }
            }

            ans.add(list);
        }

        return ans;
    }
}
```
- Runtime: 22 ms (Beats: 59.02%)
- Memory: 46.49 MB (Beats: 94.97%)

<br>
