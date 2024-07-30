# [LeetCode Records](../../README.md) - Question 1279 Traffic Light Controlled Intersection

### Attempt 1: Use a LinkedBlockingQueue to track car IDs
```java
class TrafficLight {

    private int roadIdIsGreen;
    private BlockingQueue<Integer> queue;

    public TrafficLight() {
        roadIdIsGreen = 1;
        queue = new LinkedBlockingQueue();
    }
    
    public void carArrived(
        int carId,           // ID of the car
        int roadId,          // ID of the road the car travels on. Can be 1 (road A) or 2 (road B)
        int direction,       // Direction of the car
        Runnable turnGreen,  // Use turnGreen.run() to turn light to green on current road
        Runnable crossCar    // Use crossCar.run() to make car cross the intersection 
    ) {
        queue.add(carId);

        while (queue.peek() != carId) {}

        if (roadIdIsGreen != roadId) {
            roadIdIsGreen = roadId;
            turnGreen.run();
        }
        crossCar.run();

        queue.poll();
    }
}
```
- Runtime: 11 ms (Beats: 97.70%)
- Memory: 43.46 MB (Beats: 70.11%)

<br>
