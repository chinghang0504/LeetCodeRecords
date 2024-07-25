# [LeetCode Records](../../README.md) - Question 1356 Sort Integers by The Number of 1 Bits

### Attempt 1: Use a HashMap to store the number of 1
```java
class Solution {
    public int[] sortByBits(int[] arr) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int num : arr) {
            map.put(num, getBits(num));
        }

        Integer[] integerArray = Arrays.stream(arr).boxed().toArray(Integer[]::new);
        Arrays.sort(integerArray, new Comparator<Integer>(){
            @Override
            public int compare(Integer o1, Integer o2) {
                int count1 = map.get(o1);
                int count2 = map.get(o2);

                if (count1 < count2) {
                    return -1;
                } else if (count1 > count2) {
                    return 1;
                }

                if (o1 < o2) {
                    return -1;
                } else if (o1 > o2) {
                    return 1;
                } else {
                    return 0;
                }
            }
        });

        return Arrays.stream(integerArray).mapToInt(Integer::intValue).toArray();
    }

    private int getBits(int num) {
        int count = 0;

        while (num > 0) {
            count += num & 1;
            num >>>= 1;
        }

        return count;
    }
}
```
- Runtime: 16 ms (Beats: 22.27%)
- Memory: 44.92 MB (Beats: 11.44%)

<br>
