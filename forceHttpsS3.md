In order to ALWAYS force https for data during transit this should be added to every s3 bucket

If this is not set we cannot be sure during transit the files are always encrypted because the client could try and access the resource via http and then that data will be transmitted in plain text

```
{
    "Statement": [
        {
            "Action": "s3:*",
            "Effect": "Deny",
            "Principal": "*",
            "Resource": "arn:aws:s3:::bucketname/*",
            "Condition": {
                "Bool": {
                    "aws:SecureTransport": false
                }
            }
        }
    ]
}
```
