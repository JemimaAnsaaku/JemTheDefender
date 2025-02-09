# OSI Model
The Open Systems Interconnection (OSI) model

The OSI model provides a framework for dictating how all networked devices will send, recieve and interpret data. 

One of the main benefits of the OSI model is that it allows devices to have different functions and designs on a network while communicating with other devices. Data sent across a network that follows the uniformity of the OSI model can be understood by other devices. 

Encaspulation - The OSI model consists of 7 layers which are arranged from layer 7 at the top to layer 1 at the bottom. (7- application, 6- presentation, 5- session, 4- transport, 3- network, 2- data link, 1- physical).
Encapsulation is the process of adding headers and trailers to data as it moves down the layers of the OSI model before transmission. Each layer wraps the data with its own control information to ensure proper delivery. 

## Layer 1 - Physical
The Physical Layer (Layer 1) is responsible for the actual transmission of raw data (bits: 0s and 1s) over a physical medium like cables, fiber optics, or wireless signals. It deals with hardware components and how data is physically sent and received.

-Data exists as binary (0s and 1s) in computers. The Physical Layer converts these into electrical signals (copper cables), light pulses (fiber optic cables), or radio waves (Wi-Fi).

-It specifies the types of cables, connectors, and wireless technologies used for communication. Example: Ethernet cables, fiber optics, and Wi-Fi signals.

- Manages Network Topology.Defines how devices are physically arranged (e.g., star, bus, ring topology).

Physical layer components - ethernet cables - connects network devices, copper cables - fibre optic cables converts to light pulses, wifi- wireless communication through radiowaves, NIC - network interfsce cards within your hardware that allows you to connect to a network.

Think of the Physical Layer as the infrastructure that carries data—like roads carrying cars. If you’re sending a message, this layer ensures that the actual physical transmission happens over a cable or wireless connection.

## Layer 2 Data link
Focuses on the physical addressing of the transmission. It recieves a packet from the network layer (including IP address for the remote computer) and adds in the physical MAC address of the recieing endpoint. Inside every network enabled computer is  NIC which comes with a unique MAC address to identify it. The NIC is like the security guard at a club—it lets you (the device) into the network. The MAC address is like the stamp you get on your hand to uniquely identify you among everyone else inside. You need both to connect and be recognized on the network!

MAC (Media Access Control) addresses are used for local communication within the same network (Local Area Network – LAN) and help devices identify each other at the Data Link Layer (Layer 2). However, MAC addresses don’t work between different networks, which is why we need IP (Internet Protocol) addresses. IP addresses are used for routing data between networks (Layer 3 – Network Layer), allowing devices to communicate across the internet. Routers use IP addresses to forward data to the correct destination, while NAT (Network Address Translation) allows multiple devices on a private network to share a single public IP address for internet access. In short, MAC is for local delivery, IP is for global delivery!

## Layer 3 Network
The magic of routing and re-assembley occurs (from small chunks to the larger chunk)

Routing data determines the most optimal path for which chunks of data should be sent. 

1. What is a "Chunk of Data"?
A general term for any portion of data that is broken down for transmission.
Data is not sent all at once; it is split into smaller pieces as it moves through the network.
These pieces are given specific names at different layers of the OSI model (segment, packet, frame, etc.).
Example: Think of a book being mailed page by page instead of all at once. Each "chunk" is a page, but depending on how it’s packaged and labeled, it takes on different names.

2. What is a "Packet"?
A specific type of chunk of data that belongs to the Network Layer (Layer 3).
A packet contains:
Payload (the actual data being sent)
Source and destination IP addresses (so routers know where to send it)

Other routing information (to help it reach its destination)

At this stage of networking, some protocols help determine the best path for data to reach its destination. You don’t need to worry about the details of these protocols, but they include OSPF (Open Shortest Path First) and RIP (Routing Information Protocol). The protocols choose the best route based on a few factors:

Shortest path: Which route has the fewest devices to pass through?
Most reliable path: Which route has fewer problems, like lost data packets?
Fastest connection: Which path is the fastest, like one using fiber instead of copper?

Layer 1 (Physical) and Layer 2 (Data Link) are concerned with communication within the same network (local network), meaning devices communicate using MAC addresses (in Layer 2).

