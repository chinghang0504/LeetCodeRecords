# [LeetCode Records](../../README.md) - Question 1169 Invalid Transactions

### Attempt 1: Use a HashMap to store the name and its transactions key-value pairs
```java
class Solution {

    class Transaction {

        String name;
        int time;
        int amount;
        String city;
        String original;

        Transaction(String transaction) {
            String[] splits = transaction.split(",");
            name = splits[0];
            time = Integer.valueOf(splits[1]);
            amount = Integer.valueOf(splits[2]);
            city = splits[3];
            original = transaction;
        }
    }

    public List<String> invalidTransactions(String[] transactions) {
        Map<String, List<Transaction>> nameMap = new HashMap<>();

        for (int i = 0; i < transactions.length; i++) {
            Transaction transaction = new Transaction(transactions[i]);
            List<Transaction> list = nameMap.get(transaction.name);
            if (list == null) {
                list = new ArrayList<>();
                nameMap.put(transaction.name, list);
            }
            list.add(transaction);
        }

        List<String> ans = new ArrayList<>();
        for (List<Transaction> list : nameMap.values()) {
            for (Transaction transaction1 : list) {
                if (transaction1.amount > 1000) {
                    ans.add(transaction1.original);
                    continue;
                }

                for (Transaction transaction2 : list) {
                    if (transaction1 == transaction2) {
                        continue;
                    } else if (!transaction1.city.equals(transaction2.city) && Math.abs(transaction1.time - transaction2.time) <= 60) {
                        ans.add(transaction1.original);
                        break;
                    }
                }
            }
        }

        return ans;
    }
}
```
- Runtime: 10 ms (Beats: 64.89%)
- Memory: 45.55 MB (Beats: 49.16%)

<br>
