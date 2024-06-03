# [LeetCode Records](../../README.md) - Question 1603 Design Parking System

### Attempt 1: Use 6 variables
```java
class ParkingSystem {

    private int maxBig, maxMedium, maxSmall;
    private int big, medium, small;

    public ParkingSystem(int big, int medium, int small) {
        maxBig = big;
        maxMedium = medium;
        maxSmall = small;

        big = 0;
        medium = 0;
        small = 0;
    }
    
    public boolean addCar(int carType) {
        switch (carType) {
            case 1:
                if (big < maxBig) {
                    big++;
                    return true;
                }
                break;
            case 2:
                if (medium < maxMedium) {
                    medium++;
                    return true;
                }
                break;
            case 3:
                if (small < maxSmall) {
                    small++;
                    return true;
                }
                break;
        }

        return false;
    }
}
```
- Runtime: 8 ms (Beats: 63.87%)
- Memory: 45.05 MB (Beats: 63.30%)

<br>

### Attempt 2: Use 3 variables
```java
class ParkingSystem {

    private int big, medium, small;

    public ParkingSystem(int big, int medium, int small) {
        this.big = big;
        this.medium = medium;
        this.small = small;
    }
    
    public boolean addCar(int carType) {
        switch (carType) {
            case 1:
                if (this.big > 0) {
                    big--;
                    return true;
                }
                break;
            case 2:
                if (this.medium > 0) {
                    medium--;
                    return true;
                }
                break;
            case 3:
                if (this.small > 0) {
                    small--;
                    return true;
                }
                break;
        }

        return false;
    }
}
```
- Runtime: 7 ms (Beats: 100.00%)
- Memory: 44.78 MB (Beats: 94.21%)

<br>
