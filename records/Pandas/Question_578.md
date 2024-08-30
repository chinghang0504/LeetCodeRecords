# [LeetCode Records](../../README.md) - Question 578 Get Highest Answer Rate Question

### Attempt 1: Use value_counts(), pd.merge(), fillna(), max(), min(), and pd.isnull()
```py
import pandas as pd

def get_the_question(survey_log: pd.DataFrame) -> pd.DataFrame:
    answer_actions = survey_log[survey_log['action'] == 'answer']
    answer_action_counts = answer_actions['question_id'].value_counts().reset_index()

    show_actions = survey_log[survey_log['action'] == 'show']
    show_action_counts = show_actions['question_id'].value_counts().reset_index()

    merged_df = pd.merge(answer_action_counts, show_action_counts, on='question_id', how='outer').fillna(0)
    merged_df['answer_rate'] = merged_df['count_x'] / merged_df['count_y']
    target_questiod_id = merged_df[merged_df['answer_rate'] == merged_df['answer_rate'].max()]['question_id'].min()
    if pd.isnull(target_questiod_id):
        return pd.DataFrame({
            'survey_log': []
        })
    else:
        return pd.DataFrame({
            'survey_log': [target_questiod_id]
        })
```
- Runtime: 343 ms (Beats: 96.46%)
- Memory: 71.47 MB (Beats: 26.55%)

<br>