Layer 3 (Network), where IP comes into play, is used for communication between different networks. This is where the IP address is used because it allows devices to send data across multiple networks (i.e., the internet or different subnets). The IP address helps routers figure out how to send data from one network to another.

Routing information protocol (RIP) - helps routers figure out the best way to send data across networks. It does this by choosing the route with the fewest hops (or routers) to reach the destination. How it works: Routers using RIP share information with each other to update their routing tables. The router with the fewest hops to a destination will be chosen as the best route.
Limit: RIP only allows up to 15 hops, so it’s best for smaller networks.
In short, RIP is a simple protocol that helps routers find the shortest path (fewest hops) for data to travel between networks.

OSPF (Open Shortest Path First) - is a link-state routing protocol. Unlike RIP, which uses the fewest hops, OSPF calculates the best path based on cost (e.g., connection speed, reliability). It updates routing tables faster and is better for larger, more complex networks. In short: OSPF is more efficient and flexible than RIP for determining the best route between networks.

## Layer 4 Transport
Vital in transmitting data across a network. It follows one of two different protocols. 

### TCP (Transmission Control Protocol) 

-designed with reliability and guarantee. This protocol serves a constant connection between the two devices for the amount of time it takes for the data to be sent and received. TCP also incorporates error checking into its design to guarantee that data sent from small chunks in the session (layer 5) has then been recieved and reassembled in the same order. 

PROS

- Guarantees accuracy of data

- Capable of synchronising two devices to prevent each other from being flooded with data

- performs a lot more processes for reliability

CONS

- Requires a reliable connection between the two devices. If one small chunk is not recieved then the entire chunk of data cannot be used.

- TCP Flow Control: TCP ensures data is sent in a controlled way so the receiving device isn't overwhelmed. If the receiving device is slow, TCP slows down the data transfer to match the device’s ability to handle the incoming data.
Waiting for Acknowledgments: TCP also waits for the acknowledgments that the data was successfully received before sending more. If the receiver is slow to process the data or send acknowledgments, TCP holds back and causes a delay.
This slowness can create a bottleneck, because the rest of the network traffic has to wait for the slow device, even if the other devices could process data faster. So, TCP creates a bottleneck by making sure data is delivered reliably, but if one device is slow, it slows everything down.

- TCP is significantly slower than UDP because more work has to be done by the devices using this protocol.

TCP is used for situations such as file sharing, internet browsing or sending emails because these services require data to be accurate and complete. 

### User Datagram Protocol (UDP)
UDP is not as advanced as TCP - any data that gets sent via udp is sent to the computer whether it gets there or not - (UDP doesn’t guarantee that data will be received successfully. It simply sends the data to the destination without waiting for an acknowledgment or checking if it was received properly.
"Sent to the computer whether it gets there or not" means that UDP sends the data, but it doesn’t track if it actually reaches its destination or if there are any issues, like loss or errors.)

PROS

-UDP is much faster than TCP

- UDP (User Datagram Protocol) doesn’t manage things like how fast data is sent or what to do if data is lost. Instead, it lets the application (like a video streaming app or a game) decide those things. This means UDP is faster because it skips over extra steps like checking for lost packets or waiting for confirmation that the data has been received. The app using UDP can handle data loss or errors in its own way, which is useful for things where speed is more important than perfect delivery, such as live video or online gaming. So, the advantage of UDP is that it’s quicker and uses less network resources because it doesn’t need to worry about checking and managing every single piece of data.

- UDP doesn’t reserve a continuous connection like TCP does, which is an advantage because it makes data transfer faster and more efficient. With TCP, a connection must be set up before data can be sent, which takes extra time and uses more resources. UDP skips this step and sends data immediately without the need for an ongoing connection, making it quicker and using fewer resources. This makes UDP ideal for real-time applications, like live streaming or online gaming, where speed is more important than ensuring every piece of data arrives perfectly.

CONS

- UDP doesn't care if the data is recieved

- it is quite flexible to software developers in this sense so it means that unstable connections result in a terrible experience for the user.

