# TsgcHTTPGoogleCloud_Calendar_Client - Example

Full source of `FGoogleCalendar.pas` from the **20.HTTP_Protocol/03.Google/02.Google_Calendar** demo, which uses `TsgcHTTPGoogleCloud_Calendar_Client`.

API reference: [TsgcHTTPGoogleCloud_Calendar_Client](../reference/api/TsgcHTTPGoogleCloud_Calendar_Client.md)
Source demo: `20.HTTP_Protocol/03.Google/02.Google_Calendar` (file `FGoogleCalendar.pas`)

```pascal
unit FGoogleCalendar;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, DateUtils, sgcBase_Classes, sgcHTTP_Google_Cloud,
  sgcHTTP_Google_Calendar, sgcHTTP, ComCtrls, UITypes, System.ImageList,
  Vcl.ImgList;

type
  TFRMGoogleCalendar = class(TForm)
    memoLog: TMemo;
    pnlTop: TPanel;
    GoogleCalendar: TsgcHTTPGoogleCloud_Calendar_Client;
    pnlAPI: TPanel;
    PageControl1: TPageControl;
    tabACL: TTabSheet;
    btnExecuteACL: TButton;
    txtACLCalendarId: TEdit;
    txtACLRuleId: TEdit;
    Label1: TLabel;
    Label4: TLabel;
    cboACL: TComboBox;
    tabCalendarList: TTabSheet;
    btnExecuteCalendarList: TButton;
    cboCalendarList: TComboBox;
    txtCalendarListCalendarId: TEdit;
    Label5: TLabel;
    tabCalendar: TTabSheet;
    Label6: TLabel;
    txtCalendarId: TEdit;
    btnExecuteCalendar: TButton;
    cboCalendar: TComboBox;
    tabChannel: TTabSheet;
    Label7: TLabel;
    txtChannelId: TEdit;
    Label8: TLabel;
    txtChannelResourceId: TEdit;
    btnExecuteChannel: TButton;
    tabColor: TTabSheet;
    btnExecuteColor: TButton;
    tabEvent: TTabSheet;
    Label9: TLabel;
    txtEventCalendarId: TEdit;
    Label10: TLabel;
    txtEventId: TEdit;
    cboEvent: TComboBox;
    btnExecuteEvent: TButton;
    tabFreebusy: TTabSheet;
    btnExecuteFreebusy: TButton;
    dateFromFreeBusy: TDateTimePicker;
    dateToFreeBusy: TDateTimePicker;
    tabSettings: TTabSheet;
    tabExecuteSettings: TButton;
    cboSettings: TComboBox;
    pageBody: TPageControl;
    tabAPI: TTabSheet;
    tabDemo: TTabSheet;
    listCalendars: TListBox;
    groupCalendars: TGroupBox;
    Label11: TLabel;
    btnCalendarNew: TButton;
    btnCalendarEdit: TButton;
    btnCalendarDelete: TButton;
    btnCalendarRefresh: TButton;
    GroupBox2: TGroupBox;
    listEvents: TListBox;
    chkEventByDate: TCheckBox;
    dateFromEvents: TDateTimePicker;
    dateToEvents: TDateTimePicker;
    btnEventEdit: TButton;
    btnEventNew: TButton;
    btnEventDelete: TButton;
    btnEventRefresh: TButton;
    txtCalendarNextSyncToken: TEdit;
    Label12: TLabel;
    Label13: TLabel;
    txtCalendarSyncToken: TEdit;
    Label14: TLabel;
    txtEventNextSyncToken: TEdit;
    txtEventSyncToken: TEdit;
    Label15: TLabel;
    cboEventsOrderBy: TComboBox;
    Label16: TLabel;
    btnCalendarsChanges: TButton;
    btnEventsChanged: TButton;
    ImageList1: TImageList;
    Panel1: TPanel;
    Timer1: TTimer;
    PageControl2: TPageControl;
    tabOAuth2: TTabSheet;
    Label2: TLabel;
    Label3: TLabel;
    RadioGroup2: TRadioGroup;
    txtClientId: TEdit;
    txtClientSecret: TEdit;
    tabServiceAccount: TTabSheet;
    Label17: TLabel;
    Label18: TLabel;
    Label19: TLabel;
    txtJWTClientEmail: TEdit;
    txtJWTPrivateKeyId: TEdit;
    memoJWTPrivateKey: TMemo;
    btnLoadJSONSettings: TButton;
    Label20: TLabel;
    txtJWTSubject: TEdit;
    procedure FormCreate(Sender: TObject);
    procedure btnCalendarDeleteClick(Sender: TObject);
    procedure btnCalendarEditClick(Sender: TObject);
    procedure btnCalendarNewClick(Sender: TObject);
    procedure btnCalendarRefreshClick(Sender: TObject);
    procedure btnCalendarsChangesClick(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnEventDeleteClick(Sender: TObject);
    procedure btnEventEditClick(Sender: TObject);
    procedure btnEventNewClick(Sender: TObject);
    procedure btnEventRefreshClick(Sender: TObject);
    procedure btnEventsChangedClick(Sender: TObject);
    procedure btnExecuteACLClick(Sender: TObject);
    procedure btnExecuteCalendarClick(Sender: TObject);
    procedure btnExecuteCalendarListClick(Sender: TObject);
    procedure btnExecuteChannelClick(Sender: TObject);
    procedure btnExecuteColorClick(Sender: TObject);
    procedure btnExecuteEventClick(Sender: TObject);
    procedure btnExecuteFreebusyClick(Sender: TObject);
    procedure btnGetCalendarsClick(Sender: TObject);
    procedure btnLoadJSONSettingsClick(Sender: TObject);
    procedure cboEventsOrderByChange(Sender: TObject);
    procedure chkEventByDateClick(Sender: TObject);
    procedure dateFromEventsChange(Sender: TObject);
    procedure dateToEventsChange(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure GoogleCalendarAuthToken(Sender: TObject;
      const TokenType, Token, Data: string);
    procedure GoogleCalendarError(Sender: TObject; const aError:
        TsgcGoogleCalendarError);
    procedure listCalendarsClick(Sender: TObject);
    procedure listCalendarsDblClick(Sender: TObject);
    procedure listEventsDblClick(Sender: TObject);
    procedure memoJWTPrivateKeyChange(Sender: TObject);
    procedure tabExecuteSettingsClick(Sender: TObject);
    procedure Timer1Timer(Sender: TObject);
    procedure txtClientIdChange(Sender: TObject);
    procedure txtClientSecretChange(Sender: TObject);
    procedure txtJWTClientEmailChange(Sender: TObject);
    procedure txtJWTPrivateKeyIdChange(Sender: TObject);
    procedure txtJWTSubjectChange(Sender: TObject);
  private
    FRefreshToken: Boolean;
    procedure DoLog(const aText: string);
    procedure DoRefreshToken;
  private
    procedure DoListCalendars;
    function GetSelectedCalendar: TsgcGoogleCalendarItem;
  public
    procedure DoDeleteCalendar;
    procedure DoEditCalendar;
    procedure DoLoadCalendars;
    procedure DoNewCalendar;
    procedure DoLoadCalendarsChanged;
  private
    procedure DoListEvents(const aCalendar: TsgcGoogleCalendarItem);
  public
    procedure DoEditEvent;
    procedure DoDeleteEvent;
    procedure DoNewEvent;
    procedure DoLoadEvents;
    procedure DoLoadEventsChanged;
  public
    procedure DoAuthenticate;
  end;

var
  FRMGoogleCalendar: TFRMGoogleCalendar;

implementation

uses
  INIFiles, FCalendar,
  sgcJSON, FEvent;

{$R *.dfm}

procedure TFRMGoogleCalendar.FormCreate(Sender: TObject);
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    txtClientId.Text := oINI.ReadString('OAUTH2', 'ClientId', '');
    txtClientSecret.Text := oINI.ReadString('OAUTH2', 'ClientSecret', '');

    txtJWTClientEmail.Text := oINI.ReadString('JWT', 'ClientEmail', '');
    txtJWTPrivateKeyId.Text := oINI.ReadString('JWT', 'PrivateKeyId', '');
    txtJWTSubject.Text := oINI.ReadString('JWT', 'Subject', '');
  Finally
    oINI.Free;
  End;

  if FileExists('private_key.txt') then
    memoJWTPrivateKey.Lines.LoadFromFile('private_key.txt');

  dateFromEvents.Date := EncodeDate(StrToInt(FormatDateTime('yyyy', Now)), 1, 1);
  dateToEvents.Date := Trunc(Now);
end;

procedure TFRMGoogleCalendar.btnCalendarDeleteClick(Sender: TObject);
begin
  DoAuthenticate;

  DoDeleteCalendar;
end;

procedure TFRMGoogleCalendar.btnCalendarEditClick(Sender: TObject);
begin
  DoAuthenticate;

  DoEditCalendar;
end;

procedure TFRMGoogleCalendar.btnCalendarNewClick(Sender: TObject);
begin
  DoAuthenticate;

  DoNewCalendar;
end;

procedure TFRMGoogleCalendar.btnCalendarRefreshClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLoadCalendars;
end;

procedure TFRMGoogleCalendar.btnCalendarsChangesClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLoadCalendarsChanged;
end;

procedure TFRMGoogleCalendar.btnConnectClick(Sender: TObject);
begin
  GoogleCalendar.GoogleCloudOptions.OAuth2.ClientId := txtClientId.Text;
  GoogleCalendar.GoogleCloudOptions.OAuth2.ClientSecret := txtClientSecret.Text;

  DoLoadCalendars;
end;

procedure TFRMGoogleCalendar.btnEventDeleteClick(Sender: TObject);
begin
  DoAuthenticate;

  DoDeleteEvent;
end;

procedure TFRMGoogleCalendar.btnEventEditClick(Sender: TObject);
begin
  DoAuthenticate;

  DoEditEvent;
end;

procedure TFRMGoogleCalendar.btnEventNewClick(Sender: TObject);
begin
  DoAuthenticate;

  DoNewEvent;
end;

procedure TFRMGoogleCalendar.btnEventRefreshClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLoadEvents;
end;

procedure TFRMGoogleCalendar.btnEventsChangedClick(Sender: TObject);
begin
  DoAuthenticate;

  DoLoadEventsChanged;
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
    3:
      DoLog(GoogleCalendar.ACL_List(txtACLCalendarId.Text));
    4:
      begin
        oResource := TsgcGoogleCalendarResource_ACL.Create;
        Try
          oResource.Role := gcrReader;
          oResource.Scope._type := gcstDefault;
          DoLog(GoogleCalendar.ACL_Patch(txtACLCalendarId.Text,
            txtACLRuleId.Text, oResource));
        Finally
          oResource.Free;
        End;
      end;
    5:
      begin
        oResource := TsgcGoogleCalendarResource_ACL.Create;
        Try
          oResource.Role := gcrReader;
          oResource.Scope._type := gcstDefault;
          DoLog(GoogleCalendar.ACL_Update(txtACLCalendarId.Text,
            txtACLRuleId.Text, oResource));
        Finally
          oResource.Free;
        End;
      end;
    6:
      begin
        oWatch := TsgcGoogleCalendarWatch.Create;
        Try
          oWatch.id := FormatDateTime('yyyymmddhhnnsszzz', Now);
          DoLog(GoogleCalendar.ACL_Watch(txtACLCalendarId.Text, oWatch));
        Finally
          oWatch.Free;
        End;
      end;
  end;
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
    4:
      begin
        oResource := TsgcGoogleCalendarResource_Calendar.Create;
        Try
          oResource.Summary := InputBox('Summary',
            'Patch the description of the Calendar', '');
          DoLog(GoogleCalendar.Calendar_Patch(txtCalendarId.Text, oResource));
        Finally
          oResource.Free;
        End;
      end;
    5:
      begin
        oResource := TsgcGoogleCalendarResource_Calendar.Create;
        Try
          oResource.Summary := InputBox('Summary',
            'Update the description of the Calendar', '');
          DoLog(GoogleCalendar.Calendar_Update(txtCalendarId.Text, oResource));
        Finally
          oResource.Free;
        End;
      end;
  end;
end;

procedure TFRMGoogleCalendar.btnExecuteCalendarListClick(Sender: TObject);
var
  oResource: TsgcGoogleCalendarResource_CalendarList;
  oWatch: TsgcGoogleCalendarWatch;
begin
  case cboCalendarList.ItemIndex of
    0:
      DoLog(GoogleCalendar.CalendarList_Delete(txtCalendarListCalendarId.Text));
    1:
      DoLog(GoogleCalendar.CalendarList_Get(txtCalendarListCalendarId.Text));
    2:
      begin
        oResource := TsgcGoogleCalendarResource_CalendarList.Create;
        Try
          oResource.id := txtCalendarListCalendarId.Text;
          DoLog(GoogleCalendar.CalendarList_Insert(oResource));
        Finally
          oResource.Free;
        End;
      end;
    3:
      DoLog(GoogleCalendar.CalendarList_List);
    4:
      begin
        oResource := TsgcGoogleCalendarResource_CalendarList.Create;
        Try
          oResource.id := txtCalendarListCalendarId.Text;
          oResource.BackgroundColor := '#0088aa';
          oResource.ForegroundColor := '#ffffff';
          DoLog(GoogleCalendar.CalendarList_Patch
            (txtCalendarListCalendarId.Text, oResource, True));
        Finally
          oResource.Free;
        End;
      end;
    5:
      begin
        oResource := TsgcGoogleCalendarResource_CalendarList.Create;
        Try
          oResource.id := txtCalendarListCalendarId.Text;
          oResource.BackgroundColor := '#0088aa';
          oResource.ForegroundColor := '#ffffff';
          DoLog(GoogleCalendar.CalendarList_Update
            (txtCalendarListCalendarId.Text, oResource, True));
        Finally
          oResource.Free;
        End;
      end;
    6:
      begin
        oWatch := TsgcGoogleCalendarWatch.Create;
        Try
          oWatch.id := FormatDateTime('yyyymmddhhnnsszzz', Now);
          DoLog(GoogleCalendar.CalendarList_Watch(oWatch));
        Finally
          oWatch.Free;
        End;
      end;
  end;
end;

procedure TFRMGoogleCalendar.btnExecuteChannelClick(Sender: TObject);
begin
  DoLog(GoogleCalendar.Channel_Stop(txtChannelId.Text,
    txtChannelResourceId.Text));
end;

procedure TFRMGoogleCalendar.btnExecuteColorClick(Sender: TObject);
begin
  DoLog(GoogleCalendar.Color_Get);
end;

procedure TFRMGoogleCalendar.btnExecuteEventClick(Sender: TObject);
var
  oResource: TsgcGoogleCalendarResource_Event;
  oWatch: TsgcGoogleCalendarWatch;
begin
  case cboEvent.ItemIndex of
    0:
      DoLog(GoogleCalendar.Event_Delete(txtEventCalendarId.Text,
        txtEventId.Text));
    1:
      DoLog(GoogleCalendar.Event_Get(txtEventCalendarId.Text, txtEventId.Text));
    2:
      begin
        oResource := TsgcGoogleCalendarResource_Event.Create;
        Try
          oResource.Start.DateTime := Now;
          oResource._End.DateTime := Trunc(Now);
          oResource.iCalUID := InputBox('originalUID', 'Set iCalUID', '');

          DoLog(GoogleCalendar.Event_Import(txtEventCalendarId.Text,
            oResource));
        Finally
          oResource.Free;
        End;
      end;
    3:
      begin
        oResource := TsgcGoogleCalendarResource_Event.Create;
        Try
          oResource.Start.DateTime := Now;
          oResource.iCalUID := 'originalUID';

          DoLog(GoogleCalendar.Event_Insert(txtEventCalendarId.Text,
            oResource));
        Finally
          oResource.Free;
        End;
      end;
    4:
      DoLog(GoogleCalendar.Event_Instances(txtEventCalendarId.Text,
        txtEventId.Text));
    5:
      DoLog(GoogleCalendar.Event_List(txtEventCalendarId.Text));
    6:
      DoLog(GoogleCalendar.Event_Move(txtEventCalendarId.Text, txtEventId.Text,
        InputBox('Destination', 'Set Destination', '')));
    7:
      begin
        oResource := TsgcGoogleCalendarResource_Event.Create;
        Try
          oResource.Summary := InputBox('Summary', 'Set Summary Event', '');

          DoLog(GoogleCalendar.Event_Patch(txtEventCalendarId.Text,
            txtEventId.Text, oResource));
        Finally
          oResource.Free;
        End;
      end;
    8:
      DoLog(GoogleCalendar.Event_QuickAdd(txtEventCalendarId.Text,
        InputBox('Text', 'Set New Event Text', '')));
    9:
      begin
        oResource := TsgcGoogleCalendarResource_Event.Create;
        Try
          oResource.Summary := InputBox('Summary', 'Set Summary Event', '');

          DoLog(GoogleCalendar.Event_Update(txtEventCalendarId.Text,
            txtEventId.Text, oResource));
        Finally
          oResource.Free;
        End;
      end;
    10:
      begin
        oWatch := TsgcGoogleCalendarWatch.Create;
        Try
          oWatch.id := FormatDateTime('yyyymmddhhnnsszzz', Now);
          DoLog(GoogleCalendar.Event_Watch(txtEventCalendarId.Text, oWatch));
        Finally
          oWatch.Free;
        End;
      end;
  end;
end;

procedure TFRMGoogleCalendar.btnExecuteFreebusyClick(Sender: TObject);
var
  oItems: TStringList;
begin
  oItems := TStringList.Create;
  Try
    oItems.Add(InputBox('Item', 'Set Item', ''));
    DoLog(GoogleCalendar.Freebusy_Query(oItems, dateFromFreeBusy.DateTime,
      dateToFreeBusy.DateTime));
  Finally
    oItems.Free;
  End;
end;

procedure TFRMGoogleCalendar.btnGetCalendarsClick(Sender: TObject);
begin
  DoLoadCalendars;
end;

procedure TFRMGoogleCalendar.btnLoadJSONSettingsClick(Sender: TObject);
var
  oDialog: TOpenDialog;
begin
  oDialog := TOpenDialog.Create(nil);
  Try
    oDialog.Filter := 'JSON Files|*.json';
    if oDialog.Execute then
    begin
      GoogleCalendar.LoadSettingsFromFile(oDialog.FileName);
      txtJWTClientEmail.Text := GoogleCalendar.GoogleCloudOptions.JWT.ClientEmail;
      txtJWTPrivateKeyId.Text := GoogleCalendar.GoogleCloudOptions.JWT.PrivateKeyId;
      memoJWTPrivateKey.Lines.Text := GoogleCalendar.GoogleCloudOptions.JWT.PrivateKey.Text;
    end;
  Finally
    oDialog.Free;
  End;
end;

procedure TFRMGoogleCalendar.cboEventsOrderByChange(Sender: TObject);
begin
  DoLoadEvents;
end;

procedure TFRMGoogleCalendar.chkEventByDateClick(Sender: TObject);
begin
  DoLoadEvents;
end;

procedure TFRMGoogleCalendar.dateFromEventsChange(Sender: TObject);
begin
  DoLoadEvents;
end;

procedure TFRMGoogleCalendar.dateToEventsChange(Sender: TObject);
begin
  DoLoadEvents;
end;

procedure TFRMGoogleCalendar.DoAuthenticate;
var
  oINI: TINIFile;
  vToken: string;
begin
  if pageControl2.ActivePage = tabOAuth2 then
  begin
    GoogleCalendar.GoogleCloudOptions.Authentication := gcaOAuth2;
    if not FRefreshToken then
    begin
      FRefreshToken := True;

      oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
      Try
        vToken := oINI.ReadString('OAUTH2', 'Token', '');
        if vToken <> '' then
          GoogleCalendar.RefreshToken(vToken);
      Finally
        oINI.Free;
      End;
    end;
  end
  else if pageControl2.ActivePage = tabServiceAccount then
    GoogleCalendar.GoogleCloudOptions.Authentication := gcaJWT;
end;

procedure TFRMGoogleCalendar.DoDeleteCalendar;
var
  oCalendar: TsgcGoogleCalendarResource_CalendarList;
begin
  if listCalendars.ItemIndex <> -1 then
  begin
    oCalendar := TsgcGoogleCalendarResource_CalendarList
      (listCalendars.Items.Objects[listCalendars.ItemIndex]);
    if messagedlg(Format('Do you want delete Calendar: %s?', [oCalendar.Summary]
      ), mtConfirmation, mbOKCancel, 0) = mrOK then
    begin
      if GoogleCalendar.DeleteCalendar(oCalendar.id) then
      begin
        ShowMessage('Calendar Deleted');

        DoLoadCalendars;
      end;
    end;
  end;
end;

procedure TFRMGoogleCalendar.DoDeleteEvent;
var
  oCalendar: TsgcGoogleCalendarItem;
  oEvent: TsgcGoogleCalendarEventItem;
begin
  if listEvents.ItemIndex <> -1 then
  begin
    oCalendar := GetSelectedCalendar;
    if Assigned(oCalendar) then
    begin
      oEvent := TsgcGoogleCalendarEventItem
        (listEvents.Items.Objects[listEvents.ItemIndex]);
      if messagedlg(Format('Do you want delete Event: %s?', [oEvent.Summary]
        ), mtConfirmation, mbOKCancel, 0) = mrOK then
      begin
        if GoogleCalendar.DeleteEvent(oCalendar.id, oEvent.id) then
        begin
          ShowMessage('Event Deleted');

          DoLoadEvents;
        end;
      end;
    end;
  end;
end;

procedure TFRMGoogleCalendar.DoEditCalendar;
var
  oFRMCalendar: TFRMCalendar;
begin
  if listCalendars.ItemIndex <> -1 then
  begin
    oFRMCalendar := TFRMCalendar.Create(nil);
    Try
      oFRMCalendar.Calendar := GetSelectedCalendar;
      if oFRMCalendar.ShowModal = mrOK then
        GoogleCalendar.UpdateCalendar(oFRMCalendar.Calendar);
    Finally
      oFRMCalendar.Free;
    End;
  end;
end;

procedure TFRMGoogleCalendar.DoEditEvent;
var
  oFRMEvent: TFRMEvent;
  oCalendar: TsgcGoogleCalendarItem;
begin
  if listEvents.ItemIndex <> -1 then
  begin
    oCalendar := GetSelectedCalendar;
    if Assigned(oCalendar) then
    begin
      oFRMEvent := TFRMEvent.Create(nil);
      Try
        oFRMEvent.Event := TsgcGoogleCalendarEventItem
          (listEvents.Items.Objects[listEvents.ItemIndex]);
        if oFRMEvent.ShowModal = mrOK then
        begin
          GoogleCalendar.UpdateEvent(oCalendar.Id, oFRMEvent.Event);

          DoLoadEvents;
        end;
      Finally
        oFRMEvent.Free;
      End;
    end;
  end;
end;

procedure TFRMGoogleCalendar.DoListCalendars;
var
  i: Integer;
  vText: string;
begin
  listCalendars.clear;

  listCalendars.Items.BeginUpdate;
  Try
    for i := 0 to GoogleCalendar.Calendars.Count - 1 do
    begin
      vText := GoogleCalendar.Calendars.Calendar[i].Summary;
      if GoogleCalendar.Calendars.Calendar[i].Primary then
        vText := vText + ' [Primary]';

      listCalendars.Items.AddObject(vText, GoogleCalendar.Calendars.Calendar[i]);
    end;
  Finally
    listCalendars.Items.EndUpdate;
  End;
end;

procedure TFRMGoogleCalendar.DoListEvents(const aCalendar
  : TsgcGoogleCalendarItem);
var
  i: Integer;
  vText: string;
begin
  listEvents.Items.BeginUpdate;
  Try
    listEvents.clear;

    for i := 0 to aCalendar.Events.Count - 1 do
    begin
      if aCalendar.Events[i].Start.Date > EncodeDate(1900, 1, 1) then
        vText := Format('%s - %s %s', [FormatDateTime('yyyy-mm-dd',
          aCalendar.Events[i].Start.Date), FormatDateTime('yyyy-mm-dd',
          aCalendar.Events[i]._End.Date), aCalendar.Events[i].Summary])
      else
        vText := Format('%s - %s %s', [FormatDateTime('yyyy-mm-dd hh:nn',
          aCalendar.Events[i].Start.DateTime), FormatDateTime('hh:nn',
          aCalendar.Events[i]._End.DateTime), aCalendar.Events[i].Summary]);

      if aCalendar.Events[i].Location <> '' then
        vText := vText + ' (' + aCalendar.Events[i].Location + ')';

      listEvents.Items.AddObject(vText, aCalendar.Events[i]);
    end;
  Finally
    listEvents.Items.EndUpdate;
  End;
end;

procedure TFRMGoogleCalendar.DoLoadCalendars;
begin
  GoogleCalendar.LoadCalendars;
  DoListCalendars;
  txtCalendarNextSyncToken.Text := GoogleCalendar.Calendars.NextSyncToken;
end;

procedure TFRMGoogleCalendar.DoLoadCalendarsChanged;
begin
  if txtCalendarSyncToken.Text <> '' then
    GoogleCalendar.LoadCalendarsChanged(txtCalendarSyncToken.Text)
  else
    GoogleCalendar.LoadCalendarsChanged(txtCalendarNextSyncToken.Text);
end;

procedure TFRMGoogleCalendar.DoLoadEvents;
var
  oCalendar: TsgcGoogleCalendarItem;
begin
  listEvents.clear;

  if listCalendars.ItemIndex <> -1 then
  begin
    oCalendar := TsgcGoogleCalendarItem(listCalendars.Items.Objects
      [listCalendars.ItemIndex]);
    if Assigned(oCalendar) then
    begin
      if chkEventByDate.Checked then
        GoogleCalendar.LoadEvents(oCalendar.id, dateFromEvents.DateTime, dateToEvents.DateTime, TsgcGoogleCalendarEventListOrdered(cboEventsOrderBy.ItemIndex))
      else
        GoogleCalendar.LoadEvents(oCalendar.id, TsgcGoogleCalendarEventListOrdered(cboEventsOrderBy.ItemIndex));

      DoListEvents(oCalendar);
      txtEventNextSyncToken.Text := oCalendar.Events.NextSyncToken;
    end;
  end;
end;

procedure TFRMGoogleCalendar.DoLoadEventsChanged;
var
  oCalendar: TsgcGoogleCalendarItem;
begin
  oCalendar := GetSelectedCalendar;
  if Assigned(oCalendar) then
  begin
    if txtEventSyncToken.Text <> '' then
      GoogleCalendar.LoadEventsChanged(oCalendar.ID, txtEventSyncToken.Text)
    else
      GoogleCalendar.LoadEventsChanged(oCalendar.ID, txtEventNextSyncToken.Text);
  end;
end;

procedure TFRMGoogleCalendar.DoLog(const aText: string);
begin
  memoLog.Lines.Text := aText;
end;

procedure TFRMGoogleCalendar.DoNewCalendar;
var
  vId: string;
  vSummary: string;
begin
  vSummary := InputBox('New Calendar', 'Set Calendar Name', '');

  vId := GoogleCalendar.NewCalendar(vSummary);
  if vId <> '' then
  begin
    ShowMessage('New Calendar created with id: ' + vId);

    DoLoadCalendars;
  end;
end;

procedure TFRMGoogleCalendar.DoNewEvent;
var
  oFRMEvent: TFRMEvent;
  oCalendar: TsgcGoogleCalendarItem;
  oEvent: TsgcGoogleCalendarEventItem;
  vId: string;
begin
  oCalendar := GetSelectedCalendar;
  if Assigned(oCalendar) then
  begin
    oFRMEvent := TFRMEvent.Create(nil);
    Try
      oEvent := TsgcGoogleCalendarEventItem.Create;
      Try
        oFRMEvent.Event := oEvent;
        if oFRMEvent.ShowModal = mrOK then
        begin
          vId := GoogleCalendar.NewEvent(oCalendar.Id, oFRMEvent.Event);
          if vId <> '' then
          begin
            ShowMessage('New Event created with id: ' + vId);

            DoLoadEvents;
          end;
        end;
      Finally
        oEvent.Free;
      End;
    Finally
      oFRMEvent.Free;
    End;
  end;
end;

procedure TFRMGoogleCalendar.DoRefreshToken;
var
  oINI: TINIFile;
  vToken: string;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    vToken := oINI.ReadString('OAUTH2', 'Token', '');
    if vToken <> '' then
      GoogleCalendar.RefreshToken(vToken);
  Finally
    oINI.Free;
  End;
end;

procedure TFRMGoogleCalendar.FormClose(Sender: TObject; var Action:
    TCloseAction);
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.WriteString('OAUTH2', 'ClientId', txtClientId.Text);
    oINI.WriteString('OAUTH2', 'ClientSecret', txtClientSecret.Text);
    oINI.WriteString('JWT', 'ClientEmail', txtJWTClientEmail.Text);
    oINI.WriteString('JWT', 'PrivateKeyId', txtJWTPrivateKeyId.Text);
    oINI.WriteString('JWT', 'Subject', txtJWTSubject.Text);

    memoJWTPrivateKey.Lines.SaveToFile('private_key.txt');
  Finally
    oINI.Free;
  End;
end;

function TFRMGoogleCalendar.GetSelectedCalendar: TsgcGoogleCalendarItem;
begin
  result := nil;
  if listCalendars.ItemIndex <> -1 then
    result := TsgcGoogleCalendarItem(listCalendars.Items.Objects[listCalendars.ItemIndex]);
end;

procedure TFRMGoogleCalendar.GoogleCalendarAuthToken(Sender: TObject;
  const TokenType, Token, Data: string);
var
  oINI: TINIFile;
  oJSON: TsgcJSON;
begin
  oJSON := TsgcJSON.Create(nil);
  Try
    oJSON.Read(Data);
    if oJSON.Node['refresh_token'] <> nil then
    begin
      oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
      Try
        oINI.WriteString('OAUTH2', 'Token', oJSON.Node['refresh_token'].Value);
      Finally
        oINI.Free;
      End;
    end;
  Finally
    oJSON.Free;
  End;
end;

procedure TFRMGoogleCalendar.GoogleCalendarError(Sender: TObject; const aError:
    TsgcGoogleCalendarError);
begin
  ShowMessage(aError.Description);
end;

procedure TFRMGoogleCalendar.listCalendarsClick(Sender: TObject);
begin
  DoLoadEvents;
end;

procedure TFRMGoogleCalendar.listCalendarsDblClick(Sender: TObject);
begin
  DoEditCalendar;
end;

procedure TFRMGoogleCalendar.listEventsDblClick(Sender: TObject);
begin
  DoEditEvent;
end;

procedure TFRMGoogleCalendar.memoJWTPrivateKeyChange(Sender: TObject);
begin
  GoogleCalendar.GoogleCloudOptions.JWT.PrivateKey.Text := memoJWTPrivateKey.Lines.Text;
end;

procedure TFRMGoogleCalendar.tabExecuteSettingsClick(Sender: TObject);
var
  oWatch: TsgcGoogleCalendarWatch;
begin
  case cboSettings.ItemIndex of
    0:
      DoLog(GoogleCalendar.Settings_Get('locale'));
    1:
      DoLog(GoogleCalendar.Settings_List);
    2:
      begin
        oWatch := TsgcGoogleCalendarWatch.Create;
        Try
          oWatch.id := FormatDateTime('yyyymmddhhnnsszzz', Now);
          DoLog(GoogleCalendar.Settings_Watch(oWatch));
        Finally
          oWatch.Free;
        End;
      end;
  end;
end;

procedure TFRMGoogleCalendar.Timer1Timer(Sender: TObject);
begin
  DoRefreshToken;
end;

procedure TFRMGoogleCalendar.txtClientIdChange(Sender: TObject);
begin
  GoogleCalendar.GoogleCloudOptions.OAuth2.ClientId := txtClientId.Text;
end;

procedure TFRMGoogleCalendar.txtClientSecretChange(Sender: TObject);
begin
  GoogleCalendar.GoogleCloudOptions.OAuth2.ClientSecret := txtClientSecret.Text;
end;

procedure TFRMGoogleCalendar.txtJWTClientEmailChange(Sender: TObject);
begin
  GoogleCalendar.GoogleCloudOptions.JWT.ClientEmail := txtJWTClientEmail.Text;
end;

procedure TFRMGoogleCalendar.txtJWTPrivateKeyIdChange(Sender: TObject);
begin
  GoogleCalendar.GoogleCloudOptions.JWT.PrivateKeyId := txtJWTPrivateKeyId.Text;
end;

procedure TFRMGoogleCalendar.txtJWTSubjectChange(Sender: TObject);
begin
  GoogleCalendar.GoogleCloudOptions.JWT.Subject := txtJWTSubject.Text;
end;

end.
```

