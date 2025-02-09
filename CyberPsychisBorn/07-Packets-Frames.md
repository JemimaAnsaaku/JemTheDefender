# Packets and frames 
Packets and frames are small pieces of data that, when they form together they make a larger piece of information or message. 

Frame - frames are at layer 2 (data link) of the OSI model. This means that there is no such information as IP addresses

Packets - packets are at layer 3 of the OSI mofels. This is where IP addresses are intoduced

1. What Is Data and How Does It Travel?
When we talk about sending data across networks, we are talking about information (files, emails, webpages, etc.) that needs to move from one computer to another. This data has to travel across physical connections, like cables or wireless signals.

The internet and other networks are made up of many interconnected devices (like computers, phones, routers, etc.), and we need a way to move data between them reliably.

This is where the concept of network layers and encapsulation come in.

2. Networking Layers (The OSI Model)
The OSI Model (Open Systems Interconnection Model) is a standard way of thinking about how data moves across a network. It breaks the process down into 7 layers. Each layer handles a specific task in the process of moving data.

Let’s focus on the 3 most relevant layers for now, using our burger analogy:

Layer 7: Application Layer (The Patty)
This is the actual data — the content you want to send (like an email, a website, or a file). This is what you see and interact with as a user. The patty is the core of the burger — the reason for sending data in the first place.

Layer 2: Data Link Layer (The Cheese)
This is where physical addressing (like MAC addresses) and local communication happen. Devices use this layer to move data within the same network. Think of this as the preparation layer that ensures data is formatted properly for the physical network. It's like the cheese holding everything together, but it's more focused on getting it to the right device within the same network.

Layer 3: Network Layer (The Bun)
This is where IP addresses come in. The IP address ensures that data can be routed across different networks and reaches the correct destination (think of this as how you navigate the delivery of the package, routing it across cities, countries, etc.). Routers are the devices that operate at this layer, directing the data to its correct destination, whether it's local or across the globe.

3. Encapsulation: Wrapping Data Like a Burger
When we send data, it doesn’t just stay as one piece of information. It gets wrapped by each layer of the OSI model before it travels. This process is called encapsulation.

Think of this like wrapping your burger (the data) in different layers of paper:

The Layer 7 data (the patty) is what you want to send.

The Layer 2 (cheese) wraps around the data to help it be sent within a local network (like making sure the data gets to the right computer within your home or office).

The Layer 3 (bun) wraps around it to allow it to travel across different networks and eventually get to the right destination.

Combination of Both in Real-Life Scenarios: Even though Layer 3 can handle routing, it still relies on Layer 2 when the data is moving through each network segment. Think of Layer 2 as the local “delivery system” that takes care of delivering data within a local network, while Layer 3 is like the "postal service" that takes care of getting the data from one network to another.

## When Sending Data: ENCASPULATION STARTS AT APPLICATION LAYER 7
1. Layer 7 (Application Layer): The original data (like an email or a file) is generated here.

2. Layer 6 (Presentation Layer): If necessary, the data may be encrypted, compressed, or formatted.

3. Layer 5 (Session Layer): Ensures a stable communication session.

4. Layer 4 (Transport Layer): The data from Layer 7 is broken down into smaller chunks (segments).
Encapsulation happens here by adding a header with transport-specific info (like port numbers, sequence numbers for TCP, etc.).

5. Layer 3 (Network Layer): These segments are encapsulated into packets. An IP header is added, which includes the source and destination IP addresses for routing across networks.

6. Layer 2 (Data Link Layer): These packets are then encapsulated into frames. A MAC address is added to ensure the data can be sent to the correct device on a local network (or the next hop).

7Layer 1 (Physical Layer): Finally, the frames are converted into bits (electrical signals, light pulses, etc.) and transmitted across the physical medium.


## When Receiving Data: DECASPULATION STARTS AT PHYSICAL LAYER 1 
1. Layer 1 (Physical Layer): The bits are received from the network.

2. Layer 2 (Data Link Layer): The frames are received and the frame header is stripped off (the MAC address is removed).
The packet is passed up to Layer 3.

3. Layer 3 (Network Layer): The packet header is removed (which contained the IP address), revealing the segment.
The segment is passed up to Layer 4.

4. Layer 4 (Transport Layer): The segment header is removed (which contained transport-specific info like port numbers and sequence numbers).
The original data is now revealed, and it can be passed up to Layer 5.

5. Layer 5 (Session Layer): Manages the session, ensuring the communication continues smoothly.

