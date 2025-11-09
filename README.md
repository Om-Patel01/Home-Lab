# Home Lab Cybersecurity

## Objective

The Home Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to create a playground where I can test different malware sent to a Windows environment and expose myself to the use of the Splunk (SIEM) system, Sysmon and generate test telemetry to mimic real-world attack scenarios. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned

- Knowledge of Splunk and Sysmon tools and how they help us detect attacks.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used

- Security Information and Event Management (SIEM) system for log ingestion and analysis (Splunk).
- Network analysis tools (Wireshark, Nmap) for capturing and examining network traffic and also scanning for open ports.
- Telemetry generation tools to create realistic network traffic and attack scenarios (Sysmon).

## Steps

*Ref 1: Virtual Box*

<img width="1194" height="740" alt="image" src="https://github.com/user-attachments/assets/1cc9279d-19fd-4ae6-9d60-9ef76af773a4" />

- Configured a Windows 10 virtual machine and downloaded Splunk and Sysmon. 
- Set up a Kali Linux attacking machine to create and send malware .
- Added both machines to the same internal network to protect host machine and ensure connectivity.

*Ref 2: Nmap Scan*

<img width="886" height="670" alt="image" src="https://github.com/user-attachments/assets/4bd12d04-2adc-4871-b7e0-d2c67ab26f5a" />

- After Nmap scan, I identified and targeted the open port 3389.

*Ref 3: Malware Creation*

<img width="880" height="672" alt="image" src="https://github.com/user-attachments/assets/6ebb8bd4-961a-46e2-b49a-8c88441d74e3" />

- I know that this malware is very simple and would most likely get detected by the common anti-virus.
- The purpose of this project to gain experience with finding attack patterns and getting used to analyzing through SIEM systems and telemetry to understand how to defend against attacks, and where to start.

*Ref 4: Server*

<img width="885" height="670" alt="image" src="https://github.com/user-attachments/assets/4035541d-393d-49bf-b5b5-cc6034cdc340" />

- Set up a quick server with the use of python so that the Windows vm can access the malware. 

*Ref 5: Connection Check*

<img width="982" height="515" alt="image" src="https://github.com/user-attachments/assets/7562e926-0a4a-4e6a-b2d7-6425b3ca8ad3" />

- After running the malware on the Windows machine, I checked and found that the malware had established a connection from the Kali Linux to the Windows machine.
- Noted process id 7256. Checked task manager and found passport.pdf.exe running under pid: 7256.

*Ref 6: Handler*

<img width="881" height="665" alt="image" src="https://github.com/user-attachments/assets/53dfa4d7-37fa-48b7-8fb8-877ff711a479" />

- On the handler on my kali vm, I ran some commands such as "net user" and "ipconfig" through the connection.

*Ref 7: Splunk and Sysmon*

<img width="1913" height="960" alt="image" src="https://github.com/user-attachments/assets/1cd969e2-5f10-4281-ba88-020e4abd7d7d" />

- Configured Splunk to be able to read the Sysmon events through the index labeled endpoint.

*Ref 8: Splunk Analysis*
<img width="1919" height="984" alt="image" src="https://github.com/user-attachments/assets/3a72c164-7e88-4970-a48e-f103919b5698" />

- On Splunk, I learned to search and query the events to start analyzing.
- After querying data with the Kali Linux ip, I found that it was targeting the destination port 3389, which is RDP.
- During the analysis of the telemetry, in a real scenario, the questions I found myself asking were "Should this device be trying to connect to the Remote Desktop Protocol?" "Whose device is this?".
- After further research I found that if I would implement network sensors in between the machines, I could potentially see generation of signatures and the ports that were scanned.
- Also I would see TCP flags if Nmap was using TCP scans.

## Conclusion

This home lab gave me a safe, repeatable setup to run a simple payload, watch it from the Windows host, and dig through the telemetry in Splunk using Sysmon. I confirmed the attacker scanned and hit RDP (port 3389), saw the passport.pdf.exe process spawn, and used those signals to trace activity back to the Kali box. The malware was basic and would likely be caught by AV, but the point was learning how to look for patterns, write queries, and connect host and network data. Overall this was a solid hands-on practice that gave me practical detection skills and a clear roadmap for securing systems and improving threat detection. I am super excited to test more and different types of malware to see what kind of telemetry they leave, to investigate them and to update protocols based on my findings. 





