# Local Area Network (LAN) Topologies
Here I delved into the experimentation and implementation of various network designs. 
## Key Concepts
Topology - The design or look of the network at hand. 

## Star Topology
The main premise is that endpoint devices (computers/phone/tablets) are individually connected via a central networking device (router/switch/hub)

This topology is most commonly found today because of its reliability and scalability despite the cost. 

Any information sent to a device in this topology is sent via the central device which it connects. 

CONS 

-this topology requires more dedicated equipment to set up so it is more expensive than any other topology.

-The more this network scales the more maintenance is required to keep the network functional, which increases its dependance on maintenance. This makes troubleshooting faults much harder

- This topology is still prone to failiure although it is less likely to.

To conclude star topology - if the central device fails, the devices will no longer be able to send or recieve data, though the centralised hardware devices are often robust. 

PROS

- This topology is much more scalable in nature, this means that it is very easy to add more devices as the demand for the network increases.

## Bus Topology
This type of cable relies upon a single connection known as a backbone cable. this is similar to a tree branch (the backbone cable) where the devices (leaves) stem from.

CONS

-Because all data destined for each device travels anong the same cable it is quickly prone to becoming slow and bottlenecked if devices are simultaneously requesting data.

- This bottleneck also results in difficult troubleshooring because it quickly becomes difficult to recognise which device is experiencing issues as the data is all travelling along the same route.

- There is little redundancy in place in case of failiutes. This means that there is single point of failiure along the backbone cable, which means that if the backbone cable were to break the devices can no longer recieve or transmit data along the bus.

PROS

- Bus topologies are easier and more cost-efficient topologgies to set up because of their expenses, such as cabling or dedicated networking equipment used to connect the devices.

## Ring Topology (Token topology)
Devices are connected directly to each other to form a loop. It works by sending data across a loop until it reaches the destined devise, using the other devices along the loop to forward the data. A device will only send recieved data from another in this topology if it does not have any to send itself. If the device happens to have its own data to send, it will send its own data before sending data from another device

CONS 

- Because there is only one direction for data to travel across this topology it is fairly eady to troubleshoor any faults that arise.

- A fault such as a cut cable or a broken device will result in the whole network breaking.

PROS

- There is little cabling required and less dependent on dedicated hardware - such as with star topology. 

- It isnt an efficient way of travelling data actoss a network as it may have to visit many multiple devices first before reaching the intended device.

- Ring topologies are less prone to bottlenecks as within bus topology, as large amounts of traffic are not travelling the network at any one time. 

## What is a switch?
- Switches are dedicated devices within a network that are designed to aggregate (gather into a mass) multiple other devices such as computers, printers or any other networking capable device using ethernet.

- These various devices plug into a switch port and are usually found in larger networks such as businesses and schools.

- Switches can connect a large number of devices by having ports of 4,8,16,24,32 and 64 for devices to plug into.

- Switches are much more efficient than their lesser counterpart (hubs/repeaters) as they keep track of what device is connected to which port. This way, when they recieve a packet, instead of repeating that packed to every port like a hub would do, it just sends it to the intended target, thus reducing network traffic.

- Network traffic - data being transmitted across a network, such as the internet or a local area network (LAN).

- Both switches and routers can be connected to one another. In doing so, we increase the redundancy (the duplication of critical components or functions in a system to increase reliability and prevent failures) of a network by adding multiple paths for data to take. If one path goes down another can be used.

- However, this may reduce the overall performance of a network because paths have longer to travel however this is a short price to pay for no downtime.

- ## What is a Router?
A router connects networks and pass data between them, it does this by routing. 

Routing - the label given to the process of data travelling across networks. Routing involves creating a path between networks so data can be successfully delivered. 

Routing is useful when devices are connected by many paths.

## Primer on subnetting 
subnetting - the term given to splitting up a network into smaller miniature networks within itself

Networks administrators use subnetting to categorise and assign specific parts of a network to know where to send information. 

Subnetting is achieved by splitting up the number of hosts that can fit within a network.

Subnet mask- the number of hosts that can fit into a network

Subnets use IP addresses in three different ways:

- identify the network address (this address identifies the start of the actual network and is used to identify a network's existence

- identify host address (an ip address here is used to identify a device on the subnet)

- identify default gateway (a special address assigned to a device on the network that is capable of sending information to another website.

Places such as businesses and offices and schools will usually see subnetting take place to increase efficiency, security and full control. 

For now, all we need to understand is this concept - lets take a typical cafe- it will have two networks, one for employees, cash registed and other devices for the facility, and another for the general public to use as a hotspot. Subnetting allows us to seperate these two from each other whilst having the benefit of a connection to larger networks such as the internet.

## Adress Resolution Protocol (ARP)
ARP is the technology responsible for allowing devices to identify themselves on a network. ARP allows a device to associate its mac address with an IP address on the network. Each device on a network will keep a log of the MAC addresses associated with other devices. When devices which to communicate with eachother they will send a broadcast to the entire network searching for the specific device. Devices can use ARP to find the MAC address (thus the physical identifier) of a device for communication. 

## How does ARP work
Each device within a network has a ledger to store info on which is called a cache. In context of ARP, this cache stores the identifiers of other devices on the netwok.

In order to map the two identifiers together an ARP sends two types of messages:

1. ARP Request - when this is sent a message is broadcasted asking what is the mac address that owns this IP address?
2. ARP Reply - when other devices recieve the message they will only respond if they own that ip address and will send an ARP reply with its MAC address.

The requesting device can now remember this mapping and store it in its ARP Cache for future use.

 ## Dynamic Host Configuration Protocol (DHCP)
 IP addresses can be manually assigned by entering them into a device or automatically -most commonly by a DHCP server.

When a device connects to a server and has not already been assigned an IP address, it sends out a request (DHCP discover) to see if any DCHP servers are on the network.

The DHCP server then replies back with an IP address that the device can use (DHCP offer).

The device then sends a reply confirming it wants the offered IP address (DHCP request).

The DHCP server sends a reply acknowledging this has been completed and the device can start using IP address (DHCP ACK)
