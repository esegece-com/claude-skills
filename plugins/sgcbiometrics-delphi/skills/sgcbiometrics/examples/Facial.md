# Facial

Featured demo. Full source of every unit.

Demo: `Facial`

### FFacial.pas

```pascal
unit FFacial;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ComCtrls, jpeg, ExtCtrls,
  // sgc
  sgcBiometrics_WinBio_Types, sgcBiometrics, sgcBiometrics_WinBio_Storage,
  sgcBiometrics_WinBio_Storage_File, sgcBiometrics_Classes,
  sgcBiometrics_Client, sgcBiometrics_WinBio_Client,
  sgcBiometrics_WinBio_Client_Facial, Vcl.Imaging.pngimage;

type
  TFRMFacial = class(TForm)
    memoLog: TMemo;
    pnlLog: TPanel;
    Facial: TsgcWinBioFacial;
    Panel2: TPanel;
    PageControl1: TPageControl;
    pnlLeft: TPanel;
    Image1: TImage;
    Panel1: TPanel;
    lblLog: TLabel;
    Label6: TLabel;
    tabStart: TTabSheet;
    Label8: TLabel;
    Label10: TLabel;
    Label11: TLabel;
    btnStartMonitorPresence: TButton;
    btnStopMonitorPresence: TButton;
    groupMonitorPresence: TGroupBox;
    GroupBox1: TGroupBox;
    Label1: TLabel;
    btnFacialRecognize: TButton;
    btnFacialIdentify: TButton;
    Label2: TLabel;
    procedure btnFacialIdentifyClick(Sender: TObject);
    procedure btnFacialRecognizeClick(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure btnStartMonitorPresenceClick(Sender: TObject);
    procedure btnStopMonitorPresenceClick(Sender: TObject);
    procedure FacialCancel(Sender: TObject; const aSession: Cardinal);
    procedure FacialEnumBiometricUnit(Sender: TObject;
      const aUnit: WINBIO_UNIT_SCHEMA; const aNum, aCount: Integer);
    procedure FacialOpenSession(Sender: TObject; const aSession: Cardinal);
    procedure FacialCloseSession(Sender: TObject; const aSession: Cardinal);
    procedure FacialEnumEnrollments(Sender: TObject; const aIdentity:
        WINBIO_IDENTITY; const aSubFactor: WINBIO_BIOMETRIC_SUBTYPE; const aNum,
        aCount: Integer);
    procedure FacialError(Sender: TObject; const aError: string; const aCode:
        Integer);
    procedure FacialPresenceArrive(Sender: TObject; const aUnitId: Integer; const
        aPresence: WINBIO_PRESENCE);
    procedure FacialPresenceDepart(Sender: TObject; const aUnitId: Integer; const
        aPresence: WINBIO_PRESENCE);
    procedure FacialPresenceRecognize(Sender: TObject; const aUnitId: Integer;
        const aPresence: WINBIO_PRESENCE);
    procedure FacialPresenceTrack(Sender: TObject; const aUnitId: Integer; const
        aPresence: WINBIO_PRESENCE);
    procedure FacialPresenceUnknown(Sender: TObject; const aUnitId: Integer);
    procedure FacialPresenceUpdateAll(Sender: TObject; const aUnitId: Integer);
    procedure StorageFileAddUnit(Sender: TObject;
      const aDatabaseId: WINBIO_GUID; aUnitId: Integer);
  private
  protected
    procedure DoLog(const aText: string);
    procedure DoMessage(const aText: string; const aColor: TColor = clGreen);
  end;

var
  FRMFacial: TFRMFacial;

implementation

uses
  ShellAPI, INIFiles,
  // sgc
  sgcBiometrics_WinBio, sgcBiometrics_Types,
  sgcBiometrics_Helpers;

{$R *.dfm}


procedure TFRMFacial.btnFacialIdentifyClick(Sender: TObject);
begin
  if not Facial.SessionIsOpen then
  begin
    if Facial.InitializeSensors(10000) then
      DoLog('#Identified: ' + Facial.FacialIdentify)
  end
  else
    DoLog('#Identified: ' + Facial.FacialIdentify);
end;

procedure TFRMFacial.btnFacialRecognizeClick(Sender: TObject);
begin
  if not Facial.SessionIsOpen then
  begin
    if Facial.InitializeSensors(10000) then
    begin
      if Facial.FacialRecognize then
        DoLog('#Recognized');
    end;
  end
  else
  begin
    if Facial.FacialRecognize then
      DoLog('#Recognized');
  end;
end;

procedure TFRMFacial.FormCreate(Sender: TObject);
begin
  pageControl1.TabHeight := 1;
  pageControl1.TabWidth := 1;
end;

procedure TFRMFacial.btnStartMonitorPresenceClick(Sender: TObject);
begin
  btnStopMonitorPresence.Enabled := True;
  btnStartMonitorPresence.Enabled := False;

  if not Facial.SessionIsOpen then
  begin
    if Facial.InitializeSensors(10000) then
      Facial.StartMonitorPresence
  end
  else
    Facial.StartMonitorPresence;
end;

procedure TFRMFacial.btnStopMonitorPresenceClick(Sender: TObject);
begin
  btnStopMonitorPresence.Enabled := False;
  btnStartMonitorPresence.Enabled := True;

  if Facial.SessionIsOpen then
    Facial.StopMonitorPresence;
end;

procedure TFRMFacial.DoMessage(const aText: string; const aColor:
    TColor = clGreen);
begin
  lblLog.Caption := aText;
  lblLog.Font.Color := aColor;
  Application.ProcessMessages;
end;

procedure TFRMFacial.DoLog(const aText: string);
begin
  memoLog.Lines.Add(aText);
end;


procedure TFRMFacial.StorageFileAddUnit(Sender: TObject; const aDatabaseId:
    WINBIO_UUID; aUnitId: Integer);
begin
  DoLog('AddUnit: ' + aDatabaseId.Guid + ' ' + IntToStr(aUnitId));
end;

procedure TFRMFacial.FacialCancel(Sender: TObject; const
    aSession: Cardinal);
begin
  DoLog('Cancelled operation.');
end;

procedure TFRMFacial.FacialCloseSession(Sender: TObject; const
    aSession: Cardinal);
begin
  DoLog('Session Closed');
end;


procedure TFRMFacial.FacialEnumBiometricUnit(Sender: TObject; const aUnit:
    WINBIO_UNIT_SCHEMA; const aNum: Integer; const aCount: Integer);
begin
  if aNum = 1 then
  begin
    DoLog('Using unit id: ' + IntToStr(aUnit.UnitId));
    DoLog('Device instance id: ' + aUnit.DeviceInstanceId);
  end;
end;

procedure TFRMFacial.FacialEnumEnrollments(Sender: TObject; const
    aIdentity: WINBIO_IDENTITY; const aSubFactor: WINBIO_BIOMETRIC_SUBTYPE;
    const aNum, aCount: Integer);
var
  vSubFactor: string;
begin
  case aSubfactor of
    WINBIO_ANSI_385_FACE_TYPE_UNKNOWN: vSubFactor := 'UNKNOWN';
    WINBIO_ANSI_385_FACE_FRONTAL_FULL: vSubFactor := 'FRONTAL_FULL';
    WINBIO_ANSI_385_FACE_FRONTAL_TOKEN: vSubFactor := 'FRONTAL_TOKEN';
  end;
  DoLog('EnumEnrollment: ' + vSubFactor);
end;

procedure TFRMFacial.FacialError(Sender: TObject; const aError:
    string; const aCode: Integer);
begin
  DoLog('Error: ' + aError + ' [' + IntToStr(aCode) + ']');
  DoMessage(aError, clRed);
end;

procedure TFRMFacial.FacialOpenSession(Sender: TObject; const aSession:
    WINBIO_SESSION_HANDLE);
begin
  DoLog('Open Session');
end;

procedure TFRMFacial.FacialPresenceArrive(Sender: TObject; const aUnitId:
    Integer; const aPresence: WINBIO_PRESENCE);
begin
  DoLog('Monitor Presence [' + IntToStr(aPresence.TrackingId) + ']: ARRIVE');
end;

procedure TFRMFacial.FacialPresenceDepart(Sender: TObject; const aUnitId:
    Integer; const aPresence: WINBIO_PRESENCE);
begin
  DoLog('Monitor Presence [' + IntToStr(aPresence.TrackingId) + ']: DEPART');
end;

procedure TFRMFacial.FacialPresenceRecognize(Sender: TObject; const aUnitId:
    Integer; const aPresence: WINBIO_PRESENCE);
begin
  if aPresence.Identity._Type = WINBIO_ID_TYPE_SID then
    DoLog('Monitor Presence [' + IntToStr(aPresence.TrackingId) + ']: RECOGNIZE ' + aPresence.Identity.AccountSid.Data)
  else
    DoLog('Monitor Presence [' + IntToStr(aPresence.TrackingId) + ']: RECOGNIZE');
end;

procedure TFRMFacial.FacialPresenceTrack(Sender: TObject; const aUnitId:
    Integer; const aPresence: WINBIO_PRESENCE);
var
  vReject: string;
begin
  vReject := '';
  case aPresence.RejectDetail of
    WINBIO_FACE_TOO_BRIGHT: vReject := 'FACE Too Bright';
    WINBIO_FACE_TOO_DARK: vReject := 'FACE Too Dark';
    WINBIO_FACE_SPOOF_DETECTED: vReject := 'FACE Spoof Detected';
    WINBIO_FACE_AMBIGUOUS_TARGET: vReject := 'FACE Ambiguous Target';
    WINBIO_FACE_EYES_OCCLUDED: vReject := 'FACE Eyes Occluded';
    WINBIO_FACE_WRONG_ORIENTATION: vReject := 'FACE Wrong Orientation';
    WINBIO_FACE_TOO_HIGH: vReject := 'FACE Too High';
    WINBIO_FACE_TOO_LOW: vReject := 'FACE Too Low';
    WINBIO_FACE_TOO_LEFT: vReject := 'FACE Too Left';
    WINBIO_FACE_TOO_RIGHT: vReject := 'FACE Too Right';
    WINBIO_FACE_TOO_NEAR: vReject := 'FACE Too Near';
    WINBIO_FACE_TOO_FAR: vReject := 'FACE Too Far';
  end;
  DoLog('Monitor Presence [' + IntToStr(aPresence.TrackingId) + ']: TRACK [' + vReject + ']');
end;

procedure TFRMFacial.FacialPresenceUnknown(Sender: TObject; const aUnitId:
    Integer);
begin
  DoLog('Monitor Presence: UNKNOWN');
end;

procedure TFRMFacial.FacialPresenceUpdateAll(Sender: TObject; const aUnitId:
    Integer);
begin
  DoLog('Monitor Presence: UPDATE ALL');
end;

end.
```

