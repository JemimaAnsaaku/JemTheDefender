# Offensive Security 
This lesson emphasises how in order to outsmart a hacker, it is important to think like one.
Offensive security is essential in Cyber security because understanding hacker tactics allows us to enhance our own defence systems. Here, advanced tactics like breaking into computer systems, taking advantage of software bugs and locating loopholes in applications to gain unauthorised access is used. 

# Key concepts 
## Hidden pages/directories 
Due to human error or negligence there are sometimes cases whereby pages are not made private. This allows attackers to find hidden pages that show or give hackers access to admin controls or sensitive data. 

## Gobuster 
Gobuster is a command-line application which is sometimes used to find hidden directories and pages on any given website. It works by taking a list of words (wordlist) and brute-forcing them onto the target URL to see if any directories or files exist. If a valid directory or file is found, Gobuster will report the status code in its output, where 200 means the page exists and 301 means it is redirected.

## Command line 
A command line is a text-based interface (CLI) or terminal window (point of interaction between the user and the system sometimes two - or how different systems communicate with each other) where you can type commands to interact with a computer's operating system. Instead of using a mouse to click on icons, you type specific instructions to perform tasks like navigating files, running programs or managiing system settings. Many hacking tools and security programs run in the command line and allows for faster and more precise control over a system. It makes it essential for cybersecurity proefessionals as we use it for tasks like scanning networks, analysing logs and automating processes. 

## Command
A command is a specific instruction that you type into a CLI or terminal to tell the computer to consuct a certain action. They are typically short and used to interact directly with the system. A command using Gobuster would follow this layout:

Gobuster -u insertwebsite.co.uk -w wordlist.txt dir 

The -u specifies the URL that you want to scan.

The -w tells Gobuster to use the wordlist file (wordlist.txt)

The dir specifies the type of scan to perform, so in this case dir stands for directories.

## What happens next?
With the output you will see that Gobuster scans the website with each word in the list, findinf potential pages which may exist linked with the site. It will tell you pages in the list of page/directory names and this will be indicated by status:200 as previously mentioned. For example /bank-transfer (status:200)

This can then be typed into the the url bar, depending on the page, the hacker may have found vulnerabilities in the application. As an ethical hacker, it is my job to report this. 

## Potential careers
Penetration tester - testing tech products for exploitable security vulnerabilities

Red teamer - attacking an organisation (with permission) and providing feedback from an enemy perspective 

Security engineer - designing, monitoring and maintaining security controls. 
