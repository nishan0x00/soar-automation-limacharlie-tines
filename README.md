\# 🛡️ SOAR EDR Automation with LimaCharlie, Tines, Slack \& Email



This project demonstrates a real-world SOAR (Security Orchestration, Automation, and Response) pipeline that automates the detection and response to suspicious activity using:



\- \*\*LimaCharlie\*\* for endpoint detection and response (EDR)

\- \*\*Tines\*\* for orchestration and automation

\- \*\*Slack\*\* and \*\*Email\*\* for alerting and user interaction



---



\## 🚨 Use Case



The system detects suspicious behavior on a \*\*Windows Server 2022\*\* (simulated via the open-source tool \[LaZagne](https://github.com/AlessandroZ/LaZagne)) and launches a complete alert + response workflow, including an option to isolate the host in real time.



---



\## 🔁 Workflow Overview



1\. \*\*LimaCharlie agent\*\* detects suspicious activity (e.g., LaZagne).

2\. Detection is forwarded to \*\*Tines\*\* via webhook.

3\. Tines:

&nbsp;  - Parses and enriches the event

&nbsp;  - Sends an alert to \*\*Slack\*\* and \*\*Email\*\*

&nbsp;  - Prompts the user: “Do you want to isolate the machine?”

4\. If user selects ✅ YES:

&nbsp;  - Tines calls the \*\*LimaCharlie API\*\* to isolate the machine

&nbsp;  - Sends a confirmation to Slack

5\. If user selects ❌ NO:

&nbsp;  - Logs the decision and notifies Slack



---



\## 📸 Architecture Diagram



!\[SOAR Architecture](architecture/soar-architecture.png)



---



\## 🧠 Tools Used



| Tool         | Purpose                                |

|--------------|----------------------------------------|

| LimaCharlie  | Detection, host telemetry, isolation   |

| Tines        | Workflow automation and user prompt    |

| Slack        | Real-time alerting and notifications   |

| Email        | Alerting and audit trail               |

| LaZagne      | Simulated attack vector (trigger)      |



---



\## 🔍 Example Alert Contents



Alerts sent to Slack/Email contain:



\- Project Name

\- Computer Name

\- Internal IP Address

\- Username

\- Time of detection

\- File Path

\- Command Line

\- Sensor ID

\- Link to full event in LimaCharlie



---



\## 📁 Project Structure



```bash

soar-edr-automation/

├── README.md

├── architecture/

│   └── soar-architecture.png

├── tines/

│   ├── tines-story.json

│   └── prompt-screenshot.png

├── limacharlie/

│   ├── agent-setup.md

│   └── isolation-payload.json

├── alerting/

│   ├── slack-alert.json

│   ├── email-template.md

│   └── alert-fields.md

├── docs/

│   └── workflow.md

├── triggers/

│   └── lazagne-trigger-rule.yaml

├── LICENSE

└── .gitignore



---



\## 💡 Why This Project?



This project simulates an actual SOC (Security Operations Center) workflow and highlights:



\- Threat detection  

\- Alert enrichment  

\- Conditional automation  

\- Human-in-the-loop response  

\- Real-time decision-based remediation



---



\## 🚀 Skills Demonstrated



\- SOAR \& EDR Integration (LimaCharlie + Tines)  

\- Incident response automation  

\- REST API usage  

\- Alert engineering and delivery  

\- Security tool orchestration



---



\## 🔐 Disclaimer



This project uses LaZagne strictly for educational and detection simulation purposes. No credentials were harvested or misused.



---



\##📫 Contact



Want to learn more or collaborate? Reach out via LinkedIn or open an issue.

