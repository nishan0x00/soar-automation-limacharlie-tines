\# 🧠 SOAR EDR Workflow



This document outlines the end-to-end detection and response workflow for this project, leveraging LimaCharlie, Tines, Slack, and Email.



---



\## 🖥️ 1. Endpoint Monitoring (Windows Server 2022)



A LimaCharlie agent is installed on a Windows Server 2022 machine. It continuously monitors the system for defined indicators of compromise (IOCs) or behavioral signatures.



> 🔍 For this project, the simulated detection was based on execution of the open-source tool \*\*LaZagne\*\*, which attempts to extract locally stored passwords.



---



\## 🔔 2. Detection Triggers LimaCharlie Event



When the agent detects the defined behavior (e.g., `lazagne.exe` process), LimaCharlie generates an event containing full contextual data:



\- Hostname  

\- Internal IP address  

\- Username  

\- File path  

\- Command line  

\- Sensor ID  

\- Timestamp  

\- Detection link (in LimaCharlie console)



---



\## 🔁 3. Event Forwarded to Tines (Webhook)



LimaCharlie is configured to forward detection events to a \*\*Tines webhook\*\*, which starts a \*\*Story\*\* (Tines’ term for a playbook or automation workflow).



---



\## ⚙️ 4. Tines Workflow Logic



Tines performs the following actions:



\### a. Parse Detection Data



\- Extracts all key fields from the event payload

\- Stores them in variables for downstream use



\### b. Alerting



\- Sends a real-time alert to \*\*Slack\*\* (security channel)

\- Sends an \*\*Email\*\* to the incident response team

\- Both include full detection metadata



\### c. User Prompt (Decision Page)



\- A Tines-generated web page is sent to the team

\- Prompt: \_"Do you want to isolate this machine?"\_

\- Analyst selects ✅ \*\*Yes\*\* or ❌ \*\*No\*\*



---



\## 🧑‍💻 5. Conditional Response



\### ❌ If NO:

\- No further action taken

\- Tines sends confirmation to Slack: “No isolation — user declined.”



\### ✅ If YES:

\- Tines uses the \*\*LimaCharlie API\*\* to isolate the sensor (host)

\- Slack notification: “✅ Host \[hostname] was successfully isolated.”

\- Optional: Tines adds a note to LimaCharlie for audit tracking



---



\## 🧰 Tool Breakdown



| Tool         | Role                                  |

|--------------|----------------------------------------|

| LimaCharlie  | EDR agent, event generation, isolation |

| Tines        | Orchestration, API calls, alert routing |

| Slack        | Real-time alerting \& confirmation     |

| Email        | Alert delivery and documentation      |

| LaZagne      | Simulated trigger for detection       |



---



\## 🔐 Security Considerations



\- No real credential theft occurs; LaZagne was used solely to simulate malicious activity.

\- The workflow is modular and can be expanded to include more advanced triage, sandboxing, or escalation logic.



---



\## ✅ Summary



This workflow simulates an enterprise-ready SOAR response where:



\- Threats are detected in real time

\- Alerts are enriched and communicated across channels

\- Analysts are brought into the loop for high-impact decisions

\- Automated action is taken only with approval



The goal: \*\*Reduce response time without removing human control.\*\*



