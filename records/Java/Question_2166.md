# [LeetCode Records](../../README.md) - Question 2166 Design Bitset

### Attempt 1: Use two char[] to store the bits
```java
class Bitset {

    private char[] bits1;
    private char[] bits2;
    private int oneCount;
    private boolean isFlipped;

    public Bitset(int size) {
        bits1 = new char[size];
        bits2 = new char[size];
        for (int i = 0; i < size; i++) {
            bits1[i] = '0';
            bits2[i] = '1';
        }

        oneCount = 0;
        isFlipped = false;
    }

    public void fix(int idx) {
        if (isFlipped) {
            if (bits1[idx] == '1') {
                bits1[idx] = '0';
                bits2[idx] = '1';
                oneCount--;
            }
        } else {
            if (bits1[idx] == '0') {
                bits1[idx] = '1';
                bits2[idx] = '0';
                oneCount++;
            }
        }
    }

    public void unfix(int idx) {
        if (isFlipped) {
            if (bits1[idx] == '0') {
                bits1[idx] = '1';
                bits2[idx] = '0';
                oneCount++;
            }
        } else {
            if (bits1[idx] == '1') {
                bits1[idx] = '0';
                bits2[idx] = '1';
                oneCount--;
            }
        }
    }

    public void flip() {
        isFlipped = !isFlipped;
    }

    public boolean all() {
        return isFlipped ? oneCount == 0 : oneCount == bits1.length;
    }

    public boolean one() {
        return isFlipped ? oneCount != bits1.length : oneCount > 0;
    }

    public int count() {
        return isFlipped ? bits1.length - oneCount : oneCount;
    }

    public String toString() {
        char[] arr = isFlipped ? bits2 : bits1;
        return new String(arr);
    }
}

/**
 * Your Bitset object will be instantiated and called as such:
 * Bitset obj = new Bitset(size);
 * obj.fix(idx);
 * obj.unfix(idx);
 * obj.flip();
 * boolean param_4 = obj.all();
 * boolean param_5 = obj.one();
 * int param_6 = obj.count();
 * String param_7 = obj.toString();
 */
```
- Runtime: 43 ms (Beats: 96.00%)
- Memory: 86.72 MB (Beats: 44.93%)

<br>
