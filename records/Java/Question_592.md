# [LeetCode Records](../../README.md) - Question 592 Fraction Addition and Subtraction

### Attempt 1: Convert the string to a list of fractions
```java
class Solution {

    static class Fraction {
        int numerator;
        int denominator;

        Fraction(int numerator, int denominator) {
            this.numerator = numerator;
            this.denominator = denominator;
        }

        static Fraction plus(Fraction f1, Fraction f2) {
            if (f1.denominator == f2.denominator) {
                int numerator = f1.numerator + f2.numerator;
                int denominator = numerator == 0 ? 1 : f1.denominator;
                return new Fraction(numerator, denominator).reduce();
            } else {
                int numerator = f1.numerator * f2.denominator + f2.numerator * f1.denominator;
                int denominator = f1.denominator * f2.denominator;
                return new Fraction(numerator, denominator).reduce();
            }
        }

        Fraction reduce() {
            int a = Math.abs(numerator);
            int b = Math.abs(denominator);
            for (int i = Math.min(a, b); i >= 2; i--) {
                if (a % i == 0 && b % i == 0) {
                    numerator /= i;
                    denominator /= i;
                    break;
                }
            }

            return this;
        }

        @Override
        public String toString() {
            StringBuilder stringBuilder = new StringBuilder();
            stringBuilder.append(numerator);
            stringBuilder.append('/');
            stringBuilder.append(denominator);
            return stringBuilder.toString();
        }
    }

    public String fractionAddition(String expression) {
        List<Fraction> list = getFractionList(expression);

        int size = list.size();
        Fraction result = list.get(0);
        for (int i = 1; i < size; i++) {
            result = Fraction.plus(result, list.get(i));
        }

        return result.toString();
    }

    private List<Fraction> getFractionList(String expression) {
        List<Fraction> list = new ArrayList<>();
        char[] arr = expression.toCharArray();

        int curr = 0;
        while (curr < arr.length) {
            boolean isNegative = false;
            int numerator = 0;
            int denominator = 0;

            if (arr[curr] == '+') {
                curr++;
            } else if (arr[curr] == '-') {
                isNegative = true;
                curr++;
            }

            while (arr[curr] != '/') {
                numerator = numerator * 10 + arr[curr] - '0';
                curr++;
            }
            curr++;
            while (curr < arr.length && arr[curr] != '+' && arr[curr] != '-') {
                denominator = denominator * 10 + arr[curr] - '0';
                curr++;
            }

            if (isNegative) {
                numerator *= -1;
            }

            list.add(new Fraction(numerator, denominator));
        }

        return list;
    }
}
```
- Runtime: 1 ms (Beats: 99.76%)
- Memory: 41.34 MB (Beats: 98.14%)

<br>