6. Layer 6 (Presentation Layer): If the data was encrypted or compressed, it is decrypted or decompressed here.

7. Layer 7 (Application Layer): The original data (like the email, file, etc.) is delivered to the application.

Encaspulation - When data is being SENT from a source device to a destination device, encapsulation happens in the outbound direction. (layer 7 to layer 1)

Decaspulation - When the destination device receives the data, the reverse process happens — de-encapsulation (layer 1 to layer 7)

In short:

Frames exist at Layer 2 (Data Link).
Packets exist at Layer 3 (Network).
Data (the original message) exists at Layer 7 (Application).

*so the direction in how data moves through the layers depends on whether it is being sent or received by a device*

## Keywords
Time to live - this field sets an expiry timer for the packet to not clog up your network if it never manages to reach a host or escape.

Checksum - This field provides integrity checking for protocols such as TCP/IP. if any data is changed this value will be different from what was expected and therefore corrupt. 

Source address - The IP address of the device that the packet is being sent from so that the data knows where to return to.

Destination address - the device's ip address that the packet is being sent to so that data knows where to travel next. 

## Transmission Control Protocol/IP - 3 Way handshake
TCP/IP Model vs OSI Model:
The TCP/IP model is often compared to the OSI model because both describe how data is transmitted across networks, but they structure the layers differently. TCP/IP is more streamlined, and each layer serves a specific purpose, just like the OSI model.

## What is TCP
OSI Model is theoretical: The Open Systems Interconnection (OSI) Model is a conceptual framework that defines how different networking protocols work together. It has 7 layers and serves as a guideline for designing and understanding network systems.
The OSI model helps explain how data moves between two devices, but it does not represent the exact protocols used in real-world networking.
TCP/IP Model is Practical: The TCP/IP model, on the other hand, is the actual protocol suite used on the internet and real-world networks. It's not just a concept; it's how data is transmitted in practice. It has 4 layers and includes protocols like TCP and IP to handle data transmission.

Application Layer (TCP/IP):
"Software applications like email partners, browsers, file systems – the GUI?"
 The Application Layer in the TCP/IP model refers to the software that directly interacts with the user, such as web browsers, email clients, file transfer programs, etc. It handles the high-level protocols like HTTP, SMTP, FTP, etc., which are used for actual data transmission between applications.
In the OSI model, this corresponds to Layer 7 (Application Layer).

Transport Layer (TCP/IP):
"Ensuring the correct transmission of data."
The Transport Layer is responsible for ensuring that data is transmitted reliably and without error. This includes protocols like TCP (Transmission Control Protocol) and UDP (User Datagram Protocol). TCP ensures that data packets are delivered reliably, in the correct order, and without errors by using mechanisms like the 3-way handshake and checksums.
In the OSI model, this corresponds to Layer 4 (Transport Layer).

Internet Layer (TCP/IP):

"IP addresses are introduced, makes data suitable to be transferred from router to router."
The Internet Layer in TCP/IP is where IP addresses come into play. It’s responsible for routing the data across networks. This is where IP packets are created, and routers use these IP addresses to forward packets from one network to another (this is called routing). Protocols like IP (Internet Protocol) and ICMP (Internet Control Message Protocol) operate here.
In the OSI model, this corresponds to Layer 3 (Network Layer).

Network Interface Layer (TCP/IP):
"How data is transported within a network?"
The Network Interface Layer in the TCP/IP model is responsible for the physical transmission of data within a local network. This includes the hardware aspects of networking, like Ethernet cables, network interface cards (NICs), and the physical addressing (MAC addresses). It deals with data encapsulation into frames.
In the OSI model, this corresponds to Layer 2 (Data Link Layer) and Layer 1 (Physical Layer), since both deal with hardware and the physical transmission of data.

One definining feature of TCP is that it is connection-based, so TCP must establish a connection between both a client and a device acting as a server BEFORE data is sent. Because od this, TCP guarantees that any data sent will be recieved on the other hand. this is known as a threeway handshake.

PROS of TCP

- guarantees the integrity of data

- capable of synchronising two devices to prevent each other from being flooded with data in the wrong order

- performs a lot more processes for reliability

CONS of TCP

- requires a reliable connection between the two devices. If one small chunk of data is not received, then the entire chunk of data cannot be used and must be re-sent.

- a slow connection can bottleneck another device as the connection will be reserved on the other device the whole time.

- TCP is significantly slower than UDP because more work (computing) has to be done by the devices using this protocol

## How Encapsulation Works with TCP:

### From the Source Device (sending data):

