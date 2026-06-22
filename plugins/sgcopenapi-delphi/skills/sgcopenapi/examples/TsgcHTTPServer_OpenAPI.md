# TsgcHTTPServer_OpenAPI - Example

Full source of `FOpenAPI_Server_CodeFirst.pas` from the **30.Server/01.CodeFirst** demo, which uses `TsgcHTTPServer_OpenAPI`.

API reference: [TsgcHTTPServer_OpenAPI](../reference/api/TsgcHTTPServer_OpenAPI.md)
Source demo: `30.Server/01.CodeFirst` (file `FOpenAPI_Server_CodeFirst.pas`)

```pascal
{ ***************************************************************************
  sgcOpenAPI component

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit FOpenAPI_Server_CodeFirst;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls,
  // sgc
  sgcBase_Classes, sgcHTTP_OpenAPI_Server, sgcHTTP_OpenAPI_Server_CodeFirst,
  sgcHTTP_OpenAPI_Server_Engine, sgcHTTPServer_OpenAPI;

type

  { --- Define the API using attributes --- }

  [sgcServiceContract('Task Manager API',
    'A simple task management demo using code-first OpenAPI', '1.0.0')]
  [sgcRoute('/api/v1')]
  TTaskManagerService = class
  public
    [sgcHttpGet]
    [sgcRoute('/tasks')]
    [sgcSummary('List all tasks')]
    [sgcDescription
      ('Returns a list of all tasks, optionally filtered by status')]
    [sgcTag('Tasks')]
    [sgcResponse(200, 'A list of tasks')]
    procedure ListTasks([sgcFromQuery] const status: string); virtual;

    [sgcHttpPost]
    [sgcRoute('/tasks')]
    [sgcSummary('Create a new task')]
    [sgcDescription('Creates a new task with the given title and description')]
    [sgcTag('Tasks')]
    [sgcResponse(201, 'Task created successfully')]
    procedure CreateTask([sgcFromBody] const body: string); virtual;

    [sgcHttpGet]
    [sgcRoute('/tasks/{taskId}')]
    [sgcSummary('Get a task by ID')]
    [sgcDescription('Returns a single task by its unique identifier')]
    [sgcTag('Tasks')]
    [sgcResponse(200, 'The requested task')]
    [sgcResponse(404, 'Task not found')]
    procedure GetTask([sgcFromPath][sgcRequired] const taskId
      : Integer); virtual;

    [sgcHttpPut]
    [sgcRoute('/tasks/{taskId}')]
    [sgcSummary('Update a task')]
    [sgcDescription('Updates an existing task')]
    [sgcTag('Tasks')]
    [sgcResponse(200, 'Task updated')]
    [sgcResponse(404, 'Task not found')]
    procedure UpdateTask([sgcFromPath][sgcRequired] const taskId: Integer;
      [sgcFromBody] const body: string); virtual;

    [sgcHttpDelete]
    [sgcRoute('/tasks/{taskId}')]
    [sgcSummary('Delete a task')]
    [sgcTag('Tasks')]
    [sgcResponse(204, 'Task deleted')]
    [sgcResponse(404, 'Task not found')]
    procedure DeleteTask([sgcFromPath][sgcRequired] const taskId
      : Integer); virtual;

    [sgcHttpGet]
    [sgcRoute('/tasks/stats')]
    [sgcSummary('Get task statistics')]
    [sgcDescription('Returns counts of tasks by status')]
    [sgcTag('Statistics')]
    [sgcResponse(200, 'Task statistics')]
    procedure GetStats; virtual;
  end;

  { --- Main Form --- }

  TFRMOpenAPIServerCodeFirst = class(TForm)
    pnlTop: TPanel;
    lblTitle: TLabel;
    lblHost: TLabel;
    lblPort: TLabel;
    lblInfo: TLabel;
    txtHost: TEdit;
    txtPort: TEdit;
    btnStart: TButton;
    btnStop: TButton;
    btnShowSpec: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure btnShowSpecClick(Sender: TObject);
  private
    FOpenAPI: TsgcHTTPServer_OpenAPI;
    FGeneratedSpec: string;
    FTasks: TStringList;
    FNextId: Integer;
    procedure DoLog(const aText: string);
    procedure OnOpenAPIRequest(Sender: TObject; const aOperationId: string;
      const aContext: TsgcOpenAPIServerContext; var Handled: Boolean);
    procedure OnOpenAPIBeforeRequest(Sender: TObject;
      const aOperationId: string; const aContext: TsgcOpenAPIServerContext;
      var Accept: Boolean);
    procedure HandleListTasks(const aContext: TsgcOpenAPIServerContext);
    procedure HandleCreateTask(const aContext: TsgcOpenAPIServerContext);
    procedure HandleGetTask(const aContext: TsgcOpenAPIServerContext);
    procedure HandleUpdateTask(const aContext: TsgcOpenAPIServerContext);
    procedure HandleDeleteTask(const aContext: TsgcOpenAPIServerContext);
    procedure HandleGetStats(const aContext: TsgcOpenAPIServerContext);
  end;

var
  FRMOpenAPIServerCodeFirst: TFRMOpenAPIServerCodeFirst;

implementation

{$R *.dfm}
{ TTaskManagerService - empty implementations (these are just for RTTI scanning) }

procedure TTaskManagerService.ListTasks(const status: string);
begin
  // Stub - actual logic is in the form's event handler
end;

procedure TTaskManagerService.CreateTask(const body: string);
begin
end;

procedure TTaskManagerService.GetTask(const taskId: Integer);
begin
end;

procedure TTaskManagerService.UpdateTask(const taskId: Integer;
  const body: string);
begin
end;

procedure TTaskManagerService.DeleteTask(const taskId: Integer);
begin
end;

procedure TTaskManagerService.GetStats;
begin
end;

{ TFRMOpenAPIServerCodeFirst }

procedure TFRMOpenAPIServerCodeFirst.FormCreate(Sender: TObject);
begin
  FTasks := TStringList.Create;
  FNextId := 1;

  // Pre-populate some tasks
  FTasks.Add
    ('1={"id":1,"title":"Buy groceries","description":"Milk, eggs, bread","status":"pending"}');
  FTasks.Add
    ('2={"id":2,"title":"Write report","description":"Q1 sales report","status":"in_progress"}');
  FTasks.Add
    ('3={"id":3,"title":"Fix login bug","description":"Users cannot login with SSO","status":"done"}');
  FNextId := 4;

  // Create OpenAPI component
  FOpenAPI := TsgcHTTPServer_OpenAPI.Create(Self);
  FOpenAPI.OnRequest := OnOpenAPIRequest;
  FOpenAPI.OnBeforeRequest := OnOpenAPIBeforeRequest;
  FOpenAPI.OpenAPIOptions.Endpoint.ServeSpec := True;
  FOpenAPI.OpenAPIOptions.Endpoint.ServeSwaggerUI := True;
  FOpenAPI.OpenAPIOptions.CORS.Enabled := True;
end;

procedure TFRMOpenAPIServerCodeFirst.FormDestroy(Sender: TObject);
begin
  FTasks.Free;
end;

procedure TFRMOpenAPIServerCodeFirst.DoLog(const aText: string);
begin
  TThread.Queue(nil, procedure
    begin
      if Assigned(memoLog) then
      begin
        memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ' ' + aText);
        SendMessage(memoLog.Handle, EM_LINESCROLL, 0, memoLog.Lines.Count);
      end;
    end);
end;

procedure TFRMOpenAPIServerCodeFirst.btnStartClick(Sender: TObject);
var
  oScanner: TsgcOpenAPICodeFirstScanner;
begin
  // Step 1: Generate OpenAPI spec from the annotated class via RTTI
  oScanner := TsgcOpenAPICodeFirstScanner.Create;
  try
    FGeneratedSpec := oScanner.GenerateSpec(TTaskManagerService);
  finally
    oScanner.Free;
  end;

  DoLog('OpenAPI spec generated from TTaskManagerService attributes');
  DoLog('Spec size: ' + IntToStr(Length(FGeneratedSpec)) + ' bytes');

  // Step 2: Load the generated spec into the OpenAPI server component
  FOpenAPI.LoadFromString(FGeneratedSpec);
  DoLog('Spec loaded into OpenAPI server component');

  // Step 3: Configure and start the HTTP server
  FOpenAPI.Bindings.Clear;
  with FOpenAPI.Bindings.Add do
  begin
    Port := StrToInt(txtPort.Text);
    IP := txtHost.Text;
  end;
  FOpenAPI.Active := True;

  DoLog('Server started on ' + txtHost.Text + ':' + txtPort.Text);
  DoLog('Swagger UI: http://localhost:' + txtPort.Text + '/docs');
  DoLog('');
  DoLog('Endpoints (auto-generated from attributes):');
  DoLog('  GET    /api/v1/tasks          - List tasks');
  DoLog('  POST   /api/v1/tasks          - Create task');
  DoLog('  GET    /api/v1/tasks/{taskId}  - Get task');
  DoLog('  PUT    /api/v1/tasks/{taskId}  - Update task');
  DoLog('  DELETE /api/v1/tasks/{taskId}  - Delete task');
  DoLog('  GET    /api/v1/tasks/stats     - Statistics');
  DoLog('---');

  btnStart.Enabled := False;
  btnStop.Enabled := True;
end;

procedure TFRMOpenAPIServerCodeFirst.btnStopClick(Sender: TObject);
begin
  FOpenAPI.Active := False;
  DoLog('Server stopped.');
  btnStart.Enabled := True;
  btnStop.Enabled := False;
end;

procedure TFRMOpenAPIServerCodeFirst.btnShowSpecClick(Sender: TObject);
var
  oScanner: TsgcOpenAPICodeFirstScanner;
begin
  if FGeneratedSpec = '' then
  begin
    oScanner := TsgcOpenAPICodeFirstScanner.Create;
    try
      FGeneratedSpec := oScanner.GenerateSpec(TTaskManagerService);
    finally
      oScanner.Free;
    end;
  end;

  memoLog.Lines.Clear;
  DoLog('=== Generated OpenAPI Spec ===');
  DoLog(FGeneratedSpec);
  DoLog('=== End of Spec ===');
end;

{ Event Handlers }

procedure TFRMOpenAPIServerCodeFirst.OnOpenAPIBeforeRequest(Sender: TObject;
const aOperationId: string; const aContext: TsgcOpenAPIServerContext;
var Accept: Boolean);
begin
  DoLog('>> ' + aContext.Request.Method + ' ' + aContext.Request.Document + ' ['
    + aOperationId + ']');
  Accept := True;
end;

procedure TFRMOpenAPIServerCodeFirst.OnOpenAPIRequest(Sender: TObject;
const aOperationId: string; const aContext: TsgcOpenAPIServerContext;
var Handled: Boolean);
begin
  Handled := True;

  if aOperationId = 'ListTasks' then
    HandleListTasks(aContext)
  else if aOperationId = 'CreateTask' then
    HandleCreateTask(aContext)
  else if aOperationId = 'GetTask' then
    HandleGetTask(aContext)
  else if aOperationId = 'UpdateTask' then
    HandleUpdateTask(aContext)
  else if aOperationId = 'DeleteTask' then
    HandleDeleteTask(aContext)
  else if aOperationId = 'GetStats' then
    HandleGetStats(aContext)
  else
  begin
    Handled := False;
    DoLog('<< 501 Not Implemented: ' + aOperationId);
  end;
end;

{ Business Logic }

procedure TFRMOpenAPIServerCodeFirst.HandleListTasks(const aContext
  : TsgcOpenAPIServerContext);
var
  i: Integer;
  vStatus, vResult, vTask: string;
  vCount: Integer;
begin
  vStatus := aContext.QueryParamAsString('status', '');
  vResult := '[';
  vCount := 0;

  for i := 0 to FTasks.Count - 1 do
  begin
    vTask := FTasks.ValueFromIndex[i];
    // Filter by status if specified
    if (vStatus <> '') and (Pos('"status":"' + vStatus + '"', vTask) = 0) then
      continue;
    if vCount > 0 then
      vResult := vResult + ',';
    vResult := vResult + vTask;
    Inc(vCount);
  end;

  vResult := vResult + ']';
  aContext.RespondJSON(200, vResult);
  DoLog('<< 200 OK - Listed ' + IntToStr(vCount) + ' tasks');
end;

procedure TFRMOpenAPIServerCodeFirst.HandleCreateTask(const aContext
  : TsgcOpenAPIServerContext);
var
  vBody, vTitle, vDesc: string;
  vId: Integer;
  vTaskJSON: string;
begin
  vBody := aContext.BodyAsString;
  vId := FNextId;
  Inc(FNextId);

  // Extract title
  vTitle := '';
  if Pos('"title"', vBody) > 0 then
  begin
    vTitle := Copy(vBody, Pos('"title"', vBody) + 8, 200);
    if Pos('"', vTitle) > 0 then
    begin
      Delete(vTitle, 1, Pos('"', vTitle));
      vTitle := Copy(vTitle, 1, Pos('"', vTitle) - 1);
    end;
  end;

  // Extract description
  vDesc := '';
  if Pos('"description"', vBody) > 0 then
  begin
    vDesc := Copy(vBody, Pos('"description"', vBody) + 14, 200);
    if Pos('"', vDesc) > 0 then
    begin
      Delete(vDesc, 1, Pos('"', vDesc));
      vDesc := Copy(vDesc, 1, Pos('"', vDesc) - 1);
    end;
  end;

  vTaskJSON := '{"id":' + IntToStr(vId) + ',"title":"' + vTitle +
    '","description":"' + vDesc + '","status":"pending"}';

  FTasks.Add(IntToStr(vId) + '=' + vTaskJSON);

  aContext.Response.Code := 201;
  aContext.Response.ContentType := 'application/json';
  aContext.Response.Content := vTaskJSON;
  DoLog('<< 201 Created - Task #' + IntToStr(vId) + ': ' + vTitle);
end;

procedure TFRMOpenAPIServerCodeFirst.HandleGetTask(const aContext
  : TsgcOpenAPIServerContext);
var
  vId, vTaskJSON: string;
begin
  vId := aContext.PathParamAsString('taskId');
  vTaskJSON := FTasks.Values[vId];

  if vTaskJSON <> '' then
  begin
    aContext.RespondJSON(200, vTaskJSON);
    DoLog('<< 200 OK - Task #' + vId);
  end
  else
  begin
    aContext.RespondError(404, 'Not Found', 'Task with id ' + vId +
      ' not found');
    DoLog('<< 404 Not Found - Task #' + vId);
  end;
end;

procedure TFRMOpenAPIServerCodeFirst.HandleUpdateTask(const aContext
  : TsgcOpenAPIServerContext);
var
  vId, vBody, vTitle, vDesc, vStatus, vTaskJSON: string;
  i: Integer;
begin
  vId := aContext.PathParamAsString('taskId');

  if FTasks.Values[vId] = '' then
  begin
    aContext.RespondError(404, 'Not Found', 'Task with id ' + vId +
      ' not found');
    DoLog('<< 404 Not Found - Task #' + vId);
    exit;
  end;

  vBody := aContext.BodyAsString;

  // Extract fields
  vTitle := '';
  if Pos('"title"', vBody) > 0 then
  begin
    vTitle := Copy(vBody, Pos('"title"', vBody) + 8, 200);
    if Pos('"', vTitle) > 0 then
    begin
      Delete(vTitle, 1, Pos('"', vTitle));
      vTitle := Copy(vTitle, 1, Pos('"', vTitle) - 1);
    end;
  end;

  vDesc := '';
  if Pos('"description"', vBody) > 0 then
  begin
    vDesc := Copy(vBody, Pos('"description"', vBody) + 14, 200);
    if Pos('"', vDesc) > 0 then
    begin
      Delete(vDesc, 1, Pos('"', vDesc));
      vDesc := Copy(vDesc, 1, Pos('"', vDesc) - 1);
    end;
  end;

  vStatus := 'pending';
  if Pos('"status"', vBody) > 0 then
  begin
    vStatus := Copy(vBody, Pos('"status"', vBody) + 9, 200);
    if Pos('"', vStatus) > 0 then
    begin
      Delete(vStatus, 1, Pos('"', vStatus));
      vStatus := Copy(vStatus, 1, Pos('"', vStatus) - 1);
    end;
  end;

  vTaskJSON := '{"id":' + vId + ',"title":"' + vTitle + '","description":"' +
    vDesc + '","status":"' + vStatus + '"}';

  // Update in list
  for i := 0 to FTasks.Count - 1 do
  begin
    if FTasks.Names[i] = vId then
    begin
      FTasks[i] := vId + '=' + vTaskJSON;
      break;
    end;
  end;

  aContext.RespondJSON(200, vTaskJSON);
  DoLog('<< 200 OK - Updated Task #' + vId);
end;

procedure TFRMOpenAPIServerCodeFirst.HandleDeleteTask(const aContext
  : TsgcOpenAPIServerContext);
var
  vId: string;
  i: Integer;
  vFound: Boolean;
begin
  vId := aContext.PathParamAsString('taskId');
  vFound := False;

  for i := FTasks.Count - 1 downto 0 do
  begin
    if FTasks.Names[i] = vId then
    begin
      FTasks.Delete(i);
      vFound := True;
      break;
    end;
  end;

  if vFound then
  begin
    aContext.Response.Code := 204;
    aContext.Response.Content := '';
    DoLog('<< 204 No Content - Deleted Task #' + vId);
  end
  else
  begin
    aContext.RespondError(404, 'Not Found', 'Task with id ' + vId +
      ' not found');
    DoLog('<< 404 Not Found - Task #' + vId);
  end;
end;

procedure TFRMOpenAPIServerCodeFirst.HandleGetStats(const aContext
  : TsgcOpenAPIServerContext);
var
  i, vPending, vInProgress, vDone: Integer;
  vTask: string;
begin
  vPending := 0;
  vInProgress := 0;
  vDone := 0;

  for i := 0 to FTasks.Count - 1 do
  begin
    vTask := FTasks.ValueFromIndex[i];
    if Pos('"status":"pending"', vTask) > 0 then
      Inc(vPending)
    else if Pos('"status":"in_progress"', vTask) > 0 then
      Inc(vInProgress)
    else if Pos('"status":"done"', vTask) > 0 then
      Inc(vDone);
  end;

  aContext.RespondJSON(200, '{"total":' + IntToStr(FTasks.Count) + ',"pending":'
    + IntToStr(vPending) + ',"in_progress":' + IntToStr(vInProgress) +
    ',"done":' + IntToStr(vDone) + '}');
  DoLog('<< 200 OK - Stats: ' + IntToStr(FTasks.Count) + ' total');
end;

end.
```

