###############################################################
#                   FIREWALL CONFIGURATION TASK               #
#                     WINDOWS 11 - REPORT                     #
###############################################################

🎯 OBJECTIVE:
Configure and test basic firewall rules to allow or block traffic using Windows Defender Firewall.

🧰 TOOLS USED:
- Windows 11
- PowerShell
- Windows Defender Firewall with Advanced Security (GUI)

===============================================================
📌 TASK STEPS PERFORMED:
===============================================================

🔹 1. Open Firewall Configuration Tool
---------------------------------------------------------------
- Press `Win + S`, search for:
  ▶ "Windows Defender Firewall with Advanced Security"
- Click to open.

🔹 2. View Existing Rules
---------------------------------------------------------------
- Click on **Inbound Rules** and **Outbound Rules** in the left sidebar
- This shows current firewall rules configured on the system

🔹 3. BLOCK Telnet (Port 23)
---------------------------------------------------------------
Steps:
- In Inbound Rules, click **New Rule**
- Select: **Port**
- Protocol: **TCP**
- Specific Local Port: **23**
- Action: **Block the connection**
- Apply to: All profiles (Domain, Private, Public)
- Name the rule: **Block Telnet Port 23**
- Click **Finish**

🔹 4. Test Blocked Telnet Port
---------------------------------------------------------------
Open PowerShell and run:
```powershell
Test-NetConnection -ComputerName 127.0.0.1 -Port 23
