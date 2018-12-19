# lambda_cloudwatchlogs-s3

![cloudwatchlogs](https://user-images.githubusercontent.com/5633085/49983430-06e31700-ffa6-11e8-9309-742f8dd7b6cd.jpg)


## Requirement
- Synchronize the log that causes RDS general-log, slowquery-log to be read by cloudwatch logs to s3

## How to use

### RDS/logs

- Check all logs to reflect on cloudwatch logs.

Export of logs  

 - Audit log
 - Erotic
 - General log
 - Slow Quorig

・ Parameter group  

 - slow_query_log → 1
 - general_log → 1
 - long_query_time → 5
 - log_output -> FILE

### AWS/roles

cloudwatchlogs Full Access  

### S3 policy

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "logs.ap-northeast-1.amazonaws.com"
            },
            "Action": "s3:GetBucketAcl",
            "Resource": "arn:aws:s3:::xxxxxxxxxxxxxxx"
        },
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "xxx.ap-northeast-1.amazonaws.com"
            },
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::xxxxxxxxxxxxxxxxx/*",
            "Condition": {
                "StringEquals": {
                    "s3:x-amz-acl": "bucket-owner-full-control"
                }
            }
        }
    ]
}
```

### Lambda

Python 2.7

### CloudwatchLogs event

```
JST: 0 15 * * ? *
```

## Result

![49977317-3fc0c300-ff89-11e8-8261-24b4c896f8b0](https://user-images.githubusercontent.com/5633085/49983674-7f96a300-ffa7-11e8-994a-56d3178e84ef.png)

