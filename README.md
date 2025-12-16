# firewall-configuration-and-testing
Configuration and testing of basic firewall rules using Windows Defender Firewall, including blocking Telnet (port 23), allowing SSH (port 22), and verifying traffic filtering.

Repository Description
This repository demonstrates how to configure, test, and manage basic firewall rules using Windows Defender Firewall. The project includes blocking insecure services (Telnet – port 23), allowing secure services (SSH – port 22), testing connectivity, and documenting results with screenshots for an information security lab.

Objective
The objective of this task is to configure and test basic firewall rules to allow and block network traffic. This helps in understanding how a firewall filters incoming connections and protects a system from unauthorized access.

Tools Used
Operating System: Windows 10 / Windows 11
Firewall Tool: Windows Defender Firewall with Advanced Security
Command Line Tools: Command Prompt, PowerShell

Task Performed
1. Open Windows Firewall
Press Windows + R
Type wf.msc
Press Enter
Windows Defender Firewall with Advanced Security opens

2. View Existing Firewall Rules
Click on Inbound Rules
Existing firewall rules were reviewed to understand current configurations

3. Block Inbound Traffic on Port 23 (Telnet)
Steps followed:
Go to Inbound Rules
Click New Rule
Select Port → Next
Choose TCP and enter port 23
Select Block the connection
Apply rule to Domain, Private, and Public
Name the rule: Block Telnet Port 23

4. Testing the Firewall Rule
Initially, the telnet command was not recognized because the Telnet Client is disabled by default in Windows.
Enabling Telnet Client
Press Windows + R
Type optionalfeatures
Enable Telnet Client
After enabling, the following command was tested:
telnet localhost 23
Result: Connection failed, confirming that port 23 is blocked by the firewall.
Alternative test using PowerShell:
Test-NetConnection -ComputerName localhost -Port 23
Result: TcpTestSucceeded : False


5. Allow SSH (Port 22)
Steps followed:
Create a new inbound rule
Select Port → TCP → Port 22
Select Allow the connection
Apply to all profiles
Name the rule: Allow SSH Port 22

6. Remove Test Block Rule
The temporary Telnet block rule was deleted to restore the firewall to its original state

How Firewall Filters Traffic
A firewall works by inspecting incoming and outgoing network packets based on predefined rules. Each packet is checked for:
Port number
Protocol (TCP/UDP)
Direction (Inbound/Outbound)
Action (Allow or Block)
If a packet matches a rule, the corresponding action is applied. If no rule matches, the default firewall policy is enforced. Blocking insecure services like Telnet (port 23) and allowing secure services like SSH (port 22) improves system security.

Conclusion
This task demonstrated how to configure, test, and remove firewall rules using Windows Defender Firewall. Blocking and allowing specific ports showed how firewalls protect systems by controlling network traffic.
