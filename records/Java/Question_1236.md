# [LeetCode Records](../../README.md) - Question 1236 Web Crawler

### Attempt 1: Use a HashSet to store the searched urls
```java
/**
 * // This is the HtmlParser's API interface.
 * // You should not implement it, or speculate about its implementation
 * interface HtmlParser {
 *     public List<String> getUrls(String url) {}
 * }
 */

class Solution {
    public List<String> crawl(String startUrl, HtmlParser htmlParser) {
        Set<String> searchedUrls = new HashSet<>();
        String domainUrl = getDomainUrl(startUrl);

        List<String> urls = new ArrayList<>();
        urls.add(startUrl);

        while (!urls.isEmpty()) {
            List<String> nextUrls = new ArrayList<>();

            for (String url : urls) {
                searchedUrls.add(url);

                for (String nextUrl : htmlParser.getUrls(url)) {
                    if (!searchedUrls.contains(nextUrl) && nextUrl.startsWith(domainUrl)) {
                        nextUrls.add(nextUrl);
                    }
                }
            }

            urls = nextUrls;
        }
        

        return new ArrayList<>(searchedUrls);
    }

    private String getDomainUrl(String url) {
        int len = url.length();
        int i = 7;
        while (i < len && url.charAt(i) != '/') {
            i++;
        }
        return url.substring(0, i);
    }
}
```
- Runtime: 40 ms (Beats: 13.20%)
- Memory: 52.18 MB (Beats: 10.66%)

<br>
