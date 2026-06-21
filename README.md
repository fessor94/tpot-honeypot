# Tpot-Honeypot
This project documents the deployment, monitoring, and analysis of a T-Pot honeypot environment exposed to the public internet. The objective was to collect and study real-world malicious activity targeting commonly exposed services and protocols.

The deployment consisted of multiple honeypots emulating vulnerable services and devices. During the observation period, numerous reconnaissance attempts, credential attacks, vulnerability scans, and exploitation attempts were recorded from external threat actors.

 - Provision an AWS EC2 Ubuntu instance named `web-srv-101` to host the T-Pot honeypot environment.
<img width="1210" height="861" alt="1" src="https://github.com/user-attachments/assets/1d5d4206-0224-4ae8-b194-c1e488ce1a29" />
<img width="1219" height="812" alt="2" src="https://github.com/user-attachments/assets/834b5df8-b837-4296-9463-ac4ee5b31039" />
<img width="1220" height="768" alt="3" src="https://github.com/user-attachments/assets/6930e33e-c535-486f-93dd-457c4fd52fbc" />
<img width="1215" height="580" alt="4" src="https://github.com/user-attachments/assets/ee29eac3-902d-4cd7-a0ad-c234e96b8d9d" />

## Commands you run when the ec2 instance is up and running: 

 - sudo apt update && sudo apt upgrade -y
 - cd /opt
 - git clone https://github.com/telekom-security/tpotce.git
 - cd tpotce/
 - ./install.sh
 - type: "h" to select standard hive
 - username: (usually my ubuntu vm)
<img width="1377" height="849" alt="5" src="https://github.com/user-attachments/assets/47003e69-f485-4dfe-8b7d-c9fc84d997af" />
<img width="1377" height="849" alt="6" src="https://github.com/user-attachments/assets/60e52191-4dc3-460e-8555-69c692566abc" />

 - add security inbound rules, as custom tcp on aws for the new ssh port [64295]
<img width="1786" height="541" alt="7" src="https://github.com/user-attachments/assets/6e7d4ab2-775b-4ef8-9b44-b4dbf1454a46" />
 
 - reboot the vm and ssh using the new port [64295]
 - Check tpot status
<img width="1386" height="849" alt="8" src="https://github.com/user-attachments/assets/9d145aa2-37b5-4afe-bdc2-3bccd0e7de9f" />
<img width="1379" height="853" alt="9" src="https://github.com/user-attachments/assets/21afc800-7218-4332-9912-c90e721f73ed" />

 - docker ps --format "table {{.Names}}\t{{.Status}}"
<img width="1378" height="848" alt="10" src="https://github.com/user-attachments/assets/9801a6c2-65e2-48a3-bfe9-ec862075b7fc" />

 - tpot uses nginx container to epxpose the web gui type [docker port nginx]
<img width="1370" height="847" alt="11" src="https://github.com/user-attachments/assets/eaba764e-1998-46c9-aff4-50c0c13a2c8b" />

 - You will also need to go back to the AWS console to expose these ports to the internet:
<img width="1781" height="878" alt="12" src="https://github.com/user-attachments/assets/35c16dbf-8a25-41ea-8108-bcc501b9fbec" />

## Honeypots Deployed                                  

  [1] Cowrie | SSH, Telnet  Captures brute-force attempts, credentials, and attacker interactions

  [2] RDPHoneypot | RDP (Remote Desktop Protocol) | Records RDP connection and credential attacks 

  [3] Tanner      | HTTP/Web Applications | Captures web exploits, scanners, and malicious requests

  [4] CiscoASA    | Cisco ASA Firewall/VPN | Captures VPN scans, login attempts, and Cisco-targeted attacks

  [5] Dionaea     | SMB, FTP, HTTP, MSSQL and other vulnerable services | Collects malware and exploit attempts 
  
  [6] H0neytr4p   | Multi-port Listener | Captures reconnaissance, port scans, and connection metadata
  
 - Update the EC2 Security Group to expose the required honeypot services to the internet.
<img width="1600" height="825" alt="13" src="https://github.com/user-attachments/assets/2752469b-cdfe-414c-90aa-5d4daf4e9cb2" />
<img width="1596" height="826" alt="14" src="https://github.com/user-attachments/assets/c01f7956-f2b7-4c34-b95f-03291ba91c64" />
<img width="1600" height="782" alt="15" src="https://github.com/user-attachments/assets/1991573c-3fc2-4cf9-99c7-ed131ab1e82b" />
<img width="1583" height="780" alt="16" src="https://github.com/user-attachments/assets/74ceb786-0a05-4885-9425-b8b2c9d355e6" />
<img width="1588" height="778" alt="17" src="https://github.com/user-attachments/assets/963c4497-ab6f-40f1-946a-590016bab1de" />
<img width="1597" height="785" alt="18" src="https://github.com/user-attachments/assets/59806028-efe5-4829-9884-bc4969e10786" />

## Learning Objectives

- Deploy a cloud-hosted honeypot infrastructure
- Analyze real-world attack traffic
- Understand T-Pot architecture and Docker-based deployments
- Develop threat hunting and SOC analysis skills
- Attackers like open SSh ports and RDP as they are ones with most hits
- I got to understand the Elastic dashboard

## Disclaimer

This project was conducted in a controlled environment for educational and defensive cybersecurity research purposes. No production systems or user data were involved.
