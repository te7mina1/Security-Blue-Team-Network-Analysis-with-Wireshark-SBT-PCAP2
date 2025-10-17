# NETWORK ANALYSIS : Analyzing captured packets using Wireshark.

---

## Lab overview

This lab contains an already captured SBT-PCAP file for network traffic analysis with Wireshark on a Linux machine. This lab is for anyone in the SOC, Network/Digital Forensic or any path that involves monitoring of networks.

## Goal and scope

I am to perform the following activities on the PCAP capture given.

1. What is the WebAdmin password?
2. What is the version number of the attacker’s FTP server?
3. Which port was used to gain access to the victim Windows host?
4. What is the name of a confidential file on the Windows host?
5. What is the name of the log file that was created at 4:51 AM on the Windows host?

## Environment & Prerequisites

- OS (Windows/Mac/Linux)
- Wireshark([https://www.wireshark.org/download.html](https://www.wireshark.org/download.html)) install

Open Wireshark and import the pcap file, from the previous lab, you would know how to import a pcap file.

## PCAP Analyses Methodology (workflows and techniques)

### Objectives/Questions

1. What is the WebAdmin password?

![Screenshot (99).png](NETWORK%20ANALYSIS%20Analyzing%20captured%20packets%20using%20%2028e2ec062bfd8017a9acfc5faee93415/e62f25c1-abd4-498b-ada5-c3608d8fb9b8.png)

Since the password was transmitted through a web app, I applied the “http” filter for all traffic in that protocol. 

![image.png](NETWORK%20ANALYSIS%20Analyzing%20captured%20packets%20using%20%2028e2ec062bfd8017a9acfc5faee93415/image.png)

### Answer : sbt123

By following the “HTTP Stream”, we were able to view the “WebAdmin Password” as “sbt123” in plain-text.

1. What is the version number of the attacker’s FTP server?

![image.png](NETWORK%20ANALYSIS%20Analyzing%20captured%20packets%20using%20%2028e2ec062bfd8017a9acfc5faee93415/image%201.png)

### Answer : 1.5.5

we use the “ftp” filter in the display filter for all FTP traffic, we notice in the “Info” column, the ftp version was displayed.

1. Which port was used to gain access to the victim Windows host?

![image.png](NETWORK%20ANALYSIS%20Analyzing%20captured%20packets%20using%20%2028e2ec062bfd8017a9acfc5faee93415/image%202.png)

### Answer : 8081

Since the attacker tried different ports to connect to the victim’s machine, there was no correct connection. I asked ChatGPT to provide a filter to show “ack reply”, giving me the filter, “tcp.flags.ack == 1”.

```
ip.src == 192.168.56.1 && ip.dst == 192.168.56.103 && tcp.flags.ack == 1
```

using this filter I was able to get the right port used to gain access to the victim’s machine.

1. What is the name of a confidential file on the Windows host?

![image.png](NETWORK%20ANALYSIS%20Analyzing%20captured%20packets%20using%20%2028e2ec062bfd8017a9acfc5faee93415/image%203.png)

### Answer : Employee_Information_CONFIDENTIAL.txt

I followed a “TCP Stream” and checked the files in the Desktop directory and found the confidential file named “Employee_Information_CONFIDENTIAL.txt” hosted on a Windoows machine.

1. What is the name of the log file that was created at 4:51 AM on the Windows host?

![image.png](NETWORK%20ANALYSIS%20Analyzing%20captured%20packets%20using%20%2028e2ec062bfd8017a9acfc5faee93415/image%204.png)

### Answer : LogFile.log

In the same process, follow “TCP Stream” in the same open stream. A log file was created at 07/16/2019 04:51 AM named “LogFile.log”.

> Link: [https://elearning.securityblue.team/home/courses/free-courses/introduction-to-network-analysis#content#analysis-with-wireshark#introduction-to-wireshark#activity-wireshark-challenge](https://elearning.securityblue.team/home/courses/free-courses/introduction-to-network-analysis#content#analysis-with-wireshark#introduction-to-wireshark#activity-wireshark-challenge)
> 

## Thank you.