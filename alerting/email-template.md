# 📧 Detection Alert Email Template

This email is sent via Tines when a detection event is received from LimaCharlie. It provides detailed event metadata to the incident response team for further triage.

---

## 📨 Email Components

### ✅ Subject Line
```
Detection Alert
```

> You can optionally include dynamic values such as the hostname:
> ```
> Detection Alert - {{retrieve_detection.body.detect.routing.hostname}}
> ```

### ✅ Sender Name
```
SOAR EDR Automation
```

### ✅ Recipients
- security-team@example.com
- incident.response@example.com
> *(Replace with actual distribution list used by your team)*

---

## 📝 HTML Body Content

```
Project Name: <<retrieve_detection.body.cat>><br>
Time (epoch): <<retrieve_detection.body.detect.routing.event_time>><br>
Computer Name: <<retrieve_detection.body.detect.routing.hostname>><br>
Source IP: <<retrieve_detection.body.detect.routing.int_ip>><br>
Username: <<retrieve_detection.body.detect.event.USER_NAME>><br>
File Path: <<retrieve_detection.body.detect.event.FILE_PATH>><br>
Command Line: <<retrieve_detection.body.detect.event.COMMAND_LINE>><br>
Sensor ID: <<retrieve_detection.body.routing.sid>><br><br>
Detection Link: <<retrieve_detection.body.link>>
```

---

## 📌 Notes

- The message uses `<br>` tags to ensure clean formatting in HTML-compatible email clients.
- This email is only sent at the **initial detection stage**.
- No follow-up email is sent for analyst decisions (e.g., isolation or no action).
