# 🚀Project-2: Log Analysis Basics: Windows Security Logs

## **Objective:**
The objective of this lab is to learn about  **Windows Security Logs** and help them understand how to analyse logs for security-related events. Will learn how to explore and analyse various security logs such as login attempts, user account changes, and other critical system events that could indicate potential security threats.



## **Lab Setup**
### **Requirements:**
- **System:** Windows 10/11 or Windows Server 2019/2022
- **Tools:**
  - **Windows Event Viewer** (pre-installed)
  - **Notepad** (to create custom events, if needed)
  - **Administrative Privileges** (to access certain security logs)

---

## **What are Windows Security Logs?**
Windows Security Logs contain records of security-related events on the system, such as:
- **Successful and Failed Login Attempts:** Track users who log in or fail to log in.
- **Account Lockouts:** Occurs when a user exceeds the maximum allowed number of incorrect login attempts.
- **Audit Policies:** Logs related to changes in system audit settings and configurations.
- **Group Membership Changes:** Tracks changes in group memberships and user privileges.
- **Privilege Escalation:** Logs events when a user gains elevated privileges.

These logs are valuable for monitoring security incidents, detecting unauthorized access, and auditing system changes.

---

## **Understanding Event IDs in Security Logs:**
Some common **Event IDs** in **Windows Security Logs** that you will encounter include:
- **Event ID 4624**: Successful Logon.
- **Event ID 4625**: Failed Logon.
- **Event ID 4740**: Account Lockout.
- **Event ID 4732**: A user was added to a security-enabled local group.
- **Event ID 4672**: Special privileges assigned to a new logon (Privilege escalation).

---

## **Lab Task: Explore and Analyze Windows Security Logs**


### **Step 1: Simulate a Failed Login Attempt**
1. Create a test user name "haxuser1" on Windows machine.
2. Simulate a failed account access using this command
   Open **PowerShell** and enter an invalid username and password. You can do this by using the following command:
   ```cmd
   net use \\127.0.0.1\IPC$ /user:haxuser1 WrongPassword
   ```
   Here:
   
| Command Part           | Explanation                                                                                   |
|------------------------|-----------------------------------------------------------------------------------------------|
| `net use`              | A command used to connect to shared resources (like network shares or printers).              |
| `\\127.0.0.1\IPC$`     | A special hidden administrative share called `IPC$` on your local machine (127.0.0.1 = localhost). `IPC$` is used for inter-process communication, especially for authentication purposes. |
| `/user:haxuser1`       | Specifies the username to use for authentication (in this case, `haxuser1`).                 |
| `WrongPassword`        | The password you're trying to authenticate with — which is intentionally incorrect.           |

Or Else you can sign out with your existing account and sign in with `haxuser1` account with an invalid password



### **Step 2: Detect the Log in Windows Event Viewer**
1. In the **Event Viewer**, navigate to:  
   `Windows Logs → Security`
2.  After the failed login, go back to Event Viewer.
3. Filter the Security Logs for Event ID 4625 (Failed Logon).
4.. Look for entries that correspond to the failed login attempt.
5. Take a screenshot of the event details, including:
   - Failed Login Attempt Details
   - User Name
   - Logon Type
   - Source Network Address

## Conclusion:
- Understanding Windows Security Logs: Windows Security Logs are essential for identifying suspicious behavior such as unauthorized login attempts, privilege escalation, and system configuration changes.
- SOC Analyst Role: As a SOC Analyst, reviewing and analyzing these logs regularly is critical to detecting and responding to security incidents in real-time.
- Threat Detection: By monitoring for multiple failed logins, account lockouts, and privilege escalations, SOC Analysts can quickly detect malicious activities on a network.

## 📸 Submission

Screenshots demonstrating successful log analysis for both successful and failed login attempts:

Event ID 4624 (Successful Login): A screenshot showing a successful login event from the Security logs.

![image alt](https://github.com/sachinpatil-soc/30-Day-SOC-Analyst-Challenge-2025/blob/e74d7e17ca4fb65d6fca37346c0d2cba58a14fcd/windows-securty-logs-4624.JPEG)



Event ID 4625 (Failed Login): A screenshot showing a failed login attempt event (Event ID 4625) from the Security logs, explicitly highlighting the username, logon type, and source network address. 

![image alt](https://github.com/sachinpatil-soc/30-Day-SOC-Analyst-Challenge-2025/blob/45038830a4e1d079a427b6b45100b10956b0be3a/Images/windows-securty-logs-4625.JPEG)
