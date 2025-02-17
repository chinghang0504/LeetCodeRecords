# [LeetCode Records](../../README.md) - Question 3387 Maximize Amount After Two Days of Conversions

### Attempt 1: Use a HashMap to store the currency to currency and its rate key-value pairs. Use depth first search to update the amount of specific currency
```java
class Solution {

    private Map<String, Map<String, Double>> currencyToCurrencyMap;
    private Map<String, Double> currencyToAmount;
    private Set<String> currencySet;
    
    public double maxAmount(String initialCurrency, List<List<String>> pairs1, double[] rates1, List<List<String>> pairs2, double[] rates2) {
        this.currencyToCurrencyMap = getCurrencyToCurrencyMap(pairs1, rates1);
        
        this.currencyToAmount = new HashMap<>();
        this.currencyToAmount.put(initialCurrency, 1.0);
        dfs(initialCurrency, 1.0);

        this.currencyToCurrencyMap = getCurrencyToCurrencyMap(pairs2, rates2);
        this.currencySet = new HashSet<>();
        for (String currency : this.currencyToAmount.keySet()) {
            this.currencySet.add(currency);
        }

        while (!this.currencySet.isEmpty()) {
            updateAmount();
        }

        return this.currencyToAmount.get(initialCurrency);
    }

    private Map<String, Map<String, Double>> getCurrencyToCurrencyMap(List<List<String>> pairs, double[] rates) {
        Map<String, Map<String, Double>> currencyToCurrencyMap = new HashMap<>();

        int i = 0;
        for (List<String> pair : pairs) {
            String currency1 = pair.getFirst();
            String currency2 = pair.getLast();

            Map<String, Double> currencyMap = currencyToCurrencyMap.get(currency1);
            if (currencyMap == null) {
                currencyMap = new HashMap<>();
                currencyToCurrencyMap.put(currency1, currencyMap);
            }
            currencyMap.put(currency2, rates[i]);

            currencyMap = currencyToCurrencyMap.get(currency2);
            if (currencyMap == null) {
                currencyMap = new HashMap<>();
                currencyToCurrencyMap.put(currency2, currencyMap);
            }
            currencyMap.put(currency1, 1.0 / rates[i]);

            i++;
        }

        return currencyToCurrencyMap;
    }

    private void dfs(String currency, double amount) {
        Map<String, Double> currencyMap = this.currencyToCurrencyMap.get(currency);

        for (Map.Entry<String, Double> entry : currencyMap.entrySet()) {
            String targetCurrency = entry.getKey();
            double targetRate = entry.getValue();

            if (!this.currencyToAmount.containsKey(targetCurrency)) {
                double targetAmount = amount * targetRate;
                this.currencyToAmount.put(targetCurrency, targetAmount);
                dfs(targetCurrency, targetAmount);
            }
        }
    }

    private void updateAmount() {
        Set<String> nextCurrencySet = new HashSet<>();

        for (String currency : currencySet) {
            Map<String, Double> currencyMap = this.currencyToCurrencyMap.get(currency);
            if (currencyMap == null) {
                continue;
            }
            double amount = this.currencyToAmount.get(currency);

            for (Map.Entry<String, Double> entry : currencyMap.entrySet()) {
                String targetCurrency = entry.getKey();
                double targetRate = entry.getValue();
                double targetAmount = amount * targetRate;

                Double originalAmount = this.currencyToAmount.get(targetCurrency);
                if (originalAmount == null || targetAmount > originalAmount) {
                    this.currencyToAmount.put(targetCurrency, targetAmount);
                    nextCurrencySet.add(targetCurrency);
                }
            }
        }

        currencySet = nextCurrencySet;
    }
}
```
- Runtime: 8 ms (Beats: 74.08%)
- Memory: 47.12 MB (Beats: 43.20%)

<br>
