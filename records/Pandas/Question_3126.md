# [LeetCode Records](../../README.md) - Question 3126 Server Utilization Time

### Attempt 1: Use pd.to_datatime(), sort_values(), groupby(), apply(), sum(), days, and shift()
```py
import pandas as pd

def getRuntime(df):
    df['next_status_time'] = df['status_time'].shift(-1)
    df = df[df['session_status'] == 'start']
    df['diff_time'] = df['next_status_time'] - df['status_time']
    return df['diff_time'].sum()
    

def server_utilization_time(servers: pd.DataFrame) -> pd.DataFrame:
    servers['status_time'] = pd.to_datetime(servers['status_time'])
    sorted_servers = servers.sort_values(['server_id', 'status_time'])
    
    total_uptime_days = sorted_servers.groupby('server_id').apply(getRuntime).sum().days
    return pd.DataFrame({
        'total_uptime_days': [total_uptime_days]
    })
```
- Runtime: 437 ms (Beats: 68.97%)
- Memory: 70.76 MB (Beats: 34.48%)

<br>
