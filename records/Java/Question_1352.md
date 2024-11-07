# [LeetCode Records](../../README.md) - Question 1352 Product of the Last K Numbers

### Attempt 1: Use an ArrayList to store the current product and store the last index of zero
```java
class ProductOfNumbers {

    private List<Integer> productList;
    private int product;
    private int lastZeroIndex;

    public ProductOfNumbers() {
        productList = new ArrayList<>();
        product = 1;
        lastZeroIndex = -1;
    }
    
    public void add(int num) {
        if (num == 0) {
            lastZeroIndex = productList.size();
            product = 1;
            productList.addLast(0);
        } else {
            product *= num;
            productList.addLast(product);
        }
    }
    
    public int getProduct(int k) {
        int size = productList.size();
        if (size - k <= lastZeroIndex) {
            return 0;
        }

        int lastIndex = size - 1;
        int startIndex = size - k - 1;
        if (startIndex < 0 || startIndex == lastZeroIndex) {
            return productList.get(lastIndex);
        } else {
            return productList.get(lastIndex) / productList.get(startIndex);
        }
    }
}

/**
 * Your ProductOfNumbers object will be instantiated and called as such:
 * ProductOfNumbers obj = new ProductOfNumbers();
 * obj.add(num);
 * int param_2 = obj.getProduct(k);
 */
```
- Runtime: 14 ms (Beats: 100.00%)
- Memory: 68.64 MB (Beats: 65.33%)

<br>
