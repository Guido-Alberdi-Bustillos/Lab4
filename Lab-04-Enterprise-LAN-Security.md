\# Lab 04: Enterprise LAN Security Assessment

\*\*Student:\*\* Guido Alberdi  

\*\*Course:\*\* IT 520 - Corporate Cybersecurity  

\*\*Date:\*\* March 31, 2026



\---



\## Introduction

This report evaluates the network infrastructure of the \*\*Winslow Bay Municipal Utility District (WBMUD)\*\*. We implemented a segmented three-tier network architecture to isolate IT operations from Operational Technology (OT) and remote assets.



\---



\## Part 1: Network Architecture \& OSI Layers 1-3



\### Topology Overview

The network consists of IT Operations (10.1.10.0/24), OT (192.168.50.0/24), and a Remote Pump Station (172.16.5.0/24).



!\[WBMUD Network Topology](Screenshot1.png)

\*Screenshot 1: Full topology view with all segments physically connected.\*



\### OSI Layer Reflections

\- \*\*Layer 1 (Physical):\*\* Physical cabling and power represent the raw bitstream.

\- \*\*Layer 2 (Data Link):\*\* The switch uses MAC address tables for local frame delivery.

\- \*\*Layer 3 (Network):\*\* IP addressing and static routes enable inter-subnet connectivity.



\---



\## Part 2: Protocol Security Analysis



\### HTTP vs. HTTPS

HTTPS uses TLS/SSL to encrypt traffic, protecting against Man-in-the-Middle (MITM) attacks.



!\[HTTP vs HTTPS Test](Screenshot6.png)

\*Screenshot 6: Browser testing of secure vs. insecure protocols.\*



\### SSH vs. Telnet

SSH was configured to replace Telnet for secure, encrypted remote management.



!\[SSH Session](Screenshot7.png)

\*Screenshot 7: Successful encrypted session to IT-Router.\*



\---



\## Part 3: Shellshock Vulnerability Simulation

We simulated \*\*CVE-2014-6271\*\* against the OT Web Server. The exploit allowed for Remote Code Execution (RCE) by manipulating environment variables in the Bash shell.



\- \*\*Impact:\*\* Lateral movement to SCADA devices and disruption of water services.

\- \*\*Mitigation:\*\* Patching Bash (4.3+), deploying a WAF, and network micro-segmentation.



\---



\## Part 4: Incident Response \& Remediation

Following the March 15th breach, we identified a failure in patch management and lack of internal firewalling.



\### Remediation Steps:

1\. \*\*Immediate:\*\* Isolate OT Web Server and reset credentials.

2\. \*\*Short-Term:\*\* Apply Bash patches and configure ACLs.

3\. \*\*Long-Term:\*\* Transition to Zero Trust Architecture and DMZ isolation.



\---



\## Conclusion

This lab reinforces the necessity of network segmentation and protocol hardening in critical infrastructure. Moving from cleartext to encrypted protocols is vital for public safety at WBMUD.

