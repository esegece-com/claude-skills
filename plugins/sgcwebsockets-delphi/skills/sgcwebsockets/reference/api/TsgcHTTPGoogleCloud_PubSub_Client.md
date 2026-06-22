# TsgcHTTPGoogleCloud_PubSub_Client

unit: sgcHTTP
Edition: Standard

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `GoogleCloudOptions: TsgcHTTP_Google_Cloud_Options` | [TsgcHTTP_Google_Cloud_Options](../types/TsgcHTTP_Google_Cloud_Options.md) | `__property TsgcHTTP_Google_Cloud_Options * GoogleCloudOptions;` |
| `LogFile: TsgcGoogleCloudLogFile` | [TsgcGoogleCloudLogFile](../types/TsgcGoogleCloudLogFile.md) | `__property TsgcGoogleCloudLogFile * LogFile;` |
| `TLSOptions: TsgcHTTPTLS_Options` | [TsgcHTTPTLS_Options](../types/TsgcHTTPTLS_Options.md) | `__property TsgcHTTPTLS_Options * TLSOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAuthToken: TsgcOnAuthToken` | [TsgcOnAuthToken](../types/TsgcOnAuthToken.md) | `__property TsgcOnAuthToken * OnAuthToken;` |
| `OnAuthTokenError: TsgcOnAuthTokenError` | [TsgcOnAuthTokenError](../types/TsgcOnAuthTokenError.md) | `__property TsgcOnAuthTokenError * OnAuthTokenError;` |

## Methods

Delphi

```pascal
function GetIamPolicy(const aResource: string): string;
function SetIamPolicy(const aResource: string): string;
function TestIamPermissions(const aResource: string; aPermissions: TStrings): string;
function CreateSnapshot(const aProject, aSnapshot, aSubscription: string; const aLabels: TStrings = nil): string;
function DeleteSnapshot(const aProject, aSnapshot: string): string;
function ListSnapshots(const aProject: string; aPageSize: Integer = 0; aPageToken: String = ''): string;
function Acknowledge(const aProject, aSubscription, aAckId: string): string;
function CreateSubscription(const aProject, aSubscription, aTopic: string; const aPushEndPoint: String = ''; aAckDeadlineSeconds: Integer = 0; aRetainAckedMessages: Boolean = False; aMessageRetentionDuration: String = '604800s'; const aLabels: TStrings = nil; aExpirationPolicy: String = '2678400s'; const aFilter: String = ''; const aDeadLetterTopic: String = ''; aMaxDeliveryAttempts: Integer = 5; aMinBackoff: String = ''; aMaxBackoff: String = ''; aEnableMessageOrdering: Boolean = False; aDetached: Boolean = False; aEnableExactlyOnceDelivery: Boolean = False; const aTopicMessageRetentionDuration: String = ''; const aBigQueryTable: String = ''; aUseTopicSchema: Boolean = False): string;
function DeleteSubscripton(const aProject, aSubscription: string): string;
function GetSubscription(const aProject, aSubscription: string): string;
function ListSubscriptions(const aProject: string; aPageSize: Integer = 0; aPageToken: String = ''): string;
function ModifyAckDeadlineSubscription(const aProject, aSubscription: string; aAckIds: TStrings; aAckDeadlineSeconds: Integer = 0): string;
function ModifyPushConfigSubscription(const aProject, aSubscription: string; const aPushEndPoint: string = ''; const aAttributes: TStrings = nil; const aServiceAccountEmail: String = ''; aAudience: String = ''): string;
function Pull(const aProject, aSubscription: string; aMaxMessages: Integer = MaxInt): string;
function Seek(const aProject, aSubscription: string; aTimeUTC: String; const aSnapshot: String): string;
function PatchSubscription(const aProject, aSubscription: string; const aBody: string; const aUpdateMask: string = ''): string;
function DetachSubscription(const aProject, aSubscription: string): string;
function CreateTopic(const aProject, aTopic: string): string;
function DeleteTopic(const aProject, aTopic: string): string;
function GetTopic(const aProject, aTopic: string): string;
function ListTopics(const aProject: string; aPageSize: Integer = 0; aPageToken: String = ''): string;
function Publish(const aProject, aTopic, aMessage: string; const aAttributes: TStrings = nil; const aOrderingKey: string = ''): string;
function PatchTopic(const aProject, aTopic: string; const aBody: string; const aUpdateMask: string = ''): string;
function ListTopicSnapshots(const aProject, aTopic: string; aPageSize: Integer = 0; aPageToken: String = ''): string;
function ListTopicSubscriptions(const aProject, aTopic: string; aPageSize: Integer = 0; aPageToken: String = ''): string;
procedure LoadSettingsFromFile(const aFileName: String);
procedure Clear;
function RefreshToken(const aToken: string): boolean;
```

