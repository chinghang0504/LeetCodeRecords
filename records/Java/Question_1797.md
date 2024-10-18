# [LeetCode Records](../../README.md) - Question 1797 Design Authentication Manager

### Attempt 1: Use a HashMap to store the token ID and the expired time key-value pairs
```java
class AuthenticationManager {

    private Map<String, Integer> map;
    private int timeToLive;

    public AuthenticationManager(int timeToLive) {
        this.map = new HashMap<>();
        this.timeToLive = timeToLive;
    }
    
    public void generate(String tokenId, int currentTime) {
        map.put(tokenId, currentTime + timeToLive);
    }
    
    public void renew(String tokenId, int currentTime) {
        Integer expiredTime = map.get(tokenId);
        if (expiredTime == null) {
            return;
        } else if (expiredTime <= currentTime) {
            map.remove(tokenId);
            return;
        }

        map.put(tokenId, currentTime + timeToLive);
    }
    
    public int countUnexpiredTokens(int currentTime) {
        int count = 0;
        for (Map.Entry<String, Integer> entry : map.entrySet()) {
            if (entry.getValue() > currentTime) {
                count++;
            }
        }

        return count;
    }
}

/**
 * Your AuthenticationManager object will be instantiated and called as such:
 * AuthenticationManager obj = new AuthenticationManager(timeToLive);
 * obj.generate(tokenId,currentTime);
 * obj.renew(tokenId,currentTime);
 * int param_3 = obj.countUnexpiredTokens(currentTime);
 */
```
- Runtime: 57 ms (Beats: 51.23%)
- Memory: 46.04 MB (Beats: 85.01%)

<br>
