# TsgcHTTPAWS_SQS_Client - Example

Usage of `TsgcHTTPAWS_SQS_Client` extracted from the **20.HTTP_Protocol/04.AWS/01.Amazon_SQS** demo. See the full project for context.

API reference: [TsgcHTTPAWS_SQS_Client](../reference/api/TsgcHTTPAWS_SQS_Client.md)
Source demo: `20.HTTP_Protocol/04.AWS/01.Amazon_SQS` (file `FAmazonSQS.pas`)

```pascal
vURL := SQS.CreateQueue(txtQueueName.Text);
SQS.AWSOptions.Region := txtRegion.Text;
SQS.AWSOptions.AccessKey := txtAccessKey.Text;
SQS.AWSOptions.SecretKey := txtSecretKey.Text;
```