C++Builder

```cpp
UnicodeString __fastcall GetIamPolicy(const UnicodeString aResource);
UnicodeString __fastcall SetIamPolicy(const UnicodeString aResource);
UnicodeString __fastcall TestIamPermissions(const UnicodeString aResource, TStrings * aPermissions);
UnicodeString __fastcall CreateSnapshot(const UnicodeString aProject, const UnicodeString aSnapshot, const UnicodeString aSubscription, const TStrings * aLabels = nil);
UnicodeString __fastcall DeleteSnapshot(const UnicodeString aProject, const UnicodeString aSnapshot);
UnicodeString __fastcall ListSnapshots(const UnicodeString aProject, int aPageSize = 0, UnicodeString aPageToken = '');
UnicodeString __fastcall Acknowledge(const UnicodeString aProject, const UnicodeString aSubscription, const UnicodeString aAckId);
UnicodeString __fastcall CreateSubscription(const UnicodeString aProject, const UnicodeString aSubscription, const UnicodeString aTopic, const UnicodeString aPushEndPoint = '', int aAckDeadlineSeconds = 0, bool aRetainAckedMessages = False, UnicodeString aMessageRetentionDuration = '604800s', const TStrings * aLabels = nil, UnicodeString aExpirationPolicy = '2678400s', const UnicodeString aFilter = '', const UnicodeString aDeadLetterTopic = '', int aMaxDeliveryAttempts = 5, UnicodeString aMinBackoff = '', UnicodeString aMaxBackoff = '', bool aEnableMessageOrdering = False, bool aDetached = False, bool aEnableExactlyOnceDelivery = False, const UnicodeString aTopicMessageRetentionDuration = '', const UnicodeString aBigQueryTable = '', bool aUseTopicSchema = False);
UnicodeString __fastcall DeleteSubscripton(const UnicodeString aProject, const UnicodeString aSubscription);
UnicodeString __fastcall GetSubscription(const UnicodeString aProject, const UnicodeString aSubscription);
UnicodeString __fastcall ListSubscriptions(const UnicodeString aProject, int aPageSize = 0, UnicodeString aPageToken = '');
UnicodeString __fastcall ModifyAckDeadlineSubscription(const UnicodeString aProject, const UnicodeString aSubscription, TStrings * aAckIds, int aAckDeadlineSeconds = 0);
UnicodeString __fastcall ModifyPushConfigSubscription(const UnicodeString aProject, const UnicodeString aSubscription, const UnicodeString aPushEndPoint = '', const TStrings * aAttributes = nil, const UnicodeString aServiceAccountEmail = '', UnicodeString aAudience = '');
UnicodeString __fastcall Pull(const UnicodeString aProject, const UnicodeString aSubscription, int aMaxMessages = MaxInt);
UnicodeString __fastcall Seek(const UnicodeString aProject, const UnicodeString aSubscription, UnicodeString aTimeUTC, const UnicodeString aSnapshot);
UnicodeString __fastcall PatchSubscription(const UnicodeString aProject, const UnicodeString aSubscription, const UnicodeString aBody, const UnicodeString aUpdateMask = '');
UnicodeString __fastcall DetachSubscription(const UnicodeString aProject, const UnicodeString aSubscription);
UnicodeString __fastcall CreateTopic(const UnicodeString aProject, const UnicodeString aTopic);
UnicodeString __fastcall DeleteTopic(const UnicodeString aProject, const UnicodeString aTopic);
UnicodeString __fastcall GetTopic(const UnicodeString aProject, const UnicodeString aTopic);
UnicodeString __fastcall ListTopics(const UnicodeString aProject, int aPageSize = 0, UnicodeString aPageToken = '');
UnicodeString __fastcall Publish(const UnicodeString aProject, const UnicodeString aTopic, const UnicodeString aMessage, const TStrings * aAttributes = nil, const UnicodeString aOrderingKey = '');
UnicodeString __fastcall PatchTopic(const UnicodeString aProject, const UnicodeString aTopic, const UnicodeString aBody, const UnicodeString aUpdateMask = '');
UnicodeString __fastcall ListTopicSnapshots(const UnicodeString aProject, const UnicodeString aTopic, int aPageSize = 0, UnicodeString aPageToken = '');
UnicodeString __fastcall ListTopicSubscriptions(const UnicodeString aProject, const UnicodeString aTopic, int aPageSize = 0, UnicodeString aPageToken = '');
void __fastcall LoadSettingsFromFile(const UnicodeString aFileName);
void __fastcall Clear();
bool __fastcall RefreshToken(const UnicodeString aToken);
```

