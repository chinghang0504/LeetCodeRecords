# [LeetCode Records](../../README.md) - Question 535 Encode and Decode TinyURL

### Attempt 1: Return the same string
```java
public class Codec {

    // Encodes a URL to a shortened URL.
    public String encode(String longUrl) {
        return longUrl;
    }

    // Decodes a shortened URL to its original URL.
    public String decode(String shortUrl) {
        return shortUrl;
    }
}

// Your Codec object will be instantiated and called as such:
// Codec codec = new Codec();
// codec.decode(codec.encode(url));
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.72 MB (Beats: 68.63%)

<br>
