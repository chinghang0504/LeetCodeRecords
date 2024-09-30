# [LeetCode Records](../../README.md) - Question 1396 Design Underground System

### Attempt 1: Use three HashMap to store the data
```java
class UndergroundSystem {

    Map<Integer, Pair<String, Integer>> checkInMap;
    Map<Pair<String, String>, Integer> timeInMap;
    Map<Pair<String, String>, Integer> numInMap;

    public UndergroundSystem() {
        checkInMap = new HashMap<>();
        timeInMap = new HashMap<>();
        numInMap = new HashMap<>();
    }
    
    public void checkIn(int id, String stationName, int t) {
        checkInMap.put(id, new Pair<>(stationName, t));
    }
    
    public void checkOut(int id, String stationName, int t) {
        Pair<String, Integer> pair = checkInMap.get(id);
        checkInMap.remove(id);

        String startStation = pair.getKey();
        int timeDiff = t - pair.getValue();

        Pair<String, String> stations = new Pair<>(startStation, stationName);
        timeInMap.merge(stations, timeDiff, Integer::sum);
        numInMap.merge(stations, 1, Integer::sum);
    }
    
    public double getAverageTime(String startStation, String endStation) {
        Pair<String, String> stations = new Pair<>(startStation, endStation);
        return (double)timeInMap.get(stations) / numInMap.get(stations);
    }
}

/**
 * Your UndergroundSystem object will be instantiated and called as such:
 * UndergroundSystem obj = new UndergroundSystem();
 * obj.checkIn(id,stationName,t);
 * obj.checkOut(id,stationName,t);
 * double param_3 = obj.getAverageTime(startStation,endStation);
 */
```
- Runtime: 93 ms (Beats: 77.87%)
- Memory: 55.44 MB (Beats: 60.21%)

<br>