Application Layer (Layer 7):
The data is created (e.g., a web request, email, etc.).
No encapsulation yet; it's raw data.

Transport Layer (Layer 4):
The data is segmented into smaller pieces (called segments) if it's large enough.
A TCP/UDP header is added, containing essential information like port numbers and sequence numbers.

Internet Layer (Layer 3):
The TCP segment (or UDP datagram) is wrapped in an IP packet.
The IP header is added, which includes the source and destination IP addresses to ensure the data can be routed correctly across networks.

Link Layer (Layer 2):
The IP packet is wrapped in a frame.
The frame is what is actually transmitted over the physical medium (Ethernet, Wi-Fi, etc.), and it contains the MAC addresses for the source and target devices on the local network.
Once all of this data has been encapsulated, it is sent from the source device to the target device over the network.

### From the Target Device (receiving data):
At the target device, the data goes through the opposite process, which is decapsulation. This is the reverse of encapsulation, where headers are removed step-by-step as the data ascends through the layers:

Link Layer (Layer 2):
The frame is received by the target device.
The MAC address is checked, and once it’s determined that the frame is intended for this device, the frame is stripped of its Link Layer header (the MAC addresses).
The data is passed up to Layer 3 as an IP packet.

Internet Layer (Layer 3):
The IP packet is checked for its destination IP address to verify that it's the right packet for this device.
The IP header is removed, and the remaining data (the TCP segment or UDP datagram) is passed up to Layer 4.

Transport Layer (Layer 4):
The TCP/UDP header is removed, revealing the original application data (e.g., web page request, email content).
The data is now ready to be passed to the application at Layer 7.

Application Layer (Layer 7):
The original data is now available to the application (e.g., web browser, email client), which can process it and provide the appropriate response to the user.

## Headers
TCP packets contain vaious sections of information known as headers that are added from encapsulation. 

- source port is the "door" or ""exit" port on the senders device that is being used to send data. I think of it like a specific exit in a building where data leaves from.  This value is chosen randomly (out of the ports from 0-65535 that aren't already in use at the time).  It allows the receiving device to know which "room" or "exit" the data came from on the sending device, so the receiver can know where to send the response.

- destination port is the "door" on the recieving device where data is going. it is like sending a letter to a specificdepartment or service within the company. It tells the receiving device where to direct the incoming data. For instance, port 80 typically handles web traffic, and port 443 handles secure web traffic (HTTPS).

- source IP Is the IP address of the device that's sending the packet. Think of it as the "home address" of the device sending the data. This helps the receiving device know where the data is coming from and allows responses to be sent back to the correct source.

- destination IP  is the IP address of the device that is supposed to receive the packet. It's the "destination address" where the data is being sent.  It ensures that the data gets to the right device on the network. Without it, the packet wouldn’t know where to go.

- sequence number - this is a number assigned to the first byte of data being sent over to the network. It is like the serial number for each chunk of data so that the reciever can reassembe the data correctly if it is broken down into multiple packets. Since data can travel over different paths, packets might arrive out of order. The sequence number helps the receiver put the pieces back in the right order.

- acknowledgement number - after a piece of data is recieved, the reciever sends a message of acknowledgement to let the sender know which data they recieved. This number tells the sender the sequence number of the next piece of data expected. It lets the sender know that the data was received correctly and allows for reliable communication. It’s part of making sure the data transfer is complete and accurate.

-checksum - this is a mathematical check done on data to create a checksum. This is to a value that helps verify if the data is correct. When the receiving device gets the data, it does the same math, and if the number doesn't match, something went wrong during transmission. This ensures the integrity of the data. If the checksum doesn’t match, it means there was an error in transmission, and the data might be corrupted.

- data is the acrual payload of the packet, the content you want to send. it could be a file or information youre transferring. it is the part of the packet you actually care about.

- flags are are like signals or instructions that tell the sender and reciever how to handle the packet. some flags indicate the start or end of a connection whilst others may indicate that data should be sent in a certain way (like asking for a reliable connection). flags help control how communication happens especially during the 3-way handshake (used to establish connections).  For example, flags can indicate that the sender is requesting a connection, or that it is done sending data.

## Three way handshake
this is the term given for the process that is used to establish a connection between two devices. The three-way handshake communicates using a few special messages, the main ones:

ISN - initial sequence number, it is a starting number that both the sender and reciever use to track data packets. Each time data is sent, it’s given a sequence number to keep track of the order in which the data should be read. The ISN is the first sequence number used when a connection is being established.

