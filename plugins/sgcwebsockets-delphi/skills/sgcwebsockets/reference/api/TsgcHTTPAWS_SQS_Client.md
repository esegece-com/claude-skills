# TsgcHTTPAWS_SQS_Client

unit: sgcHTTP
Edition: requires SGC_AWS

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `AWSOptions: TsgcHTTP_Amazon_AWS_Options` | [TsgcHTTP_Amazon_AWS_Options](../types/TsgcHTTP_Amazon_AWS_Options.md) | `__property TsgcHTTP_Amazon_AWS_Options * AWSOptions;` |
| `LogFile: TsgcAWSLogFile` | [TsgcAWSLogFile](../types/TsgcAWSLogFile.md) | `__property TsgcAWSLogFile * LogFile;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `EndPoint: String (read-only)` | `String` | `__property UnicodeString EndPoint /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSQSBeforeRequest: TsgcOnAWSSQSBeforeRequest` | [TsgcOnAWSSQSBeforeRequest](../types/TsgcOnAWSSQSBeforeRequest.md) | `__property TsgcOnAWSSQSBeforeRequest * OnSQSBeforeRequest;` |
| `OnSQSResponse: TsgcOnAWSSQSResponse` | [TsgcOnAWSSQSResponse](../types/TsgcOnAWSSQSResponse.md) | `__property TsgcOnAWSSQSResponse * OnSQSResponse;` |
| `OnSQSError: TsgcOnAWSSQSError` | [TsgcOnAWSSQSError](../types/TsgcOnAWSSQSError.md) | `__property TsgcOnAWSSQSError * OnSQSError;` |

## Methods

Delphi

```pascal
procedure SendMessageBatch(const aQueueName: String; aRequests: TsgcSQSSendMessageRequests; var aResponses: TsgcSQSSendMessageResponses);
function ReceiveMessage(const aQueueName: String; var aResponses: TsgcSQSReceiveMessageResponses): Boolean;
function ChangeMessageVisibility(const aQueueName, aReceiptHandle: String; VisibilityTimeout: Integer): Boolean;
function ChangeMessageVisibilityBatch(const aQueueName: String; const aRequests: TsgcSQSChangeMessageVisibilityBatchRequests; var aResponseIds: TStringList): Boolean;
function DeleteMessage(const aQueueName, aReceiptHandle: String): Boolean;
procedure DeleteMessageBatch(const aQueueName: String; aDeleteBatchItems: TsgcSQSDeleteMessageBatchRequestItems);
function GetQueueURL(const aQueueName: String): String;
function CreateQueue(const aQueueName: String): string;
function DeleteQueue(const aQueueName: String): Boolean;
function ListQueues(var Queues: TStringList; const aQueueNamePrefix: String = ''): Boolean;
function ListQueueTags(const aQueueName: String; var Tags: TsgcSQSTags): Boolean;
function GetQueueAttributes(const aQueueName: String; var Attributes: TsgcSQSAttributes): Boolean;
function SetQueueAttributes(const aQueueName: String; const aAttributes: TsgcSQSAttributes): Boolean;
function PurgueQueue(const aQueueName: String): Boolean;
function TagQueue(const aQueueName: String; aTags: TsgcSQSTags) : Boolean;
function UnTagQueue(const aQueueName: String; aTags: TStringList) : Boolean;
function AddPermission(const aQueueName, aLabel: String; const aPermissions: TsgcSQSPermissions): Boolean;
function RemovePermission(const aQueueName, aLabel: String): Boolean;
function ListDeadLetterSourceQueues(const aQueueName: String; aQueueURLs: TStringList): Boolean;
function GetURL(const aURL: String; var aResponse, aError: String): Boolean;
function PostURL(const aURL: String; const aBody: TStringStream; var aResponse: TStream; var aError: String): Boolean;
```

C++Builder

```cpp
void __fastcall SendMessageBatch(const UnicodeString aQueueName, TsgcSQSSendMessageRequests * aRequests, TsgcSQSSendMessageResponses * &aResponses);
bool __fastcall ReceiveMessage(const UnicodeString aQueueName, TsgcSQSReceiveMessageResponses * &aResponses);
bool __fastcall ChangeMessageVisibility(const UnicodeString aQueueName, const UnicodeString aReceiptHandle, int VisibilityTimeout);
bool __fastcall ChangeMessageVisibilityBatch(const UnicodeString aQueueName, const TsgcSQSChangeMessageVisibilityBatchRequests * aRequests, TStringList * &aResponseIds);
bool __fastcall DeleteMessage(const UnicodeString aQueueName, const UnicodeString aReceiptHandle);
void __fastcall DeleteMessageBatch(const UnicodeString aQueueName, TsgcSQSDeleteMessageBatchRequestItems * aDeleteBatchItems);
UnicodeString __fastcall GetQueueURL(const UnicodeString aQueueName);
UnicodeString __fastcall CreateQueue(const UnicodeString aQueueName);
bool __fastcall DeleteQueue(const UnicodeString aQueueName);
bool __fastcall ListQueues(TStringList * &Queues, const UnicodeString aQueueNamePrefix = '');
bool __fastcall ListQueueTags(const UnicodeString aQueueName, TsgcSQSTags * &Tags);
bool __fastcall GetQueueAttributes(const UnicodeString aQueueName, TsgcSQSAttributes * &Attributes);
bool __fastcall SetQueueAttributes(const UnicodeString aQueueName, const TsgcSQSAttributes * aAttributes);
bool __fastcall PurgueQueue(const UnicodeString aQueueName);
bool __fastcall TagQueue(const UnicodeString aQueueName, TsgcSQSTags * aTags);
bool __fastcall UnTagQueue(const UnicodeString aQueueName, TStringList * aTags);
bool __fastcall AddPermission(const UnicodeString aQueueName, const UnicodeString aLabel, const TsgcSQSPermissions * aPermissions);
bool __fastcall RemovePermission(const UnicodeString aQueueName, const UnicodeString aLabel);
bool __fastcall ListDeadLetterSourceQueues(const UnicodeString aQueueName, TStringList * aQueueURLs);
bool __fastcall GetURL(const UnicodeString aURL, UnicodeString &aResponse, UnicodeString &aError);
bool __fastcall PostURL(const UnicodeString aURL, const TStringStream * aBody, TStream * &aResponse, UnicodeString &aError);
```

