# TsgcWinBioFingerPrint - Example

Full source of `FFingerPrint.pas` from the **FingerPrint** demo, which uses `TsgcWinBioFingerPrint`.

API reference: [TsgcWinBioFingerPrint](../reference/api/TsgcWinBioFingerPrint.md)
Source demo: `FingerPrint` (file `FFingerPrint.pas`)

```pascal
unit FFingerPrint;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ComCtrls, jpeg, ExtCtrls,
  // sgc
  sgcBiometrics_WinBio_Types, sgcBiometrics, sgcBiometrics_WinBio_Storage,
  sgcBiometrics_WinBio_Storage_File, sgcBiometrics_Classes,
  sgcBiometrics_Client, sgcBiometrics_WinBio_Client,
  sgcBiometrics_WinBio_Client_FingerPrint;

type
  TFRMFingerPrint = class(TForm)
    memoLog: TMemo;
    pnlLog: TPanel;
    FingerPrint: TsgcWinBioFingerPrint;
    StorageFile: TsgcWinBioStorageFile;
    Panel2: TPanel;
    PageControl1: TPageControl;
    tabPrivatePoolSensor: TTabSheet;
    tabSensors: TTabSheet;
    optCreateStorage: TRadioButton;
    optOpenStorage: TRadioButton;
    optRebuildStorage: TRadioButton;
    tabEnroll: TTabSheet;
    optEnroll: TRadioButton;
    optIdentify: TRadioButton;
    pnlLeft: TPanel;
    Image1: TImage;
    Panel1: TPanel;
    btnNext: TButton;
    btnPrevious: TButton;
    optLocate: TRadioButton;
    Image2: TImage;
    Image3: TImage;
    optLH_LITTLE_FINGER: TRadioButton;
    optLH_RING_FINGER: TRadioButton;
    optLH_MIDDLE_FINGER: TRadioButton;
    optLH_INDEX_FINGER: TRadioButton;
    optLH_THUMB: TRadioButton;
    optRH_THUMB: TRadioButton;
    optRH_INDEX_FINGER: TRadioButton;
    optRH_MIDDLE_FINGER: TRadioButton;
    optRH_RING_FINGER: TRadioButton;
    optRH_LITTLE_FINGER: TRadioButton;
    lblLog: TLabel;
    Label4: TLabel;
    Label5: TLabel;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    Label6: TLabel;
    tabStart: TTabSheet;
    Label7: TLabel;
    optSystemSensorPool: TRadioButton;
    optPrivateSensorPool: TRadioButton;
    Label8: TLabel;
    Label9: TLabel;
    Label10: TLabel;
    Label11: TLabel;
    Label12: TLabel;
    Label13: TLabel;
    optCaptureSample: TRadioButton;
    Label14: TLabel;
    optDeleteTemplate: TRadioButton;
    Label15: TLabel;
    tabDeleteTemplate: TTabSheet;
    cboDeleteTemplateSubFactor: TComboBox;
    Label16: TLabel;
    txtDeleteTemplateId: TEdit;
    Label17: TLabel;
    optGUID: TRadioButton;
    optSID: TRadioButton;
    chkAsynchronous: TCheckBox;
    Label18: TLabel;
    imgFingerprint: TImage;
    optEnumEnrollments: TRadioButton;
    Label19: TLabel;
    procedure FormCreate(Sender: TObject);
    procedure btnNextClick(Sender: TObject);
    procedure btnPreviousClick(Sender: TObject);
    procedure chkAsynchronousClick(Sender: TObject);
    procedure FingerPrintAfterInitializeStorage(Sender: TObject; const aDatabaseId:
        WINBIO_GUID);
    procedure FingerPrintBeforeInitializeStorage(Sender: TObject; const
        aDatabaseId: WINBIO_GUID);
    procedure FingerPrintCancel(Sender: TObject; const aSession: Cardinal);
    procedure FingerPrintCaptureSample(Sender: TObject; const aSample: WINBIO_BIR;
        const aHeader: WINBIO_BIR_HEADER; const aAnsiBdbHeader:
        WINBIO_BDB_ANSI_381_HEADER; const aAnsiBdbRecord:
        WINBIO_BDB_ANSI_381_RECORD; const aFirstPixel: PByte);
    procedure FingerPrintCaptureSampleReject(Sender: TObject; const aSample:
        WINBIO_BIR; aRejectDetail: WINBIO_REJECT_DETAIL);
    procedure FingerPrintEnrollBegin(Sender: TObject);
    procedure FingerPrintEnrollCapture(Sender: TObject; aSwipes: Integer;
      const aResult: WINBIO_ENROLL_RESULT;
      const aRejectDetail: WINBIO_REJECT_DETAIL);
    procedure FingerPrintEnrollCommit(Sender: TObject;
      const aIdentity: WINBIO_IDENTITY; aIsNewTemplate: Boolean);
    procedure FingerPrintEnumBiometricUnit(Sender: TObject;
      const aUnit: WINBIO_UNIT_SCHEMA; const aNum, aCount: Integer);
    procedure FingerPrintOpenSession(Sender: TObject; const aSession: Cardinal);
    procedure FingerPrintSensorLocated(Sender: TObject; const aUnitId: Integer);
    procedure FingerPrintCloseSession(Sender: TObject; const aSession: Cardinal);
    procedure FingerPrintEnumDatabase(Sender: TObject; const aStorage:
        WINBIO_STORAGE_SCHEMA; const aNum, aCount: Integer);
    procedure FingerPrintEnumEnrollments(Sender: TObject; const aIdentity:
        WINBIO_IDENTITY; const aSubFactor: WINBIO_BIOMETRIC_SUBTYPE; const aNum,
        aCount: Integer);
    procedure FingerPrintError(Sender: TObject; const aError: string; const aCode:
        Integer);
    procedure FingerPrintIdentify(Sender: TObject; const aUnitId: Integer; const
        aIdentity: WINBIO_IDENTITY; const aSubFactor: WINBIO_BIOMETRIC_SUBTYPE;
        const aRejectDetail: WINBIO_REJECT_DETAIL);
    procedure FingerPrintTemplateDeleted(Sender: TObject; const aUnitId: Integer;
        const aIdentity: WINBIO_IDENTITY; const aSubFactor:
        WINBIO_BIOMETRIC_SUBTYPE);
    procedure StorageFileAddDatabase(Sender: TObject;
      const aDatabaseId: WINBIO_GUID; aUnitId: Integer);
    procedure StorageFileAddUnit(Sender: TObject;
      const aDatabaseId: WINBIO_GUID; aUnitId: Integer);
    procedure StorageFileError(Sender: TObject; const aError: string; const aCode:
        Integer);
    procedure StorageFileRemoveDatabase(Sender: TObject;
      const aDatabaseId: WINBIO_GUID);
    procedure StorageFileRemoveUnit(Sender: TObject;
      const aDatabaseId: WINBIO_GUID; aUnitId: Integer);
    procedure tabCaptureSampleShow(Sender: TObject);
    procedure tabEnrollShow(Sender: TObject);
    procedure tabPrivatePoolSensorShow(Sender: TObject);
    procedure tabSensorsShow(Sender: TObject);
    procedure tabStartShow(Sender: TObject);
  private
    procedure DoReadINI;
  protected
    procedure DoLog(const aText: string);
    procedure DoMessage(const aText: string; const aColor: TColor = clGreen);
  end;

var
  FRMFingerPrint: TFRMFingerPrint;

implementation

uses
  ShellAPI, INIFiles,
  // sgc
  sgcBiometrics_WinBio, sgcBiometrics_Types,
  sgcBiometrics_Helpers;

{$R *.dfm}

function ExecAndWait(Cmdline: string; Hide: boolean = false; MaxWait: DWORD
    = INFINITE): DWORD;
var
  si: TStartupInfo;
  pi: TProcessInformation;
  iRet: Cardinal;
begin
  {$WARN SYMBOL_PLATFORM OFF}
  UniqueString(Cmdline);
  {$IFDEF VER210}
  si := Default(TStartupInfo);
  {$ELSE}
  FillChar(si, SizeOf(si), 0);
  {$ENDIF}
  si.cb := SizeOf(si);
  si.dwFlags := si.dwFlags or STARTF_USESHOWWINDOW;
  if Hide then
    si.wShowWindow := SW_HIDE
  else
    si.wShowWindow := SW_SHOWNORMAL;
  Win32Check(CreateProcess(nil, PChar(Cmdline), nil, nil, False,
    NORMAL_PRIORITY_CLASS, nil, nil, si, pi));
  CloseHandle(pi.hThread);
  try
    while True do
    begin
      iRet := MsgWaitForMultipleObjects(1, pi.hProcess, False, MaxWait, QS_ALLINPUT);
      Win32Check(iRet <> WAIT_FAILED);
      case iRet of
      WAIT_OBJECT_0:
        break;
      WAIT_OBJECT_0+1:
        Application.ProcessMessages;
      end;
    end;
    Win32Check(GetExitCodeProcess(pi.hProcess, Result));
  finally
    CloseHandle(pi.hProcess);
  end;
  {$WARN SYMBOL_PLATFORM ON}
end;


procedure TFRMFingerPrint.FormCreate(Sender: TObject);
begin
  pageControl1.TabHeight := 1;
  pageControl1.TabWidth := 1;

  DoReadINI;
end;

procedure TFRMFingerPrint.btnNextClick(Sender: TObject);
var
  oIdentity: WINBIO_IDENTITY;
begin
  if PageControl1.ActivePage = tabStart then
  begin
    if optSystemSensorPool.Checked then
    begin
      FingerPrint.Storage := nil;
      PageControl1.ActivePage := tabSensors;
    end
    else if optPrivateSensorPool.Checked then
    begin
      FingerPrint.Storage := StorageFile;
      PageControl1.ActivePage := tabPrivatePoolSensor;
    end
    else if optCaptureSample.Checked then
    begin
      if not sgcIsAdmin then
        raise Exception.Create('Your application does NOT have Administrator level privileges!');

      FingerPrint.Storage := nil;
      DoMessage('Put finger over sensor to identiy', clBlack);
      FingerPrint.CaptureSample;
    end;
  end
  else if PageControl1.ActivePage = tabPrivatePoolSensor then
  begin
    if optOpenStorage.Checked then
      PageControl1.ActivePage := tabSensors
    else if optCreateStorage.Checked then
    begin
      if not sgcIsAdmin then
        raise Exception.Create('Your application does NOT have Administrator level privileges!');
      FingerPrint.InitializeSensors;
    end
    else
    begin
      if not sgcIsAdmin then
        raise Exception.Create('Your application does NOT have Administrator level privileges!');
      FingerPrint.RebuildStorage;
    end;
  end
  else if PageControl1.ActivePage = tabSensors then
  begin
    if optLocate.checked then
    begin
      DoMessage('Press sensor to locate', clBlack);
      FingerPrint.LocateSensor;
    end
    else if optIdentify.checked then
    begin
      DoMessage('Put finger over sensor to identiy', clBlack);
      FingerPrint.Identify;
    end
    else if optEnumEnrollments.Checked then
      FingerPrint.EnumEnrollments
    else if optDeleteTemplate.Checked then
      pageControl1.ActivePage := tabDeleteTemplate
    else if optEnroll.Checked then
      PageControl1.ActivePage := tabEnroll;
  end
  else if PageControl1.ActivePage = tabDeleteTemplate then
  begin
    FillChar(oIdentity, SizeOf(oIdentity), 0);
    if optGUID.Checked then
    begin
      oIdentity._Type := WINBIO_ID_TYPE_GUID;
      oIdentity.TemplateGuid._Guid := StringToGUID(txtDeleteTemplateId.text);
    end
    else if optSID.Checked then
    begin
      oIdentity._Type := WINBIO_ID_TYPE_SID;
//      oIdentity.AccountSid.Data := txtDeleteTemplateId.Text;
    end;

    case cboDeleteTemplateSubFactor.ItemIndex of
      0: FingerPrint.DeleteTemplate(oIdentity, WINBIO_ANSI_381_POS_RH_THUMB);
      1: FingerPrint.DeleteTemplate(oIdentity, WINBIO_ANSI_381_POS_RH_INDEX_FINGER);
      2: FingerPrint.DeleteTemplate(oIdentity, WINBIO_ANSI_381_POS_RH_MIDDLE_FINGER);
      3: FingerPrint.DeleteTemplate(oIdentity, WINBIO_ANSI_381_POS_RH_RING_FINGER);
      4: FingerPrint.DeleteTemplate(oIdentity, WINBIO_ANSI_381_POS_RH_LITTLE_FINGER);

      5: FingerPrint.DeleteTemplate(oIdentity, WINBIO_ANSI_381_POS_LH_THUMB);
      6: FingerPrint.DeleteTemplate(oIdentity, WINBIO_ANSI_381_POS_LH_INDEX_FINGER);
      7: FingerPrint.DeleteTemplate(oIdentity, WINBIO_ANSI_381_POS_LH_MIDDLE_FINGER);
      8: FingerPrint.DeleteTemplate(oIdentity, WINBIO_ANSI_381_POS_LH_RING_FINGER);
      9: FingerPrint.DeleteTemplate(oIdentity, WINBIO_ANSI_381_POS_LH_LITTLE_FINGER);
    end;
  end
  else if PageControl1.ActivePage = tabEnroll then
  begin
    // ... right
    if optRH_THUMB.Checked then
      FingerPrint.EnrollBiometric(WINBIO_ANSI_381_POS_RH_THUMB)
    else if optRH_INDEX_FINGER.Checked then
      FingerPrint.EnrollBiometric(WINBIO_ANSI_381_POS_RH_INDEX_FINGER)
    else if optRH_MIDDLE_FINGER.Checked then
      FingerPrint.EnrollBiometric(WINBIO_ANSI_381_POS_RH_MIDDLE_FINGER)
    else if optRH_RING_FINGER.Checked then
      FingerPrint.EnrollBiometric(WINBIO_ANSI_381_POS_RH_RING_FINGER)
    else if optRH_LITTLE_FINGER.Checked then
      FingerPrint.EnrollBiometric(WINBIO_ANSI_381_POS_RH_LITTLE_FINGER)
    // ... left
    else if optLH_THUMB.Checked then
      FingerPrint.EnrollBiometric(WINBIO_ANSI_381_POS_LH_THUMB)
    else if optLH_INDEX_FINGER.Checked then
      FingerPrint.EnrollBiometric(WINBIO_ANSI_381_POS_LH_INDEX_FINGER)
    else if optLH_MIDDLE_FINGER.Checked then
      FingerPrint.EnrollBiometric(WINBIO_ANSI_381_POS_LH_MIDDLE_FINGER)
    else if optLH_RING_FINGER.Checked then
      FingerPrint.EnrollBiometric(WINBIO_ANSI_381_POS_LH_RING_FINGER)
    else if optLH_LITTLE_FINGER.Checked then
      FingerPrint.EnrollBiometric(WINBIO_ANSI_381_POS_LH_LITTLE_FINGER);
  end;
end;

procedure TFRMFingerPrint.btnPreviousClick(Sender: TObject);
begin
  if PageControl1.ActivePage = tabEnroll then
    PageControl1.ActivePage := tabStart
  ELSE if PageControl1.ActivePage = tabDeleteTemplate then
    PageControl1.ActivePage := tabStart
  else if PageControl1.ActivePage = tabSensors then
    PageControl1.ActivePage := tabStart;
end;

procedure TFRMFingerPrint.chkAsynchronousClick(Sender: TObject);
begin
  FingerPrint.Asynchronous := chkAsynchronous.Checked;
end;

procedure TFRMFingerPrint.DoMessage(const aText: string; const aColor:
    TColor = clGreen);
begin
  lblLog.Caption := aText;
  lblLog.Font.Color := aColor;
  Application.ProcessMessages;
end;

procedure TFRMFingerPrint.DoLog(const aText: string);
begin
  memoLog.Lines.Add(aText);
end;

procedure TFRMFingerPrint.DoReadINI;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    StorageFile.StorageOptions.DatabaseId := oINI.ReadString('STORAGE', 'DatabaseId', '{3478E3EF-0A0E-40C5-9179-F95144C47CE1}');
  Finally
    FreeAndNil(oINI);
  End;
end;


procedure TFRMFingerPrint.StorageFileAddDatabase(Sender: TObject; const aDatabaseId:
    WINBIO_UUID; aUnitId: Integer);
begin
  DoLog('AddDatabase: ' + aDatabaseId.Guid + ' ' + IntToStr(aUnitId));
end;

procedure TFRMFingerPrint.StorageFileRemoveDatabase(Sender: TObject; const aDatabaseId:
    WINBIO_UUID);
begin
  DoLog('RemoveDatabase: ' +aDatabaseId.Guid);
end;

procedure TFRMFingerPrint.StorageFileAddUnit(Sender: TObject; const aDatabaseId:
    WINBIO_UUID; aUnitId: Integer);
begin
  DoLog('AddUnit: ' + aDatabaseId.Guid + ' ' + IntToStr(aUnitId));
end;

procedure TFRMFingerPrint.FingerPrintAfterInitializeStorage(Sender: TObject; const
    aDatabaseId: WINBIO_GUID);
begin
  DoLog('Start Biometric Service');
  ExecAndWait('net start WbioSrvc', True);

  DoLog('Restart Biometric Service');
  // ... do full service restart
  ExecAndWait('net stop WbioSrvc', True);
  sleep(3000);
  ExecAndWait('net start WbioSrvc', True);
  sleep(3000);

  DoLog('Application must be restarted!!!');
  sleep(3000);
  Halt(0);
end;


procedure TFRMFingerPrint.FingerPrintBeforeInitializeStorage(Sender: TObject; const
    aDatabaseId: WINBIO_GUID);
begin
  DoLog('Stop Biometric Service');
  ExecAndWait('net stop WbioSrvc', True);
end;

procedure TFRMFingerPrint.FingerPrintCancel(Sender: TObject; const
    aSession: Cardinal);
begin
  DoLog('Cancelled operation.');
end;

procedure TFRMFingerPrint.FingerPrintCaptureSample(Sender: TObject; const
    aSample: WINBIO_BIR; const aHeader: WINBIO_BIR_HEADER; const
    aAnsiBdbHeader: WINBIO_BDB_ANSI_381_HEADER; const aAnsiBdbRecord:
    WINBIO_BDB_ANSI_381_RECORD; const aFirstPixel: PByte);
var
  x, y: integer;
  oBMP: TBitmap;
  oByte: Byte;
  vFilePath: String;
begin
  DoLog('Sample captured: ' +
    'Width --> ' + IntToStr(aAnsiBdbHeader.VerticalScanResolution) + ' ' +
    'Height --> ' + IntToStr(aAnsiBdbHeader.HorizontalImageResolution) + ' ' +
    'PixelDepth --> ' + IntToStr(aAnsiBdbHeader.PixelDepth));

  oBMP := TBitmap.Create;
  Try
    oBMP.SetSize(aAnsiBdbHeader.VerticalScanResolution, aAnsiBdbHeader.HorizontalImageResolution);
    oBMP.PixelFormat := pf8bit;
    for y := 0 to aAnsiBdbRecord.VerticalLineLength - 1 do
    begin
      for x := 0 to aAnsiBdbRecord.HorizontalLineLength - 1 do
      begin
        oByte := aFirstPixel[(y * aAnsiBdbHeader.VerticalScanResolution) + x];
        oBMP.Canvas.Pixels[x, y] := RGB(oByte, oByte, oByte);
      end;
    end;
    vFilePath := IncludeTrailingPathDelimiter(GetEnvironmentVariable('TEMP')) + 'fingerprint.bmp';
    oBMP.SaveToFile(vFilePath);
    imgFingerprint.Picture.LoadFromFile(vFilePath);
  Finally
    FreeAndNil(oBMP);
  End;
end;

procedure TFRMFingerPrint.FingerPrintCaptureSampleReject(Sender: TObject; const
    aSample: WINBIO_BIR; aRejectDetail: WINBIO_REJECT_DETAIL);
begin
  DoLog('Bad Capture Sample');
end;

procedure TFRMFingerPrint.FingerPrintCloseSession(Sender: TObject; const
    aSession: Cardinal);
begin
  DoLog('Session Closed');
end;


procedure TFRMFingerPrint.StorageFileRemoveUnit(Sender: TObject; const aDatabaseId:
    WINBIO_UUID; aUnitId: Integer);
begin
  DoLog('RemoveUnit: ' + aDatabaseId.Guid + ' ' + IntToStr(aUnitId));
end;

procedure TFRMFingerPrint.FingerPrintEnrollBegin(Sender: TObject);
var
  vMessage: string;
begin
  vMessage := 'Begin Enrollment';
  DoLog(vMessage);
  DoMessage(vMessage);
end;


procedure TFRMFingerPrint.FingerPrintEnrollCapture(Sender: TObject; aSwipes: Integer;
    const aResult: WINBIO_ENROLL_RESULT; const aRejectDetail:
    WINBIO_REJECT_DETAIL);
var
  vMessage: string;
begin
  case aResult of
    WINBIO_ENROLL_RESULT_OK:
    begin
      vMessage := Format('Enrollment complete with %d swipes.', [aSwipes]);
      DoMessage(vMessage);
      DoLog(vMessage);
      sleep(3000);
      PageControl1.ActivePage := tabStart;
    end;
    WINBIO_ENROLL_RESULT_BAD_CAPTURE:
    begin
      vMessage := Format('Swipe %d was bad.', [aSwipes]);
      DoMessage(vMessage, clRed);
      DoLog(vMessage);
    end;
    WINBIO_ENROLL_RESULT_MORE_DATA:
    begin
      vMessage := Format('Swipe %d was good.', [aSwipes]);
      DoMessage(vMessage);
      DoLog(vMessage);
    end;
  end;
end;



procedure TFRMFingerPrint.FingerPrintEnrollCommit(Sender: TObject; const aIdentity:
    WINBIO_IDENTITY; aIsNewTemplate: Boolean);
var
  vMessage: string;
begin
  vMessage := 'Committing enrollment..';
  if aIsNewTemplate then
    vMessage := 'New template committed.'
  else
    vMessage := 'Template updated.';
  DoLog(vMessage);
  DoMessage(vMessage);
end;



procedure TFRMFingerPrint.FingerPrintEnumBiometricUnit(Sender: TObject; const aUnit:
    WINBIO_UNIT_SCHEMA; const aNum: Integer; const aCount: Integer);
begin
  if aNum = 1 then
  begin
    DoLog('Using unit id: ' + IntToStr(aUnit.UnitId));
    DoLog('Device instance id: ' + aUnit.DeviceInstanceId);
    if FingerPrint.Storage <> nil then
      DoLog('Using database: ' +  StorageFile.StorageOptions.DatabaseId);
  end;
end;

procedure TFRMFingerPrint.FingerPrintEnumDatabase(Sender: TObject; const aStorage:
    WINBIO_STORAGE_SCHEMA; const aNum, aCount: Integer);
begin
  DoLog(Format('DatabaseId %d: %s', [aNum, aStorage.DatabaseId]));
end;

procedure TFRMFingerPrint.FingerPrintEnumEnrollments(Sender: TObject; const
    aIdentity: WINBIO_IDENTITY; const aSubFactor: WINBIO_BIOMETRIC_SUBTYPE;
    const aNum, aCount: Integer);
var
  vSubFactor: string;
begin
  case aSubfactor of
    WINBIO_ANSI_381_POS_RH_THUMB: vSubFactor := 'RH_THUMB';
    WINBIO_ANSI_381_POS_RH_INDEX_FINGER: vSubFactor := 'RH_INDEX_FINGER';
    WINBIO_ANSI_381_POS_RH_MIDDLE_FINGER: vSubFactor := 'RH_MIDDLE_FINGER';
    WINBIO_ANSI_381_POS_RH_RING_FINGER: vSubFactor := 'RH_RING_FINGER';
    WINBIO_ANSI_381_POS_RH_LITTLE_FINGER: vSubFactor := 'RH_LITTLE_FINGER';
    WINBIO_ANSI_381_POS_LH_THUMB: vSubFactor := 'LH_THUMB';
    WINBIO_ANSI_381_POS_LH_INDEX_FINGER: vSubFactor := 'LH_INDEX_FINGER';
    WINBIO_ANSI_381_POS_LH_MIDDLE_FINGER: vSubFactor := 'LH_MIDDLE_FINGER';
    WINBIO_ANSI_381_POS_LH_RING_FINGER: vSubFactor := 'LH_RING_FINGER';
    WINBIO_ANSI_381_POS_LH_LITTLE_FINGER: vSubFactor := 'LH_LITTLE_FINGER';
  end;
  DoLog('EnumEnrollment: ' + vSubFactor);
end;

procedure TFRMFingerPrint.FingerPrintError(Sender: TObject; const aError:
    string; const aCode: Integer);
begin
  DoLog('Error: ' + aError + ' [' + IntToStr(aCode) + ']');
  DoMessage(aError, clRed);
end;

procedure TFRMFingerPrint.FingerPrintIdentify(Sender: TObject; const aUnitId:
    Integer; const aIdentity: WINBIO_IDENTITY; const aSubFactor:
    WINBIO_BIOMETRIC_SUBTYPE; const aRejectDetail: WINBIO_REJECT_DETAIL);
var
  vId: String;
  vSubFactor: String;
  vMessage: String;
begin
  Case aIdentity._Type of
    WINBIO_ID_TYPE_SID: vId :=  aIdentity.AccountSid.Data;
    WINBIO_ID_TYPE_GUID: vId :=  aIdentity.TemplateGuid.Guid;
    else
      vId := '';
  End;

  case aSubfactor of
    WINBIO_ANSI_381_POS_RH_THUMB: vSubFactor := 'RH_THUMB';
    WINBIO_ANSI_381_POS_RH_INDEX_FINGER: vSubFactor := 'RH_INDEX_FINGER';
    WINBIO_ANSI_381_POS_RH_MIDDLE_FINGER: vSubFactor := 'RH_MIDDLE_FINGER';
    WINBIO_ANSI_381_POS_RH_RING_FINGER: vSubFactor := 'RH_RING_FINGER';
    WINBIO_ANSI_381_POS_RH_LITTLE_FINGER: vSubFactor := 'RH_LITTLE_FINGER';
    WINBIO_ANSI_381_POS_LH_THUMB: vSubFactor := 'LH_THUMB';
    WINBIO_ANSI_381_POS_LH_INDEX_FINGER: vSubFactor := 'LH_INDEX_FINGER';
    WINBIO_ANSI_381_POS_LH_MIDDLE_FINGER: vSubFactor := 'LH_MIDDLE_FINGER';
    WINBIO_ANSI_381_POS_LH_RING_FINGER: vSubFactor := 'LH_RING_FINGER';
    WINBIO_ANSI_381_POS_LH_LITTLE_FINGER: vSubFactor := 'LH_LITTLE_FINGER';
  end;

  if vId <> '' then
  begin
    vMessage := 'Identified: ' + vId + ' ' + vSubFactor;
    DoMessage(vMessage);
    DoLog(vMessage);
  end;
end;


procedure TFRMFingerPrint.FingerPrintOpenSession(Sender: TObject; const aSession:
    WINBIO_SESSION_HANDLE);
begin
  DoLog('Open Session');
end;


procedure TFRMFingerPrint.FingerPrintSensorLocated(Sender: TObject; const aUnitId:
    Integer);
var
  vMessage: string;
begin
  vMessage := 'Sensor Located: ' + IntToStr(aUnitId);
  DoMessage(vMessage);
  DoLog(vMessage);
end;

procedure TFRMFingerPrint.FingerPrintTemplateDeleted(Sender: TObject; const
    aUnitId: Integer; const aIdentity: WINBIO_IDENTITY; const aSubFactor:
    WINBIO_BIOMETRIC_SUBTYPE);
var
  vId: String;
  vSubFactor: String;
  vMessage: String;
begin
  Case aIdentity._Type of
    WINBIO_ID_TYPE_SID: vId :=  aIdentity.AccountSid.Data;
    WINBIO_ID_TYPE_GUID: vId :=  aIdentity.TemplateGuid.Guid;
    else
      vId := '';
  End;

  case aSubfactor of
    WINBIO_ANSI_381_POS_RH_THUMB: vSubFactor := 'RH_THUMB';
    WINBIO_ANSI_381_POS_RH_INDEX_FINGER: vSubFactor := 'RH_INDEX_FINGER';
    WINBIO_ANSI_381_POS_RH_MIDDLE_FINGER: vSubFactor := 'RH_MIDDLE_FINGER';
    WINBIO_ANSI_381_POS_RH_RING_FINGER: vSubFactor := 'RH_RING_FINGER';
    WINBIO_ANSI_381_POS_RH_LITTLE_FINGER: vSubFactor := 'RH_LITTLE_FINGER';
    WINBIO_ANSI_381_POS_LH_THUMB: vSubFactor := 'LH_THUMB';
    WINBIO_ANSI_381_POS_LH_INDEX_FINGER: vSubFactor := 'LH_INDEX_FINGER';
    WINBIO_ANSI_381_POS_LH_MIDDLE_FINGER: vSubFactor := 'LH_MIDDLE_FINGER';
    WINBIO_ANSI_381_POS_LH_RING_FINGER: vSubFactor := 'LH_RING_FINGER';
    WINBIO_ANSI_381_POS_LH_LITTLE_FINGER: vSubFactor := 'LH_LITTLE_FINGER';
  end;

  if vId <> '' then
  begin
    vMessage := 'Template Deleted: ' + vId + ' ' + vSubFactor;
    DoMessage(vMessage);
    DoLog(vMessage);
  end;
end;

procedure TFRMFingerPrint.StorageFileError(Sender: TObject; const aError:
    string; const aCode: Integer);
begin
  DoLog('Error: ' + aError + ' [' + IntToStr(aCode) + ']');
end;

procedure TFRMFingerPrint.tabCaptureSampleShow(Sender: TObject);
begin
  DoLog('captureSample');
end;

procedure TFRMFingerPrint.tabEnrollShow(Sender: TObject);
begin
  DoMessage('Select a Finger and Press Next', clBlack);
end;

procedure TFRMFingerPrint.tabPrivatePoolSensorShow(Sender: TObject);
var
  vStorageExists: Boolean;
begin
  btnPrevious.Enabled := True;

  vStorageExists := StorageFile.StorageExists;

  optCreateStorage.Enabled := not vStorageExists;
  optOpenStorage.Enabled := vStorageExists;
  optOpenStorage.Checked := vStorageExists;
  optRebuildStorage.Enabled := vStorageExists;

  DoMessage('Select an option', clBlack);
end;

procedure TFRMFingerPrint.tabSensorsShow(Sender: TObject);
begin
  DoMessage('Select an option', clBlack);
  
  btnPrevious.Enabled := True;

  if FingerPrint.SessionIsOpen then
    FingerPrint.CloseSession;
  FingerPrint.InitializeSensors;
end;

procedure TFRMFingerPrint.tabStartShow(Sender: TObject);
begin
  btnPrevious.Enabled := False;

  DoMessage('Select an option', clBlack);
end;

end.
```

