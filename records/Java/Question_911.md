# [LeetCode Records](../../README.md) - Question 911 Online Election

### Attempt 1: Use binary search to search the leading person at time t
```java
class TopVotedCandidate {

    private int n;
    private int[] times;
    private int[] leadingPersons;
    
    public TopVotedCandidate(int[] persons, int[] times) {
        this.n = persons.length;
        this.times = times;
        this.leadingPersons = new int[n];

        int[] personCounts = new int[n];
        int maxCount = 0;
        int maxCountPerson = 0;
        for (int i = 0; i < n; i++) {
            personCounts[persons[i]]++;
            if (personCounts[persons[i]] > maxCount) {
                maxCount = personCounts[persons[i]];
                maxCountPerson = persons[i];
            } else if (personCounts[persons[i]] == maxCount) {
                maxCountPerson = persons[i];
            }

            leadingPersons[i] = maxCountPerson;
        }
    }
    
    public int q(int t) {
        int left = 0;
        int right = n - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (t == times[mid]) {
                return leadingPersons[mid];
            } else if (t > times[mid]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return leadingPersons[left - 1];
    }
}

/**
 * Your TopVotedCandidate object will be instantiated and called as such:
 * TopVotedCandidate obj = new TopVotedCandidate(persons, times);
 * int param_1 = obj.q(t);
 */
```
- Runtime: 56 ms (Beats: 91.55%)
- Memory: 55.71 MB (Beats: 56.81%)

<br>
