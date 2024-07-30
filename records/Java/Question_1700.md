# [LeetCode Records](../../README.md) - Question 1700 Number of Students Unable to Eat Lunch

### Attempt 1: Use two LinkedList to track students and sandwiches
```java
class Solution {
    public int countStudents(int[] students, int[] sandwiches) {
        List<Integer> studentList = new LinkedList<>();
        List<Integer> sandwichList = new LinkedList<>();

        for (int student : students) {
            studentList.add(student);
        }
        for (int sandwich : sandwiches) {
            sandwichList.add(sandwich);
        }

        while (true) {
            List<Integer> nextStudentList = new LinkedList<>();
            for (Integer student : studentList) {
                if (student == sandwichList.getFirst()) {
                    sandwichList.removeFirst();
                } else {
                    nextStudentList.addLast(student);
                }
            }

            if (studentList.size() == nextStudentList.size()) {
                break;
            } else {
                studentList = nextStudentList;
            }
        }

        return studentList.size();
    }
}
```
- Runtime: 2 ms (Beats: 41.96%)
- Memory: 41.53 MB (Beats: 30.76%)

<br>
