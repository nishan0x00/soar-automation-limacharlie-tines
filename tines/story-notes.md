# 🔄 Tines Automation Story: SOAR-EDR-Project

This file provides a breakdown of the logic used in the exported Tines story. It outlines the key actions, flow, and decision points in the automation pipeline.

---

## 🧩 Overview

The Story is triggered by a detection event from LimaCharlie and flows through multiple steps to:

1. Parse event metadata
2. Alert the team
3. Present a human-in-the-loop decision
4. Take automated response action based on input

---

## ⚙️ Key Actions Breakdown

### 1. **Webhook Trigger**
- Accepts incoming JSON from LimaCharlie when a detection fires
- Randomized URL for security
- Data is passed to the rest of the Story

### 2. **Extract Event Metadata**
- Parses fields such as:
  - Hostname
  - IP address
  - Username
  - File path
  - Command line
  - Sensor ID
  - Detection link
- Saves them as variables for use in Slack/Email

### 3. **Slack Alert Action**
- Sends a message to a security Slack channel
- Includes all parsed metadata in a readable format
- Contains a summary and detection type

### 4. **Email Alert Action**
- Sends an HTML-formatted email to the IR team
- Same metadata as the Slack alert, for record-keeping

### 5. **User Prompt Page**
- Generates a Tines page with a decision prompt:
  > “Do you want to isolate the machine?”
- Includes context for the detection
- Options: ✅ Yes / ❌ No

### 6. **Conditional Branch: If YES**
- Calls the LimaCharlie API with the correct `sensor_id`
- Issues a host isolation command
- Posts success message to Slack

### 7. **Conditional Branch: If NO**
- Logs that no action was taken
- Sends a follow-up to Slack noting the user's decision

---

## 🔐 Notes

- Webhook and page URLs were randomized during export
- API credentials are stored securely via Tines credential storage
- All steps are modular and reusable for other detection scenarios

---

## 🧠 Why This Matters

This story shows how SOAR platforms like Tines can:
- Automate repetitive incident response actions
- Reduce mean time to respond (MTTR)
- Still include human analysts for high-impact decisions

