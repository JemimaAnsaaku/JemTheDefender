# Defensive Security Practical 
In this lesson I was introduced to the Security Operations Centre which is a team of defensive security professionals who are tasked with monitoring a network and its systems to detect and defend against malicious cyber events. 

## Key concepts 
Vulnerability - a weakness in a system which must be fixed by installing an impactful update or patch to prevent a hacker from exploiting.

Policy violations - A set of rules which is established by an SOC analyst to protect the system.

Threat intelligence - Information that is acqured about actual and potential enemies which is essential to form threat-based defences. 

Digital Forensics and Incidence Response (DFIR) - (DF) The art of analysing evidence of an attack and its perpetrators. Here we focus on the analysing digital forensic images (a low-level copy) of a system to reveal information. We also focus on recovering system memory, system logs and network logs. (IR) IR specifies the methodology we should follow to minimise damage of attack in as short a time as possible with the key phases preparation (having a dedicated team ready to handle the incident), detection and analysis (team has all resources), containment (preventing spread of the incident), post-incident activity (producing a report to prevent a similar incident). 

Malware (Malicious software) Analysis- A virus is a piece of code that attaches to a program and makes it unusable or slow by overwriting, altering or deleting data. A trojan horse is a program that promises a paticular function but it hiding malware underneath. Ransomware is a program that encrypts a user's files to make them unreadable and can only be reversed with a password which is given when the user pays a ransom to the hacker. 

Malware analysis - Aims to learn about malicious techniques. Static analysis inspects the malware without running it, which requires solid knowledge of assembley language.  Dynamic analysis inspects malware by running it in a contained environment to monitor its activities. 

Assembley language - low-level programming language that provides human-readable representation. 

Security Information and Event Management (SIEM) - A tool used to gather security information for an organisation. 

# Practical 
Here I imagined myself as a Security Operations Centre analyst responsible for protecting a bank. In this role it is imperative that I am sharp in detecting intrusions to prevent a catastrophic incident.

## Step 1
In the alert log I recognised an unauthorised connection attempt from an unknown IP adress. I copied the IP address to my system. This alert is especially critical as the update above in the activity log tells me that the unknown IP address was granted authorisation. 

![Unauthorised IP address](https://github.com/JemimaAnsaaku/JemTheDefender/blob/main/Images/Screenshot%202025-02-06%20at%2015.26.45.png?raw=true)

## Step 2
I then copied and pasted the IP address into an IP scanner to check the reputation of the IP address. This is to determine whether or not it can be trusted as it is currently unknown. 

![IP address scanner](https://github.com/JemimaAnsaaku/JemTheDefender/blob/main/Images/Screenshot%202025-02-06%20at%2015.27.23.png?raw=true)

## Step 3
The IP address was found to be malicious. This means that an unknown malicious IP adress has gained authorisation onto our system which has a high likelihood of causing a critical incident. 
![IP is malicious](https://github.com/JemimaAnsaaku/JemTheDefender/blob/main/Images/Screenshot%202025-02-06%20at%2015.27.46.png?raw=true)

## Step 4
This must be esculated to a senior member of the SOC team to ensure I am given guidance on how to appropriately respond to this breach. 
![Refer to SOC team lead](https://github.com/JemimaAnsaaku/JemTheDefender/blob/main/Images/Screenshot%202025-02-06%20at%2015.28.18.png?raw=true)

## Step 5
The team lead has granted me permission to block the IP adress to prevent access to our systems. 
![IP is blocked](https://github.com/JemimaAnsaaku/JemTheDefender/blob/main/Images/Screenshot%202025-02-06%20at%2015.28.52.png?raw=true)

# Conclusion
This practical provided me with a realistic insight as to what to expect as a SOC analyst protecting a bank. It is critical to be constantly observant in using Security Information and Event Management systems to contain and remediate breaches. 
