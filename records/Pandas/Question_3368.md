# [LeetCode Records](../../README.md) - Question 3368 First Letter Capitalization

### Attempt 1: Use apply() to convert the text
```py
import pandas as pd

def convertText(original):
    converted_text = ""

    is_first_ch = True
    for ch in original:
        if ch.isalpha():
            if is_first_ch:
                is_first_ch = False
                converted_text += ch.upper()
            else:
                converted_text += ch.lower()
        else:
            converted_text += ch
            is_first_ch = True
    
    return converted_text


def process_text(user_content: pd.DataFrame) -> pd.DataFrame:
    user_content['converted_text'] = user_content['content_text'].apply(convertText)
    user_content = user_content.rename(columns={'content_text': 'original_text'})
    return user_content
```
- Runtime: 284 ms (Beats: 82.61%)
- Memory: 66.24 MB (Beats: 41.30%)

<br>
