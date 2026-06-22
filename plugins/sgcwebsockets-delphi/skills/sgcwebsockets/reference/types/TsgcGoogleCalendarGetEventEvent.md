# TsgcGoogleCalendarGetEventEvent

kind: event handler type
unit: sgcHTTP_Google_Calendar

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aCalendar: TsgcGoogleCalendarItem; const aEvent: TsgcGoogleCalendarEventItem; var Accept: Boolean) of object
```

