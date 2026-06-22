# SpecFirst

Featured demo. Full source of every unit.

Demo: `30.Server/02.SpecFirst`

### FOpenAPI_Server_SpecFirst.pas

```pascal
{ ***************************************************************************
  sgcOpenAPI component

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit FOpenAPI_Server_SpecFirst;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls,
  // sgc
  sgcBase_Classes, sgcHTTP_OpenAPI_Server, sgcHTTP_OpenAPI_Server_Engine,
  sgcHTTPServer_OpenAPI;

type
  TFRMOpenAPIServerSpecFirst = class(TForm)
    pnlTop: TPanel;
    lblTitle: TLabel;
    lblHost: TLabel;
    lblPort: TLabel;
    lblSpec: TLabel;
    lblInfo: TLabel;
    txtHost: TEdit;
    txtPort: TEdit;
    txtSpecFile: TEdit;
    btnStart: TButton;
    btnStop: TButton;
    chkCORS: TCheckBox;
    chkValidation: TCheckBox;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
  private
    FOpenAPI: TsgcHTTPServer_OpenAPI;
    FPets: TStringList;
    FNextId: Integer;
    procedure DoLog(const aText: string);
    procedure OnOpenAPIRequest(Sender: TObject; const aOperationId: string;
      const aContext: TsgcOpenAPIServerContext; var Handled: Boolean);
    procedure OnOpenAPIBeforeRequest(Sender: TObject;
      const aOperationId: string; const aContext: TsgcOpenAPIServerContext;
      var Accept: Boolean);
    procedure OnOpenAPIValidationError(Sender: TObject;
      const aOperationId: string; const aErrors: TStringList;
      const aContext: TsgcOpenAPIServerContext; var Continue: Boolean);
    procedure HandleListPets(const aContext: TsgcOpenAPIServerContext);
    procedure HandleCreatePet(const aContext: TsgcOpenAPIServerContext);
    procedure HandleGetPetById(const aContext: TsgcOpenAPIServerContext);
    procedure HandleDeletePet(const aContext: TsgcOpenAPIServerContext);
  end;

var
  FRMOpenAPIServerSpecFirst: TFRMOpenAPIServerSpecFirst;

implementation

{$R *.dfm}

procedure TFRMOpenAPIServerSpecFirst.FormCreate(Sender: TObject);
begin
  FPets := TStringList.Create;
  FNextId := 1;

  // Pre-populate some pets as JSON strings keyed by ID
  FPets.Add('1={"id":1,"name":"Rex","tag":"dog"}');
  FPets.Add('2={"id":2,"name":"Whiskers","tag":"cat"}');
  FPets.Add('3={"id":3,"name":"Goldie","tag":"fish"}');
  FNextId := 4;

  // Create OpenAPI server API component
  FOpenAPI := TsgcHTTPServer_OpenAPI.Create(Self);
  FOpenAPI.OnRequest := OnOpenAPIRequest;
  FOpenAPI.OnBeforeRequest := OnOpenAPIBeforeRequest;
  FOpenAPI.OnValidationError := OnOpenAPIValidationError;
end;

procedure TFRMOpenAPIServerSpecFirst.FormDestroy(Sender: TObject);
begin
  FPets.Free;
end;

procedure TFRMOpenAPIServerSpecFirst.DoLog(const aText: string);
begin
  TThread.Queue(nil, procedure
    begin
      if Assigned(memoLog) then
      begin
        memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ' ' + aText);
        // Auto-scroll
        SendMessage(memoLog.Handle, EM_LINESCROLL, 0, memoLog.Lines.Count);
      end;
    end);
end;

procedure TFRMOpenAPIServerSpecFirst.btnStartClick(Sender: TObject);
begin
  // Configure server
  FOpenAPI.Bindings.Clear;
  with FOpenAPI.Bindings.Add do
  begin
    Port := StrToInt(txtPort.Text);
    IP := txtHost.Text;
  end;

  // Configure OpenAPI options
  FOpenAPI.OpenAPIOptions.Endpoint.ServeSpec := True;
  FOpenAPI.OpenAPIOptions.Endpoint.ServeSwaggerUI := True;
  FOpenAPI.OpenAPIOptions.CORS.Enabled := chkCORS.Checked;
  FOpenAPI.OpenAPIOptions.Validation.ValidateRequest := chkValidation.Checked;
  FOpenAPI.OpenAPIOptions.Validation.ValidateRequired := chkValidation.Checked;
  FOpenAPI.OpenAPIOptions.Validation.ValidateRequestBody :=
    chkValidation.Checked;

  // Load the OpenAPI spec
  FOpenAPI.LoadFromFile(ExtractFilePath(Application.ExeName) +
    txtSpecFile.Text);
  DoLog('OpenAPI spec loaded: ' + txtSpecFile.Text);

  // Start
  FOpenAPI.Active := True;
  DoLog('Server started on ' + txtHost.Text + ':' + txtPort.Text);
  DoLog('Swagger UI: http://localhost:' + txtPort.Text + '/docs');
  DoLog('OpenAPI Spec: http://localhost:' + txtPort.Text + '/openapi.json');
  DoLog('');
  DoLog('Endpoints:');
  DoLog('  GET    /pets          - List all pets');
  DoLog('  POST   /pets          - Create a pet');
  DoLog('  GET    /pets/{petId}  - Get pet by ID');
  DoLog('  DELETE /pets/{petId}  - Delete a pet');
  DoLog('---');

  btnStart.Enabled := False;
  btnStop.Enabled := True;
end;

procedure TFRMOpenAPIServerSpecFirst.btnStopClick(Sender: TObject);
begin
  FOpenAPI.Active := False;
  DoLog('Server stopped.');
  btnStart.Enabled := True;
  btnStop.Enabled := False;
end;

{ Event Handlers }

procedure TFRMOpenAPIServerSpecFirst.OnOpenAPIBeforeRequest(Sender: TObject;
const aOperationId: string; const aContext: TsgcOpenAPIServerContext;
var Accept: Boolean);
begin
  DoLog('>> ' + aContext.Request.Method + ' ' + aContext.Request.Document + ' ['
    + aOperationId + ']');
  Accept := True;
end;

procedure TFRMOpenAPIServerSpecFirst.OnOpenAPIValidationError(Sender: TObject;
const aOperationId: string; const aErrors: TStringList;
const aContext: TsgcOpenAPIServerContext; var Continue: Boolean);
var
  i: Integer;
begin
  DoLog('!! Validation failed for ' + aOperationId + ':');
  for i := 0 to aErrors.Count - 1 do
    DoLog('   - ' + aErrors[i]);
  Continue := False; // reject the request
end;

procedure TFRMOpenAPIServerSpecFirst.OnOpenAPIRequest(Sender: TObject;
const aOperationId: string; const aContext: TsgcOpenAPIServerContext;
var Handled: Boolean);
begin
  Handled := True;

  if aOperationId = 'listPets' then
    HandleListPets(aContext)
  else if aOperationId = 'createPet' then
    HandleCreatePet(aContext)
  else if aOperationId = 'getPetById' then
    HandleGetPetById(aContext)
  else if aOperationId = 'deletePet' then
    HandleDeletePet(aContext)
  else
  begin
    Handled := False;
    DoLog('<< 501 Not Implemented: ' + aOperationId);
  end;
end;

{ Business Logic Handlers }

procedure TFRMOpenAPIServerSpecFirst.HandleListPets(const aContext
  : TsgcOpenAPIServerContext);
var
  i: Integer;
  vLimit: Integer;
  vResult: string;
  vCount: Integer;
begin
  vLimit := aContext.QueryParamAsInteger('limit', 100);
  vResult := '[';
  vCount := 0;

  for i := 0 to FPets.Count - 1 do
  begin
    if vCount >= vLimit then
      break;
    if i > 0 then
      vResult := vResult + ',';
    vResult := vResult + FPets.ValueFromIndex[i];
    Inc(vCount);
  end;

  vResult := vResult + ']';
  aContext.RespondJSON(200, vResult);
  DoLog('<< 200 OK - Listed ' + IntToStr(vCount) + ' pets');
end;

procedure TFRMOpenAPIServerSpecFirst.HandleCreatePet(const aContext
  : TsgcOpenAPIServerContext);
var
  vBody, vName, vTag: string;
  vId: Integer;
  vPetJSON: string;
begin
  vBody := aContext.BodyAsString;
  vId := FNextId;
  Inc(FNextId);

  // Simple JSON parsing - extract name and tag
  vName := '';
  vTag := '';
  // Use basic string extraction (demo purposes)
  if Pos('"name"', vBody) > 0 then
  begin
    vName := Copy(vBody, Pos('"name"', vBody) + 7, 100);
    if Pos('"', vName) > 0 then
    begin
      Delete(vName, 1, Pos('"', vName));
      vName := Copy(vName, 1, Pos('"', vName) - 1);
    end;
  end;
  if Pos('"tag"', vBody) > 0 then
  begin
    vTag := Copy(vBody, Pos('"tag"', vBody) + 6, 100);
    if Pos('"', vTag) > 0 then
    begin
      Delete(vTag, 1, Pos('"', vTag));
      vTag := Copy(vTag, 1, Pos('"', vTag) - 1);
    end;
  end;

  vPetJSON := '{"id":' + IntToStr(vId) + ',"name":"' + vName + '"';
  if vTag <> '' then
    vPetJSON := vPetJSON + ',"tag":"' + vTag + '"';
  vPetJSON := vPetJSON + '}';

  FPets.Add(IntToStr(vId) + '=' + vPetJSON);

  aContext.Response.Code := 201;
  aContext.Response.ContentType := 'application/json';
  aContext.Response.Content := vPetJSON;
  DoLog('<< 201 Created - Pet #' + IntToStr(vId) + ': ' + vName);
end;

procedure TFRMOpenAPIServerSpecFirst.HandleGetPetById(const aContext
  : TsgcOpenAPIServerContext);
var
  vId: string;
  vPetJSON: string;
begin
  vId := aContext.PathParamAsString('petId');
  vPetJSON := FPets.Values[vId];

  if vPetJSON <> '' then
  begin
    aContext.RespondJSON(200, vPetJSON);
    DoLog('<< 200 OK - Pet #' + vId);
  end
  else
  begin
    aContext.RespondError(404, 'Not Found', 'Pet with id ' + vId +
      ' not found');
    DoLog('<< 404 Not Found - Pet #' + vId);
  end;
end;

procedure TFRMOpenAPIServerSpecFirst.HandleDeletePet(const aContext
  : TsgcOpenAPIServerContext);
var
  vId: string;
  i: Integer;
  vFound: Boolean;
begin
  vId := aContext.PathParamAsString('petId');
  vFound := False;

  for i := FPets.Count - 1 downto 0 do
  begin
    if FPets.Names[i] = vId then
    begin
      FPets.Delete(i);
      vFound := True;
      break;
    end;
  end;

  if vFound then
  begin
    aContext.Response.Code := 204;
    aContext.Response.Content := '';
    DoLog('<< 204 No Content - Deleted Pet #' + vId);
  end
  else
  begin
    aContext.RespondError(404, 'Not Found', 'Pet with id ' + vId +
      ' not found');
    DoLog('<< 404 Not Found - Pet #' + vId);
  end;
end;

end.
```