SYN - A SYN message is the initial packet sent by a client during the handshake. it is used to initiate a connection and synchronise the two devices together. 

SYN/ACK - this packet is sent by the recieving device (server) to acknowledge the synchronisation attempt from the client.

ACK - this is the acknowldegement packet which can be used wither by the client or server to acknowledge that a series of messages/packets have been successfully recieved. 

DATA- once a connection has been established, data (such as bytes of a file) is sent via the data message 

FIN- this packet is used to cleanly close the connection after it has been complete

RST - This packet abruptly ends all communication. this is the last resort and indicares there was some kind of problem during the process.

### Three way handshake process 

1. Step 1: SYN (Client to Server)

The client (the device that wants to initiate the connection) sends a message to the server to start a connection.

The client creates its Initial Sequence Number (ISN) and sends it as part of the SYN message.
Let’s say the client's ISN is 0, the message from the client will look like 

SYN, Sequence number = 0

2. Step 2: SYN/ACK (Server to Client)

When the server receives the SYN from the client, the server acknowledges the request and replies back with its own ISN.

The server generates its ISN (let's say 5000), sends the SYN signal, and also acknowledges the client's ISN by returning an ACK with the client's sequence number plus 1. This will look like 

SYN, Sequence Number = 5000

ACK, Acknowledging Client's ISN = 1 (client's ISN + 1)

3. Step 3: ACK (Client to Server)

Now, the client receives the SYN/ACK from the server and replies with its own ACK to acknowledge that it received the server's ISN.

The client increments the server's ISN by 1 (so from 5000 to 5001) and sends an ACK with this number. It will look like this 

ACK, Acknowledging Server's ISN = 5001 (server's ISN + 1)

What Happens After the Three-Way Handshake?

Now that the Three-Way Handshake is complete, the client and server can start exchanging data. The sequence numbers are used to ensure that each piece of data is sent in the correct order.

Each piece of data that is sent is given a sequence number.
If any data is lost or delayed, the receiving device can request a retransmission of the missing data using the sequence numbers.

