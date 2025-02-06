# Offensive Security 
## Objective
Offensive security encourages us to outsmart hackers by using their tactics to enhance our own defence systems. By learning specific techniques like exploiting software bugs, breaking into computer systems and finding loopholes we can identify weaknesses in softwares to prevent a hacker from doing the same. 
## Tools Used 
Gobuster - A command-line application (an application that is ran through a terminal) which works by taking a wordlist and brute forcing them onto the target URL to identify in any pages or directories exist. 
Command-line interface - A text-based interface where commands are input to interact with the operating system and perform tasks (similar to visual buttons), only they are more accurate and efficient to use
# Practical execution
## Step 1 - Terminal
Here I opened the terminal within TryHackMe's virtual machine (VM) or mock desktop environment. 
## Step 2 - GoBuster
Then i ran Gobuster through the terminal to determine whether the target site (in this case the fictious website FakeBank) had any hidden admin pages. 

To do this I input the following command
![Gobuster input command](https://github.com/JemimaAnsaaku/JemTheDefender/blob/main/Images/Gobuster%20command.png?raw=true)
- here -u represents the url, followed by the target website, -w wordlist.txt represents the wordlist (a textfile) that will deposit words that will be used for bruteforce and dir represents that in the command I am requesting to find directories.

## Step 3 - Analysing output
The output shows directories with their status code and other details. Here I am interested specifically in bank-transfer as it indicates an accessible page which is likely to contain information that is valuable to a hacker. I am not interested in investigating the image directory as images are likely to not contain information that is beneficial to a hacker. 
![Gobuster output](https://github.com/JemimaAnsaaku/JemTheDefender/blob/main/Images/Screenshot%202025-02-06%20at%2014.40.46.png?raw=true)

## Step 4 - Accessing hidden page
After running Gobuster I navigated to the address in my browser which allowed me to access the hidden bank transfer page, which allowed me to transfer a sum of money from a random bank account to my own.

![Hidden page](https://github.com/JemimaAnsaaku/JemTheDefender/blob/main/Images/Screenshot%202025-02-06%20at%2014.51.20.png?raw=true)

# Conclusion
This exercise taught me how Gobuster can be used as a command-line application to discover hidden directories on a target site. The consequences of this is colossal and it demonstrates the importance of securing sensitive web endpoints. 
