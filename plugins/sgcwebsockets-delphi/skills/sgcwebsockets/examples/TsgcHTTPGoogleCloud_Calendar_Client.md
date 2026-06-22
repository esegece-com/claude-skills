# TsgcHTTPGoogleCloud_Calendar_Client - Example

Usage of `TsgcHTTPGoogleCloud_Calendar_Client` extracted from the **20.HTTP_Protocol/03.Google/02.Google_Calendar** demo. See the full project for context.

API reference: [TsgcHTTPGoogleCloud_Calendar_Client](../reference/api/TsgcHTTPGoogleCloud_Calendar_Client.md)
Source demo: `20.HTTP_Protocol/03.Google/02.Google_Calendar` (file `FGoogleCalendar.pas`)

```pascal
procedure TFRMGoogleCalendar.btnConnectClick(Sender: TObject);
  begin
  GoogleCalendar.GoogleCloudOptions.OAuth2.ClientId := txtClientId.Text;
  GoogleCalendar.GoogleCloudOptions.OAuth2.ClientSecret := txtClientSecret.Text;
  
  DoLoadCalendars;
  end;

procedure TFRMGoogleCalendar.btnExecuteACLClick(Sender: TObject);
  var
  oResource: TsgcGoogleCalendarResource_ACL;
  oWatch: TsgcGoogleCalendarWatch;
  begin
  DoAuthenticate;
  
  case cboACL.ItemIndex of
  0:
  DoLog(GoogleCalendar.ACL_Delete(txtACLCalendarId.Text,
  txtACLRuleId.Text));
  1:
  DoLog(GoogleCalendar.ACL_Get(txtACLCalendarId.Text, txtACLRuleId.Text));
  2:
  begin
  oResource := TsgcGoogleCalendarResource_ACL.Create;
  Try
  oResource.Role := gcrOwner;
  oResource.Scope._type := gcstDefault;
  DoLog(GoogleCalendar.ACL_Insert(txtACLCalendarId.Text, oResource));
  Finally
  oResource.Free;
  End;
  end;

procedure TFRMGoogleCalendar.btnExecuteCalendarClick(Sender: TObject);
  var
  oResource: TsgcGoogleCalendarResource_Calendar;
  begin
  case cboCalendar.ItemIndex of
  0:
  DoLog(GoogleCalendar.Calendar_Clear(txtCalendarId.Text));
  1:
  DoLog(GoogleCalendar.Calendar_Delete(txtCalendarId.Text));
  2:
  DoLog(GoogleCalendar.Calendar_Get(txtCalendarId.Text));
  3:
  begin
  oResource := TsgcGoogleCalendarResource_Calendar.Create;
  Try
  oResource.Summary := InputBox('Summary',
  'Set the description of New Calendar', '');
  DoLog(GoogleCalendar.Calendar_Insert(oResource));
  Finally
  oResource.Free;
  End;
  end;

procedure TFRMGoogleCalendar.btnExecuteCalendarListClick(Sender: TObject);
  var
  oResource: TsgcGoogleCalendarResource_CalendarList;
  oWatch: TsgcGoogleCalendarWatch;
```

