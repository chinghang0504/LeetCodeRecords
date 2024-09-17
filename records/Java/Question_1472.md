# [LeetCode Records](../../README.md) - Question 1472 Design Browser History

### Attempt 1: Use a LinkedList to store the urls
```java
class BrowserHistory {

    private List<String> urlList;
    private int currStep;

    public BrowserHistory(String homepage) {
        urlList = new LinkedList<>();
        urlList.add(homepage);
        currStep = 1;
    }
    
    public void visit(String url) {
        while (currStep != urlList.size()) {
            urlList.removeLast();
        }
        
        urlList.add(url);
        currStep++;
    }
    
    public String back(int steps) {
        int nextStep = currStep - steps;
        if (nextStep < 1) {
            nextStep =  1;
        }

        currStep = nextStep;
        return urlList.get(currStep - 1);
    }
    
    public String forward(int steps) {
        int nextStep = currStep + steps;
        if (nextStep > urlList.size()) {
            nextStep = urlList.size();
        }
        
        currStep = nextStep;
        return urlList.get(currStep - 1);
    }
}

/**
 * Your BrowserHistory object will be instantiated and called as such:
 * BrowserHistory obj = new BrowserHistory(homepage);
 * obj.visit(url);
 * String param_2 = obj.back(steps);
 * String param_3 = obj.forward(steps);
 */
```
- Runtime: 51 ms (Beats: 65.80%)
- Memory: 50.72 MB (Beats: 48.24%)

<br>
