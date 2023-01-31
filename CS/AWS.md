#cs #aws

# cloudwatch
- log insight 內
- 可以下語法去查詢 Log。
    ```
    fields @timestamp, @message, @logStream
    |filter @message like 'ALERT' or @message like 'EXCEPTION' or @message like 'rejected' or @message like '派送異常'
    | sort @timestamp desc
    ```