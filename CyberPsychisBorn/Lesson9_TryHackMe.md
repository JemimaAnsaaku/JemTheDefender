# Extending your network
## Intro to port forwarding
Port forwarding is an essential component in connecting applications and services to the internet. Without port forwarding, applications such as web servers are only available to devices within the same direct network.

Web server - a system that stores, processes and delivers websites to users over the intenet. For example you open your browser type in www.example website.com. the request is sent to an Apache web server that is hosting the website. Apache processes the request and sends back the website's HTML, images and other content 

Lets take a server with an ip address of 192.168.1.10 that runs a webserver on port 80. Only the computers connected to it within its network would be able to access it (this is known as the intranet).

Intranet - a private, internal network that is only accessible to authorised users within an organisation. 

![intranet diagram](https://github.com/JemimaAnsaaku/JemTheDefender/blob/main/Images/Screenshot%202025-02-09%20at%2011.24.06.png?raw=true)

If an administer wanted a website to be accessible to the public using the internet, they would have to implement port forwarding. 

![port forwarding](https://github.com/JemimaAnsaaku/JemTheDefender/blob/main/Images/Screenshot%202025-02-09%20at%2011.24.22.png?raw=true)

Within this design, network 32 is now able to access the webserver running on Network 1 using the IP address of network 1 (82.62.51.70)

It is easy to confuse port forwarding with the behaviours of a firewall, however, I just need to understand that port forwarding opens specific ports. Whilst firewalls control whether traffic can travel across these ports. 

Port forwarding is configured at the router of a network. 


## Firewalls
A firewall is a device within a network used for determining what traffic is allowed to enter and exit. Think of it as boarder security for a network. An administrator can configure a firewall to permit or deny traffic from entering or exiting a network based on numerous factors such as:

- where is the traffic coming from? (has the firewall been configured to accept/deny traffic from a specific network?)

- where is the traffic going to? (has the firewall been configured to accept/deny traffic destined for a specific network?)

- What port is the traffic for? (has the firewall been configured to accept/deny traffic destined for port 80 only?)

- what protocol is the traffic using? (has the firewall been configured to accept/deny traffic that us UDP or TCP or both?)

firewalls perfrom packet inspection to determine the answers to these questions.

Firewalls come in all shapes and sizes. from dedicated pieces of hardware (physical elements of a computer, often found in large networks like businesses) that can handle a magnitude of data to residential routers (like at your home) or softwares such as 'Snort', firewalls can be categorised in 2 to 5 categories 

the two primary categories are:

### Stateful firewall 
A stateful firewall tracks the state of connections. It doesnt just look at individual packets in isolation, it considers the context of connections - in paticular whether the packet is part of an ongoing and legitimate connection. A stateful firewall understands that these packets are part of the process, so it allows the handshake to proceed by tracking the state of the connection. The firewall wont just block each packet, instead, it tracks the entire handshake process to ensure it is legitimate and part of an active and valid connection. 

In context, a stateful firewall would allow the first part of the TCP handshake (SYN packet) because its part of the initiation of a legitimate connection. The firewall allows the SYN packet through because its part of the connection attempt, but it isnt making a final decision yet. It is waiting to see the next steps in the handshkae process. At this point, it doesnt know whether the connection is malicious or legitimate, so it simply tracks the state of the connection. It allows the SYN packet to pass, assuming its a valid attempt to initiate a connection. However once the handshake is complete, the firewall will continue to monitor the state and then verify whether the traffic is consistent with its expected behaviour (source IP, sequence number, etc).

If any part of the handshake fails or the handshake doesnt complete properly, the firewall will block the connection.

### stateless
A stateless firewall type uses a static set of rules to determine whether or not individual packets are acceptible or not. For example, a device is sending a bad packet will not necessarily mean that the entire device is blocked. Whilst these firewalls use much fewer resources than their alternatives, they are much dumber. It doesnt track the state of a connection, but the individual packets. 

SYN PACKET: A stateless firewall will look at the SYN packet as just another packet without considering whether it is part of a larger connection attempt. It might block or allow it based on its configurated rules but doesnt know that the SYN packet is part of a legitimate handshake. 

SYN-ACK Packet: The server's response (SYN-ACK) will also be evaluated in isolation. the stateless firewall doesnt track whether the SYN packet was previously allowed or not, it just checks the packet's contents according to its rules.

ACK Packet: when the the client sends the ACK packet, the stateless firewall will again process this packet in isolation. It doesnt know whether the SYN and SYN-ACK packets came before it, so will only evaluate the packet based on predefined rules. 

## Virtual Private Network (VPN)
This is a technology that allows devices on seperate networks to communicate securely by creating a dedicated path between each other over the internet (known as a tunnel). Devices connected within this tunnel form their own private network. 

for example, only devices within the same network (such as within a business) can directly communicate. However, a VPN allows two offices to be connected.

Benefits

Allows networks in different geographical locations to be connected - ie bueinesses with multiple offices will find this beneficial, including people who work from home.

offer privacy - VPN technology uses encryption to protect data. This means that it can only be understood between the devices it was being sent from and is destined for, meaning the data isnt vulnerable to sniffing. This encryption is useful in places with public wifi, where no encryption is provided by the network. You can use a VPN to protect your traffic being viewed by other people. 

Offers anonymity - journalists and activicsts often depend on VPNs to safely report on global issues in countries where freedom of speech is controlled. Usually, your traffic can be viewed by your isp and other intermediariees and, therefore tracked. The level of anonymity a VPN provides is only as much as how other devices on the network respect privacy. For example, a VPN that logs all of your data/history is essentially the same as not using a VPN in this regard. 

TryHackMe uses a vpn to connect you to our vulnerable machines without making them directly accessible on the intenet. This means that:

I can securely interact with tryhackme machines 

service providers such as ISPs dont think you are attacking another machine on the internet, which could be against the terms of service)

The VPN provides security to tryhackme as vulnerable machines are not accessible using the internet. 

VPN tech has improved over the years. Types of VPN technologies:

PPTP - The Point-to-Point Tunneling Protocol (PPTP) is the technology that allows the data from PPP to travel and leave a network. PPTP is very easy to set up and is supported by most devices. It is however, weakly encrypted in comparison to alternatives.

PPP - this technology is used by PPTP to allow for authentication and provide encryption of data. VPNs work by using a private key and public certificate (similar to SSH - SSH (Secure Shell) is a network protocol that provides a secure way to access a computer over an unsecured network, like the internet.) A private key and certiciate must match for you to connect. This technology is not capable of leaving a network by itself (non-routable) and must be routed by PPTP. 

IPSec - Internet protocol security (IPSec) encrypts data using the existing IP framework. it is difficult to set up in comparison to others, however if successful it boasts strong encryption, and is also supported on many devices 

