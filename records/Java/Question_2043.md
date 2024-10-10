# [LeetCode Records](../../README.md) - Question 2043 Simple Bank System

### Attempt 1: Use the same long[]
```java
class Bank {

    private long[] balances;

    public Bank(long[] balance) {
        balances = balance;
    }
    
    public boolean transfer(int account1, int account2, long money) {
        if (account1 < 1 || account1 > balances.length || account2 < 1 || account2 > balances.length || balances[account1 - 1] < money) {
            return false;
        }

        balances[account1 - 1] -= money;
        balances[account2 - 1] += money;
        return true;
    }
    
    public boolean deposit(int account, long money) {
        if (account < 1 || account > balances.length) {
            return false;
        }

        balances[account - 1] += money;
        return true;
    }
    
    public boolean withdraw(int account, long money) {
        if (account < 1 || account > balances.length || balances[account - 1] < money) {
            return false;
        }

        balances[account - 1] -= money;
        return true;
    }
}

/**
 * Your Bank object will be instantiated and called as such:
 * Bank obj = new Bank(balance);
 * boolean param_1 = obj.transfer(account1,account2,money);
 * boolean param_2 = obj.deposit(account,money);
 * boolean param_3 = obj.withdraw(account,money);
 */
```
- Runtime: 95 ms (Beats: 97.02%)
- Memory: 101.37 MB (Beats: 31.38%)

<br>
