# [LeetCode Records](../../README.md) - Question 3421 Find Students Who Improved

### Attempt 1: Use pd.merge() to get the scores from the first exam date and the last exam date
```py
import pandas as pd

def find_students_who_improved(scores: pd.DataFrame) -> pd.DataFrame:
    exam_date_groups = scores.groupby(['student_id', 'subject'])['exam_date']
    first_exam_dates = exam_date_groups.min().reset_index()
    last_exam_dates = exam_date_groups.max().reset_index()
    
    first_scores = pd.merge(scores, first_exam_dates, on=['student_id', 'subject', 'exam_date']).rename(columns={'score': 'first_score', 'exam_date': 'first_exam_date'})
    last_scores = pd.merge(scores, last_exam_dates, on=['student_id', 'subject', 'exam_date']).rename(columns={'score': 'latest_score', 'exam_date': 'latest_exam_date'})
    scores = pd.merge(first_scores, last_scores, on=['student_id', 'subject'])
    
    ans = scores[(scores['first_exam_date'] != scores['latest_exam_date']) & (scores['first_score'] < scores['latest_score'])]
    ans = ans.sort_values(['student_id', 'subject'])[['student_id', 'subject', 'first_score', 'latest_score']]
    return ans

```
- Runtime: 574 ms (Beats: 100.00%)
- Memory: 68.59 MB (Beats: 100.00%)

<br>
