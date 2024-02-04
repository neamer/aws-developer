AWS has limits in place that define the maximum amount of actions that can be performed in an interval.

For intermittent errors that are caused by these limits, we should use **Exponential backoff**. 

Therefore:
- **Must only implement the retries on 5xx server errors and throttling**
- Do not implement on the 4xx client erros


Intermittent error is _a malfunction of a device or system that occurs at intervals, usually irregular, in a_ device or system that functions normally at other times.