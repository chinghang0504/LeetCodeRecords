# [LeetCode Records](../../README.md) - Question 3391 Design a 3D Binary Matrix with Efficient Layer Tracking

### Attempt 1: Use PriorityQueue to store the sorted item with the index and its count
```java
class Matrix3D {

    private int[][][] matrix;
    private int[][] items;
    private Queue<int[]> priorityQueue;

    public Matrix3D(int n) {
        matrix = new int[n][n][n];
        items = new int[n][2];
        priorityQueue = new PriorityQueue<>((item1, item2) -> {
            if (item1[1] != item2[1]) {
                return item2[1] - item1[1];
            } else {
                return item2[0] - item1[0];
            }
        });

        for (int i = 0; i < n; i++) {
            items[i][0] = i;
            items[i][1] = 0;
            priorityQueue.add(items[i]);
        }
    }
    
    public void setCell(int x, int y, int z) {
        if (this.matrix[x][y][z] == 0) {
            this.matrix[x][y][z] = 1;

            priorityQueue.remove(this.items[x]);
            this.items[x][1]++;
            priorityQueue.add(this.items[x]);
        }
    }
    
    public void unsetCell(int x, int y, int z) {
        if (this.matrix[x][y][z] == 1) {
            this.matrix[x][y][z] = 0;
            
            priorityQueue.remove(this.items[x]);
            this.items[x][1]--;
            priorityQueue.add(this.items[x]);
        }
    }
    
    public int largestMatrix() {
        return priorityQueue.peek()[0];
    }
}

/**
 * Your Matrix3D object will be instantiated and called as such:
 * Matrix3D obj = new Matrix3D(n);
 * obj.setCell(x,y,z);
 * obj.unsetCell(x,y,z);
 * int param_3 = obj.largestMatrix();
 */
```
- Runtime: 97 ms (Beats: 55.56%)
- Memory: 108.24 MB (Beats: 55.56%)

<br>

### Attempt 2: Use an int[] to store the count of each x
```java
class Matrix3D {

    private int[][][] matrix;
    private int[] counts;

    public Matrix3D(int n) {
        matrix = new int[n][n][n];
        counts = new int[n];
    }
    
    public void setCell(int x, int y, int z) {
        if (matrix[x][y][z] == 0) {
            matrix[x][y][z] = 1;
            counts[x]++;
        }
    }
    
    public void unsetCell(int x, int y, int z) {
        if (matrix[x][y][z] == 1) {
            matrix[x][y][z] = 0;
            counts[x]--;
        }
    }
    
    public int largestMatrix() {
        int maxIndex = counts.length - 1;
        int maxCount = counts[maxIndex];
        for (int i = counts.length - 2; i >= 0; i--) {
            if (counts[i] > maxCount) {
                maxCount = counts[i];
                maxIndex = i;
            }
        }
        
        return maxIndex;
    }
}

/**
 * Your Matrix3D object will be instantiated and called as such:
 * Matrix3D obj = new Matrix3D(n);
 * obj.setCell(x,y,z);
 * obj.unsetCell(x,y,z);
 * int param_3 = obj.largestMatrix();
 */
```
- Runtime: 56 ms (Beats: 94.44%)
- Memory: 106.55 MB (Beats: 88.89%)

<br>
