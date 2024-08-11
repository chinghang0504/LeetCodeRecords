# [LeetCode Records](../../README.md) - Question 2383 Minimum Hours of Training to Win a Competition

### Attempt 1: Use two variables to track the current energy and experience
```java
class Solution {
    public int minNumberOfHours(int initialEnergy, int initialExperience, int[] energy, int[] experience) {
        int n = energy.length;
        int currEnergy = initialEnergy;
        int currExperience = initialExperience;
        int trainTime = 0;

        for (int i = 0; i < n; i++) {
            if (currExperience <= experience[i]) {
                trainTime += experience[i] + 1 - currExperience;
                currExperience = experience[i] + 1;
            }
            currExperience += experience[i];

            if (currEnergy <= energy[i]) {
                trainTime += energy[i] + 1 - currEnergy;
                currEnergy = energy[i] + 1;
            }
            currEnergy -= energy[i];
        }

        return trainTime;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.08 MB (Beats: 30.00%)

<br>
