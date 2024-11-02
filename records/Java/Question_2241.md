# [LeetCode Records](../../README.md) - Question 2241 Design an ATM Machine

### Attempt 1: Use an int[] to store the number of each notes
```java
class ATM {

    private int[] banknotes;
    private int[] counts;

    public ATM() {
        banknotes = new int[]{ 20, 50, 100, 200, 500 };
        counts = new int[5];
    }
    
    public void deposit(int[] banknotesCount) {
        for (int i = 0; i < 5; i++) {
            counts[i] += banknotesCount[i];
        }
    }
    
    public int[] withdraw(int amount) {
        int[] ans = new int[5];

        for (int i = 4; i >= 0; i--) {
            int numOfNotes = Math.min(amount / banknotes[i], counts[i]);
            ans[i] = numOfNotes;
            amount -= numOfNotes * banknotes[i];
        }

        if (amount > 0) {
            return new int[]{ -1 };
        }

        for (int i = 0; i < 5; i++) {
            counts[i] -= ans[i];
        }

        return ans;
    }
}

/**
 * Your ATM object will be instantiated and called as such:
 * ATM obj = new ATM();
 * obj.deposit(banknotesCount);
 * int[] param_2 = obj.withdraw(amount);
 */
```
- Runtime: 54 ms (Beats: 100.00%)
- Memory: 48.86 MB (Beats: 10.87%)

<br>
