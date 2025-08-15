# 🧰 Installing LimaCharlie Agent on Windows Server 2022

This document outlines how the LimaCharlie agent was installed and configured to monitor a Windows Server 2022 machine.

---

## 🖥️ Host System
- **OS**: Windows Server 2022 (x64)
- **Role**: Simulated endpoint for EDR detection and response testing

---

## 🔑 1. Create Sensor in LimaCharlie Console

1. Log into [https://console.limacharlie.io](https://console.limacharlie.io)
2. Navigate to your organization > **Deploy Sensor**
3. Choose:
   - Platform: `Windows`
   - Architecture: `x64`
4. (Optional) Add tags like `test`, `windows_server`, `lab`
5. Click **Download Installer**

---

## 🖥️ 2. Install the Agent

Copy the downloaded `.exe` file (e.g., `lc_sensor_installer.exe`) to your Windows Server machine and run it:

```bash
lc_sensor_installer.exe
```
---

## ✅ 3. Verify Sensor Registration

After installation, go back to the LimaCharlie console and:

- Go to the Sensors tab

- Confirm that your device shows up as Online

- You’ll see metadata like:

    - Hostname

    - Internal IP

    - OS version

    - Sensor ID

    - Tags

---

## 🔍 4. Set Up a Detection Rule (Optional)

To test the SOAR workflow, I created a rule that triggers on execution of lazagne.exe (credential dumping tool).

You can find the YAML rule used in this project under:
triggers/lazagne-trigger-rule.yaml

---

🔐 Isolation via API

Tines uses LimaCharlie’s API to issue host isolation commands.

You can also isolate manually from the console:

- Go to the Sensor

- Click "Isolate Sensor"

---

🧪 Test Scenario

Once deployed:

- Run a tool like lazagne.exe on the endpoint

- Confirm the detection is logged in LimaCharlie

- It should trigger your Tines workflow (webhook)

---
Reference
- [LimaCharlie Documentation](https://docs.limacharlie.io/)
