# cloudwatch
- log insight 內
- 可以下語法去查詢 Log。
    ```
    fields @timestamp, @message, @logStream
    |filter @message like 'ALERT' or @message like 'EXCEPTION' or @message like 'rejected' or @message like '派送異常'
    | sort @timestamp desc
    ```

# Lambda
## 測試
	可以直接去 Trigger Lambda Function。

# Eventbridge
## Enable/Disable
	可以去切換

# S3
## 利用 aws cli 把 s3 object copy 到本機
```bash
# 先去設置要連結哪個 aws
aws configure 
# download 下來
aws s3 sync s3://private.lcy.clinic/hibaby/0073701/2023-03-13/ /Users/liaoguanjie/Downloads/folder
```

