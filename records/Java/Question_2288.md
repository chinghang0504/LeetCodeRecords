# [LeetCode Records](../../README.md) - Question 2288 Apply Discount to Prices

### Attempt 1: Use String.format() to format the price
```java
class Solution {
    public String discountPrices(String sentence, int discount) {
        String[] splits = sentence.split("\s");

        for (int i = 0; i < splits.length; i++) {
            splits[i] = updateWord(splits[i], discount);
        }

        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append(splits[0]);
        for (int i = 1; i < splits.length; i++) {
            stringBuilder.append(' ');
            stringBuilder.append(splits[i]);
        }

        return stringBuilder.toString();
    }

    private String updateWord(String str, int discount) {
        char[] arr = str.toCharArray();

        if (arr[0] != '$' || arr.length <= 1) {
            return str;
        }

        double price = 0;
        for (int i = 1; i < arr.length; i++) {
            if (!Character.isDigit(arr[i])) {
                return str;
            } else {
                price = price * 10 + arr[i] - '0';
            }
        }

        double newPrice = price * (100 - discount) / 100.0;
        return String.format("$%.2f", newPrice);
    }
}
```
- Runtime: 117 ms (Beats: 81.20%)
- Memory: 52.76 MB (Beats: 69.49%)

<br>