## TCP Closing a connection
TCP will close a connection once a device has determned that the other device has successfully recieved all of the data. Becuase TCP reserves system resources on a device, it is best [ractice to close TCP connections as soon as possile. The device will send a "FIN" packet to the other device. with TCP of course, the other device will also have to acknowledge this packet. 

step 1 - FIN packet sent to server requesting to close the connection. The client decides to close the connection and sends a FIN (Finish) packet to the server.
This means the client is done sending data and wants to terminate its side of the connection.
However, the server can still send data back until it is also ready to close.
Message sent from Client to Server: FIN - hi i am done sending data, its time to close the connection.

step 2 - server sends an ACK package to acknowledge recieval of FIN package, step 2 - server sends an ACK package to acknowledge recieval of FIN package, initiate the closure of the connection. The message ACK- got it! but i still have some data to send 

step 3 - Once the server has finished sending all of its data, it sends its own FIN packet to the client, saying that it's now ready to close the connection. FIN = I am also done. lets close the connection

step 4 - The client receives the FIN from the server and acknowledges it by sending a final ACK. This message is to say "got it, connection closed"

## UDP/IP
User datagram protocol (UDP) is another protocol used to communicate data between devices.

unlike TCP, UDP is a stateless protocol that does not require a constant connection between the two devices for data to be sent. three way handshake does not occur and there is not any synchronisation between the two devices. UDP is used in situations where applications can tolerate data being lost (videostreaming or voice chat) remember the pros and cons of UDP

PROS:

Faster than TCP

UDP leaves the application to decide if there is any control override how quickly packets are sent. UDP lets applications control how fast data is sent instead of following strict TCP rules. This is great for real-time apps like gaming and streaming, where speed matters more than reliability. It allows custom handling of lost packets and avoids TCP’s automatic slowdowns. However, if not managed well, it can overload networks and cause packet loss. 

Since UDP doesn’t require a continuous connection, it can send data even if the network is unstable. If one path is weak or unavailable, packets can still get through via another route. This makes UDP great for real-time applications like video calls or gaming, where losing a few packets is better than waiting for a perfect connection. 

CONS

UDP does not care if data is recieved or not 

UDP gives developers flexibility but lacks built-in reliability, meaning lost or out-of-order packets aren't automatically fixed like in TCP. This puts the burden on the application to handle errors, which can lead to lag or missing data if not managed properly.

unstable connections can result in a terrible experience for the user. 

## UDP Headers

time to lie (TTL) - An expiry timer for the packet so it doesnt clog up your network if it never manages to reach a host or escape

source address- ip address of where the data is being transferred from so data knows where to return to 

destination address - the ip of the device where the package is being sent to, so the data knows where to travel next 

source port - source port is the "door" or ""exit" port on the senders device that is being used to send data. I think of it like a specific exit in a building where data leaves from. This value is chosen randomly (out of the ports from 0-65535 that aren't already in use at the time). It allows the receiving device to know which "room" or "exit" the data came from on the sending device, so the receiver can know where to send the response.

destination port - When you visit a website, your computer sends a request to the web server. That web server is always listening on a specific port (like port 80 for websites using HTTP). this port is not random unline the source port. 

data - This header is where data, i.e. bytes of a file that is being transmitted, is stored.

## Ports
Ports allow multiple applications or services to communicate over a network simultaneously without interference. If ports were not available, there would be no way to differentiate traffic for different applications or services. All the data would be sent through a single, undifferentiated "channel," causing the following issues:

1. Data Confusion
Without ports, data packets wouldn't have a clear destination. Since different applications require different types of data processing (e.g., web traffic, email, file transfers), there would be no clear way for the device to know how to handle incoming data.

For example:

Data from a web browser (HTTP) would be mixed up with data from an email client (SMTP), file transfer applications (FTP), and other services.

2. Single Entry Point for All Traffic

Without the concept of ports, there would need to be just one "entry point" or channel for all data traffic. This would essentially create a bottleneck where:
All incoming data from different applications would be waiting in line at the same "door" to be processed. The system would struggle to differentiate between all the different types of data, leading to inefficiencies and delays.

3. Resource Overload

In a system without ports, the resources required to manage communication (CPU, memory, network bandwidth) could be overwhelmed because the device would have to deal with all types of traffic at once, without any way to prioritize or route the data correctly.

4. Impossible to Manage Multiple Services
In today’s networked world, devices often run multiple services at once (e.g., web browsing, email, file sharing). Ports allow each of these services to operate on separate channels. If we didn't have ports:

A single connection would have to handle all types of traffic at once.
The network would face serious congestion because the communication system wouldn't have a way to prioritize or manage different types of data.

Why It Matters Which Port Data Goes To

It matters because each service expects data to come through a specific port. If data is sent to the wrong port, the device won't know how to handle it, or it might just ignore it entirely.

For example:

A web server listens on port 80 (HTTP) and expects data that corresponds to web requests. If you send HTTP data to a different port (say, port 25, which is for email), the server won’t know how to handle it.

### corresponding protocols with port numbers

Protocol	Port Number	Description
File Transfer Protocol (FTP)	21	This protocol is used by a file-sharing application built on a client-server model, meaning you can download files from a central location.
Secure Shell (SSH)	

22	This protocol is used to securely login to systems via a text-based interface for management.
HyperText Transfer Protocol (HTTP)

80	This protocol powers the World Wide Web (WWW)! Your browser uses this to download text, images and videos of web pages.
HyperText Transfer Protocol Secure (HTTPS)

443	This protocol does the exact same as above; however, securely using encryption.
Server Message Block (SMB)	

445	This protocol is similar to the File Transfer Protocol (FTP); however, as well as files, SMB allows you to share devices like printers.
Remote Desktop Protocol (RDP)	

3389	This protocol is a secure means of logging in to a system using a visual desktop interface (as opposed to the text-based limitations of the SSH protocol).

any port between numbers 0 and 1024 is known as a common port. 

while certain services ae commonly associated with specific ports ie (http usually uses port 80, https usually uses port 443), it is possible to run those services on non-standard ports (ie running a web server on port 8080 instead of 80). 

Protocols Follow Standards: By default, protocols like HTTP, FTP, etc., are associated with specific ports (e.g., HTTP = port 80). These are "standard" ports for these services.
Running on a Different Port: However, it's technically possible to run these services on other ports. For instance, you could set up a web server to listen on port 8080 instead of the default port 80. This is not breaking the protocol, just choosing a different port.

Applications Expect Standard Ports: Applications (like web browsers or other clients) generally expect services to be running on their default ports. For example, a browser typically assumes a web server is using port 80 when you type a URL like http://example.com.
Specifying a Custom Port: If you run a service on a non-standard port (like 8080 for HTTP), users or clients need to explicitly specify the port in the URL. For example:
Default port (no need to specify): http://example.com

Custom port (must include port number): http://example.com:8080
So, in short: You can run a web server on any port you like, but if you don't use the default port (80), users will need to include the port number in the URL to access it.
