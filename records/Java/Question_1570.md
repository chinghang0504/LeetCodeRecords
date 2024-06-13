# [LeetCode Records](../../README.md) - Question 1570 Dot Product of Two Sparse Vectors

### Attempt 1: Use a HashMap
```java
class SparseVector {
    Map<Integer, Integer> map;
    
    SparseVector(int[] nums) {
        this.map = new HashMap<>();
        
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                this.map.put(i, nums[i]);
            }
        }
    }
    
	// Return the dotProduct of two sparse vectors
    public int dotProduct(SparseVector vec) {
        int sum = 0;

        for (int index : map.keySet()) {
            Integer val = vec.map.get(index);
            if (val != null) {
                sum += val * this.map.get(index);
            }
        }

        return sum;
    }
}
```
- Runtime: 9 ms (Beats: 62.16%)
- Memory: 57.76 MB (Beats: 35.96%)

<br>

### Attempt 2: Use an int[]
```java
class SparseVector {
    
    int[] nums;
    
    SparseVector(int[] nums) {
        this.nums = nums;
    }
    
	// Return the dotProduct of two sparse vectors
    public int dotProduct(SparseVector vec) {
        int sum = 0;

        for (int i = 0; i < this.nums.length; i++) {
            sum += this.nums[i] * vec.nums[i];
        }

        return sum;
    }
}
```
- Runtime: 2 ms (Beats: 99.94%)
- Memory: 56.40 MB (Beats: 94.40%)

<br>
