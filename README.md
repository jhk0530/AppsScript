# AppsScript

## code
- `calendarid`, `메일 수신자`, `메일 제목` 수정해서 사용

``` gs
function myFunction() {
  // Calendar
  const id = "[CALENDARID]";
  const calendar = CalendarApp.getCalendarById(id); 
  var sunday = new Date(); 
  var saturday = new Date();
  saturday.setDate(sunday.getDate() + 6);   
  const events = calendar.getEvents(sunday, saturday);

  // Gmail
    const recipient = '[메일 수신자]';
    const subject = '[메일 제목];
    let body = '';
    for (const event of events) {
      body += event.getStartTime().toLocaleDateString('ko-KR', {weekday:'long'}) + ': ' ; // 캘린더 이벤트 요일
      body += event.getTitle() + '\n'; // 캘린더 이벤트 제목  
    }

  GmailApp.sendEmail(recipient, subject, body)

}
```
