# [LeetCode Records](../../README.md) - Question 831 Masking Personal Information

### Attempt 1: Use contains() to identify as an email address or a phone number
```java
class Solution {
    public String maskPII(String s) {
        return s.contains("@") ? getMaskedEmailAddress(s) : getMaskedPhoneNumber(s);
    }

    private String getMaskedEmailAddress(String s) {
        String[] splits = s.split("@");
        StringBuilder stringBuilder = new StringBuilder();

        stringBuilder.append(Character.toLowerCase(splits[0].charAt(0)));
        stringBuilder.append("*****");
        stringBuilder.append(Character.toLowerCase(splits[0].charAt(splits[0].length() - 1)));

        stringBuilder.append('@');

        stringBuilder.append(splits[1].toLowerCase());

        return stringBuilder.toString();
    }

    private String getMaskedPhoneNumber(String s) {
        char[] arr = s.toCharArray();

        StringBuilder localNumberStringBuilder = new StringBuilder();
        int i = arr.length - 1;
        for (int count = 0; count < 4; i--) {
            if (Character.isDigit(arr[i])) {
                count++;
                localNumberStringBuilder.append(arr[i]);
            }
        }

        for (int count = 0; count < 6; i--) {
            if (Character.isDigit(arr[i])) {
                count++;
            }
        }
        localNumberStringBuilder.append("-***-***");
        
        StringBuilder countryNumberStringBuilder = new StringBuilder();
        countryNumberStringBuilder.append('+');
        for (; i >= 0; i--) {
            if (Character.isDigit(arr[i])) {
                countryNumberStringBuilder.append('*');
            }
        }

        String localNumber = localNumberStringBuilder.reverse().toString();
        if (countryNumberStringBuilder.length() == 1) {
            return localNumber;
        } else {
            countryNumberStringBuilder.append('-');
            return countryNumberStringBuilder.append(localNumber).toString();
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.48 MB (Beats: 71.14%)

<br>