UDP is often useful in situations where small pieces of data are being sent like in protocols used for discovering devices (ARP, ARP (Address Resolution Protocol) is used to map a device's IP address to its MAC address. When a device wants to communicate with another device on the same network, it uses ARP to find the physical address (MAC) associated with an IP address. ARP sends a request to the network, and the device with the matching IP address responds with its MAC address, and DHC, DHCP (Dynamic Host Configuration Protocol) is used to automatically assign IP addresses to devices on a network. When a device connects to the network, DHCP allows it to request an IP address, and a DHCP server assigns one from a predefined range. This eliminates the need for manually assigning IP addresses to each device.) or larger files such as vide streaming where it is okay if some areas of the videos are pixelated - pixels are just lost data.)

## Session
Once data has been formatted from layer 6 (presentation), the session layer 5 will create and maintain the connection to other computer for which the data is destined. When a connection is established a session is created. Whilst this connection is active so is the session. This means that Once the presentation layer (Layer 6) has formatted or translated the data into a proper format that can be understood (like converting it into something readable), the session layer (Layer 5) takes over. The session layer's job is to create and manage the connection between your device and another device that will receive the data. In short, the session layer handles the connection between devices, making sure the communication can happen and stay active while the data is being transferred. Once the conversation (or session) is over, the session is closed.

The Session Layer (Layer 5) and TCP (Transport Layer, Layer 4) work together but have different roles. TCP is responsible for keeping the connection active and ensuring reliable data transfer, like establishing the connection, checking for errors, and managing how data is sent back and forth. Meanwhile, the Session Layer manages the overall session between devices, making sure that the communication (or "conversation") is properly started, maintained, and ended. While TCP handles the flow of actual data, the Session Layer ensures that multiple interactions between the same devices are organized and managed correctly. So, TCP maintains the connection, while the Session Layer manages the session or conversation between devices.

Checkpoints- if the session is lost, only the newest pieces of data are required to be sent, saving bandwidth (When the session is re-established, only the most recent data—the data that was not successfully transferred before the loss—needs to be sent again. This saves time and resources.
Saving bandwidth: Bandwidth refers to the amount of data that can be transferred over a network in a given amount of time (think of it like the width of a highway—more lanes = more cars = faster traffic). By only sending the newest pieces of data, less overall data is transmitted, which means less network traffic and less strain on your available bandwidth.)

Sessions are unique, data cannot travel over different sessions but only across different sessions - Imagine you're on a video call with your friend (Session 1), and you're also downloading a file from the internet at the same time (Session 2).

Session 1 is for your video call, where data (like your voice and video feed) is traveling back and forth between you and your friend.
Session 2 is for your file download, where data (like the file itself) is being transferred between your computer and a server.
Even though both are happening at the same time, the data from the video call doesn't mix with the data from the file download. Each session is unique and separate, meaning the video call data stays in Session 1, and the file download data stays in Session 2.  In short, data cannot travel between sessions, only within the session it belongs to.

Session - the technical term for when a connection has successfully established. 

## Layer 6 Presentation 
This is the layer where standardisation starts to take place.

The Presentation Layer acts as a translator between different systems, ensuring that data can be read and understood correctly no matter what format it was originally in.

Here's how it works:
Data format conversion: When data is sent from one device to another, it might be in a format that the receiving device doesn’t understand. For example, one computer might use a different character encoding (like UTF-8) than another. The Presentation Layer ensures that the data is converted into a common format that both computers can read.
Encryption/decryption: This layer can also handle things like encryption (to secure data) and decryption (to unlock it on the receiving end).

Imagine you’re sending an email from your computer. You may use a specific email client (like Gmail or Outlook), and that client sends the email in a particular format. But your friend might be using a completely different email client with a different format. The Presentation Layer ensures that your email looks the same to your friend, no matter what email client they are using.
So, when you send data, the Presentation Layer translates it into a format that the receiving device can understand. It makes sure everything looks right on both ends, even if the devices or applications are different.

Security features such as HTTPS occur at this layer

## Application
This is the layer we are all most familiar with. It is the layer in which protocols and rules are in place to determine how the user should interact with data sent or received. Everyday applications such as email clients (outlook microsoft gmail) and browsersprovide a friendly Graphical User Interface (GUI) for users to interact with data sent or recieved. 

DNS (Domain Name System), This is how website addresses are translated into IP addresses. 
