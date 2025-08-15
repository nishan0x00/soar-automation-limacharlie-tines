# 🧭 SOAR Architecture Diagram

This diagram illustrates the complete detection-to-response workflow in the SOAR EDR project.

---

## 🔗 Key Components

- **LimaCharlie** agent detects suspicious activity (e.g., LaZagne)
- **Tines** receives the detection event and orchestrates the response
- Alerts are sent to **Slack** and **Email** with metadata:
  - Hostname
  - IP Address
  - Username
  - Command Line
  - Sensor ID
  - Time
  - Detection link
- A **User Prompt** is generated to decide whether to isolate the machine
- **Conditional branches** automate isolation or log decisions

---

## 📁 File
- `soar-architecture.png` — visual representation of the SOAR workflow
