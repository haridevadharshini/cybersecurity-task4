# 🔥 Windows Firewall Rule Configuration & Testing

## 👩‍💻 Performed On:
- **OS**: Windows 11
- **Tool**: Windows Defender Firewall (Advanced Settings)
- **Command Line**: PowerShell

---

## 📌 Objective:
Configure and test firewall rules to **block and allow** specific ports, and verify using PowerShell.

---

## 🧪 Steps Performed:

### 1. View Existing Firewall Rules
- Open: `Windows Defender Firewall with Advanced Security`
- Navigate to: `Inbound Rules`
- Observe all default and custom rules

---

### 2. Block Port 23 (Telnet)
**Steps:**
- In **Inbound Rules**, click **New Rule**
- Select: **Port**
- Protocol: **TCP**
- Specific Local Port: `23`
- Action: **Block the connection**
- Profile: **All**
- Name: `Block Telnet Port 23`
- Click **Finish**

---

### 3. Test Blocked Telnet Port (Port 23)
**PowerShell Command:**
```powershell
Test-NetConnection -ComputerName 127.0.0.1 -Port 23
```
**Result:**  
`TcpTestSucceeded: False`  
➡️ Port 23 is **successfully blocked** by the firewall.

---

### 4. Allow Port 22 (SSH)
**Steps:**
- In **Inbound Rules**, click **New Rule**
- Select: **Port**
- Protocol: **TCP**
- Specific Local Port: `22`
- Action: **Allow the connection**
- Profile: **All**
- Name: `Allow SSH Port 22`
- Click **Finish**

---

### 5. Test SSH Port (Port 22)
**PowerShell Command:**
```powershell
Test-NetConnection -ComputerName 127.0.0.1 -Port 22
```
**Result:**  
`TcpTestSucceeded: False`  
❗ Even though the firewall allows port 22, the test fails because **Windows 11 does not run an SSH server by default**, so no service is listening on that port.

---

## 🎯 Summary: How Firewall Filters Traffic

- The firewall filters traffic using a set of rules defined by the user or system.
- Rules are based on:
  - Protocol (TCP/UDP)
  - Port numbers
  - IP addresses (source/destination)
  - Action: Allow or Block
- **In this task:**
  - Blocking port 23 stops Telnet traffic.
  - Allowing port 22 doesn’t work unless an SSH server is running.

---

## 📸 Screenshots to Include:
- Rule for port 23 (Blocked)
- Rule for port 22 (Allowed)
- PowerShell output for both test commands
- Full rule list view in firewall

---

## 📝 Extra Notes:
- PowerShell's `Test-NetConnection` only works when a service is running on the port.
- Optional: Enable SSH service using:
```powershell
Add-WindowsCapability -Online -Name OpenSSH.Server
Start-Service sshd
```

---

## ✅ Task Complete
