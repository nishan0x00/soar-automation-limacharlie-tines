# 📊 Alert Fields Reference

This document outlines the fields included in Slack and Email alerts when a detection is triggered by LimaCharlie.

---

## 🔍 Field Breakdown

| Field | Description | Source |
|-------|-------------|--------|
| `Project Name` | Internal categorization of the detection project (e.g., "SOAR-EDR-Project") | `<<retrieve_detection.body.cat>>` |
| `Time (epoch)` | UNIX timestamp of the event | `<<retrieve_detection.body.detect.routing.event_time>>` |
| `Computer Name` | Hostname of the affected endpoint | `<<retrieve_detection.body.detect.routing.hostname>>` |
| `Source IP` | Internal IP address of the machine at the time of detection | `<<retrieve_detection.body.detect.routing.int_ip>>` |
| `Username` | User account associated with the process that triggered the detection | `<<retrieve_detection.body.detect.event.USER_NAME>>` |
| `File Path` | Full path to the executable/process that caused the alert | `<<retrieve_detection.body.detect.event.FILE_PATH>>` |
| `Command Line` | The full command used to invoke the process | `<<retrieve_detection.body.detect.event.COMMAND_LINE>>` |
| `Sensor ID` | Unique ID of the LimaCharlie sensor installed on the host | `<<retrieve_detection.body.routing.sid>>` |
| `Detection Link` | Direct URL to the detection event in LimaCharlie’s console | `<<retrieve_detection.body.link>>` |

---

## 💡 Why This Matters

Each of these fields is used to:
- Enrich alerts with actionable context
- Provide quick triage data to analysts
- Maintain traceability to the original event in LimaCharlie

This field map helps maintain consistency across Slack, Email, and future alerting integrations.

