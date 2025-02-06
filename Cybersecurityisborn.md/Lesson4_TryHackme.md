# Networking 
A network can be formed anywhere from two devices to billions

## Key concepts
Internet - The internet is a giant network that consists of many many smaller networks within itself.

APRANET - The first iteration of the internet 

Identifying devices In order for devices to communicate or maintain order, they need to be able to identify other devices and also be able to be idenified themselves. In order for devices to be identified they must have ways to be identified. This is through the internet protocol adress (IP) and Media Access control (MAC) adress

### Internet Protocol 
This is a set of numbers that is divided into four octets (8-bit value using a numbering system that can provide 4.29billion ip addresses) - we were runnning out of ip addresses

An IPv4 address - a new iteration of IP and supporting 340billion ip addresses and more efficient due to new methodologies

Public IP (used to identify a device on the internet) address is assigned by the ISP and all devices in a network will share the same public ISP. 

Private IP (used to identify a device amongst other devices) address is assigned by our routers, which assigns a different private ip for each device in a network. There cannot be the same two private IP addresses in a network.

IP follows a set of standards called protocols which are the backbone of networking and ensures that devices are communicating within the same language. 

ISP - Internet Service Provider

### MAC addresses
Network Interface (NIC) - hardware component (microchip board) on your device's motherboard that allows the devise to communicate with other devices either via ethernet or wireless. 

MAC address- the unique identifier assigned to the NIC by the manufacturer, like a serial number. This is what allows the ddevices to be uniquely identified on a local network. It is a 12 character hexadecimal number. example a4:c3:f0:85:ac:2d. First 6 characters (a4:c3:f0):First 6 characters (a4:c3:f0) represent the manufacturer of the network interface. Last 6 characters (85:ac:2d): These are a unique number assigned by the manufacturer to distinguish this specific device. 

MAC addresses can be spoofed (faked). This is when a device pretends to identify as another device by using its MAC address. This could result in a spoofed device receiving traffic intended for another device or gaining access to sensitive data, bypassing firewalls.

### Ping
Ping uses Internet Control Message Protocol (ICMP) packets to determine the performance of a connection between devices - does the connection exist and is it reliable?
Internet Control Message Protocol - this is a protocol used by network devices (like routers and computers) to send control messages. It is mainly used for error-reporting purposes.



