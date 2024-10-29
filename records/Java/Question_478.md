# [LeetCode Records](../../README.md) - Question 478 Generate Random Point in a Circle

### Attempt 1: Use Math.sqrt(random.nextDouble()) to generate a random point in a circle uniformly 
```java
class Solution {

    private double radius;
    private double x_center;
    private double y_center;
    private Random random;
    private double twoPi;

    public Solution(double radius, double x_center, double y_center) {
        this.radius = radius;
        this.x_center = x_center;
        this.y_center = y_center;
        this.random = new Random();
        this.twoPi = 2 * Math.PI;
    }
    
    public double[] randPoint() {
        double r = Math.sqrt(random.nextDouble()) * radius;
        double theta = random.nextDouble() * twoPi;

        double x = x_center + r * Math.cos(theta);
        double y = y_center + r * Math.sin(theta);

        return new double[]{ x, y };
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(radius, x_center, y_center);
 * double[] param_1 = obj.randPoint();
 */
```
- Runtime: 206 ms (Beats: 100.00%)
- Memory: 52.52 MB (Beats: 89.52%)

<br>
