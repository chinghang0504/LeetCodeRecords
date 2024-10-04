# [LeetCode Records](../../README.md) - Question 2491 Divide Players Into Teams of Equal Skill

### Attempt 1: Use Arrays.sort() to skill first
```java
class Solution {
    public long dividePlayers(int[] skill) {
        Arrays.sort(skill);

        int firstTeamVal = skill[0] + skill[skill.length - 1];
        long totalChemistry = skill[0] * skill[skill.length - 1];
        for (int i = 1; i < skill.length / 2; i++) {
            int teamVal = skill[i] + skill[skill.length - i - 1];
            if (teamVal != firstTeamVal) {
                return -1;
            }

            totalChemistry += skill[i] * skill[skill.length - i - 1];
        }

        return totalChemistry;
    }
}
```
- Runtime: 16 ms (Beats: 61.21%)
- Memory: 57.64 MB (Beats: 52.90%)

<br>
