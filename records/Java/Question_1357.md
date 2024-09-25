# [LeetCode Records](../../README.md) - Question 1357 Apply Discount Every n Orders

### Attempt 1: Use a HashMap to store the product id and price key-value pairs
```java
class Cashier {

    private Map<Integer, Integer> productPrices;
    private int customerNum;
    private int selectedCustomerNum;
    private double discountFactor;

    public Cashier(int n, int discount, int[] products, int[] prices) {
        productPrices = new HashMap<>();
        for (int i = 0; i < products.length; i++) {
            productPrices.put(products[i], prices[i]);
        }
        customerNum = 1;
        selectedCustomerNum = n;
        discountFactor = (100.0 - discount) / 100.0;
    }
    
    public double getBill(int[] product, int[] amount) {
        double total = 0.0;
        for (int i = 0; i < product.length; i++) {
            total += productPrices.get(product[i]) * amount[i];
        }

        if (customerNum % selectedCustomerNum == 0) {
            total *= discountFactor;
        }

        customerNum++;
        return total;
    }
}

/**
 * Your Cashier object will be instantiated and called as such:
 * Cashier obj = new Cashier(n, discount, products, prices);
 * double param_1 = obj.getBill(product,amount);
 */
```
- Runtime: 110 ms (Beats: 40.44%)
- Memory: 73.70 MB (Beats: 81.25%)

<br>
