# Defensive Security
Lesson 2 delved into the tole of Security Operations Center analysts within defensive security measures and introduced critical topics like threat intelligence, Digital Forensics Incidence Response (DFIR), malware analysis and Systems Information and Event Management (SIEM). Defense Security is critical in preventing intrusions from occuring and appropriately protecting against intrusions when they occur.

# Key Concepts

## Blue teams 
Blue teams are part of the defensive security landcape. Their tasks consist of using cyber security aware ness to train users about cyber security to help protect against attacks targeting their systems, documenting and managing assets to fully understand the systems and devices they must manage and protect, update and patch systems to ensure computers, network devices and servers are correctly updated and patched against weaknesses, setting up preventative security devices like firewalls (controls which networks traffic may go inside and what can leave the system) and intrusion prevention systems (blocks any network that matches present rules and attack signatures), and finally setting up logging and monitoring devices to detect malicious intrusions. 

## Security Operations Center (SOC)
A team of cyber security professionals that monitors the network and its systems to detect malicious cyber effects. The main tasks of an SOC are to fix weaknesses by installing a proper update or patch. When a fix is unabailable measures should be taken to ensure an attacker cannot exploit it. A SOC must establish policy violations (a set of rules required to protect the network systems). An SOC must detect and block an event of unauthorised activity in cases where username and passowrds are stolen before the damage is done. Finally, network intrustions can occur where a user clicks on malicious links or when an attacker exploits a public server, when this occurs the SOC must detect it as soon as possible to prevent further damage. 

## What tasks does an SOC cover?
### Threat intelligence 
This refers to information you gather about actual and potential enemies (cyber criminals targetting your systems). This information is used to help the company better prepare against potential adversaries to form a threat-informed defence. 

Intelligence needs data, and data must be collected, processed and analysed. This data is collected from local sources such as network logs (a record of events or activities that occur within a network) and public sources like forums. Data processing arranges it into a format suitable for analysis. The analysis phase seeks to find more information about the hackers and their motives and aims to create a list of recommendations and actionable steps. 

In learning about adversaries, we know their tactics, techniques and procedures as a result of threat intelligence and predict strategy. 

### Digital forensics and incident response (DFIR)
Digital forensics - science to investigate digital crime and establish facts. 

In defensive security, the focus of digital forensics shifts into analysing evidence of an attack and its perpretrators. Such examples are intellectual property theft cyber espionage (hacking to gain sensitive data), etc.

Digital forensics focus on the following:

File system - analysis of a digital forensic image (low-level copy) of a systems storage which revels much information such as installed programs, created files and partially overwritten and deleted files.

System memory -  if an attacker runs their malicious program in memory without saving to the disk, taking a forensic image of the system is the best way to analyse the contents to learn about attack.

System logs - each client and server computer maintains different log files about what is happening. Log files provide plenty of information about what happened on a system. Even when a hacker attempts to clear their traces, remenants will remain. 

Network logs - logs of the network packets (small unit of data transmitted over a network) that have traversed a network would help answer more questions about whether an attack is occuring and what it entails.

### Incidence Response
Incidence - breach of data or cyber attack

In some cases it may be less critical such as misconfiguration (an error or mistake when setting up a configuring system, device or software), an intrusion attempt or policy violation. 

Examples of a cyber attack include when an attacker makes a network or systems inaccessible, defacing (changing) the public website and data breach (stealing company data.

There is a 4 step plan to reduce damage and recover in the shortest time possible:

1. Preparation - Have a team trained and ready to handle an incident.

2. Detection and analysis - The team has necessary resources to detect any incident 

3. Containment, eradication and recovery - once incident is detected, contain it by preventing any spread to other systems, eradicate it by destorying it and ensure proper system recovery.

4. Post incident activity - after successful recovery, a report must be produced and the lesson learned is shared to prevent future incidents.

### Malware Analysis
Malware = Malicious Software

Software = files, programmes or documents you can save on a disk or send over the network.

Types of Malware include

Virus - Piece of code (part of a program) that attaches itself to a program and spreads to one computer to another by altering, overwriting and ddeleting files, rendering the system unusable or slow.

Trojan horse - a program that shows a desirable function but hides malicious function underneath.

Ransomware - malware that encrypts (converting information or data into a code to prevent unauthorised access) a user's files, rendering files unusable. The attacker then offers the encryption password if the user is willing to pay a ransom. 

Malware analysis learns about such malicious techniques by using various means:

1. Static Analysis - inscpects malicious program without running it. However this requires solid knowledge of assembley language (a low-level programming language that computers can understand)

2. Dynamic analysis - runs malware in a controlled environment and monitors its activities and lets you observe how it behaves.

## Practical Scenario on TryHackMe
I acted as a SOC analyst tasked with protecting a bank. I used Systems Information and Event Management to monitor any suspicious alerts that were picked up by the software. Not all alerts were malicious - such as a user forgetting their password. However one alert flagged an unknown IP address gaining access to the system. I then used an open source database to perform a reputation and location check fot the IP address to aid in the investigation. The open-source database determined the IP adress to be malicious so I was required to block the IP adress and esculate this to the SOC team leader. 


