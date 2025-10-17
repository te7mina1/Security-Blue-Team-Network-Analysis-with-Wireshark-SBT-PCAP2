# Security Blue Team Network Analysis with Wireshark-SBT-PCAP2
## Introduction
Network analysis involves collecting, monitoring and analyzing network traffic, such as DNS traffic and other protocols like TCP/UDP/ICMP to detect and investigate security incidents. It involves using tools such as Wireshark and command-line tools(tshark) to capture network traffic, analyze it for suspicious activities, detect intrusions, and understand the network behaviors.

## Pre-requisites
- A Linux Operating System(Ubuntu/Debian)
- Understanding of networking basics and protocols
- Wireshark installed(for GUI inspection)
- Experience with the command-line

## Lab Set-up and Tools
- A computer running a Linux distribution(e.g Ubuntu/Kali/Parrot)
- [Wireshark](https://www.wireshark.org/download.html) installed(i.e if on a Windows system)
- Network traffic or sample pcap files

### Installing Wireshark
1. Update and upgrade your package list:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
2. Install Wireshark(i.e if not installed on your system)
   ```bash
    sudo apt install wireshark
   ```
3. Import the PCAP file into Wireshark for analysis
## Exercise
### Exercise 2: Finding the activities from the SBT-PCAP2 file
1. What is the WebAdmin password?
2. What is the version number of the attacker’s FTP server?
3. Which port was used to gain access to the victim Windows host?
4. What is the name of a confidential file on the Windows host?
5. What is the name of the log file that was created at 4:51 AM on the Windows host?
   

## Conclusion
After completing this exercise, I was able to filter packets from the "display filter" in Wireshark to find specific results based on the activities given to me. I finally learnt to capture and monitor network traffic during the course. These skills are essential in performing network forensics investigation and analysis in the SOC role.

