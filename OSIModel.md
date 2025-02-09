# Networking Devices in the OSI Model

## 📌 Layer 7 – Application Layer (User Interaction)

Devices: End-User Devices (Computers, Phones, Web Servers, DNS Servers)

This layer deals with software applications that allow users to interact with the network (e.g., web browsers, email clients, streaming apps).

Examples of services at this layer: HTTP (web browsing), DNS (translating domain names to IP addresses), FTP (file transfers).

🛠 Devices Involved:

✅ Computers, Smartphones, Servers, DNS Servers, Web Servers – These interact with applications like web browsers and email clients.

✅ Web Servers – Store websites and respond to requests from users' browsers.

✅ DNS Servers – Translate domain names (e.g., google.com) into IP addresses.

## 📌 Layer 6 – Presentation Layer (Data Formatting & Encryption)

Devices: End-User Devices (Computers, Web Servers, Firewalls)

Converts data into a readable format, encrypts/decrypts it, and ensures compatibility between devices.

Examples: SSL/TLS encryption (used in HTTPS), data compression.

🛠 Devices Involved:

✅ Web Servers – Encrypt/decrypt data using SSL/TLS when handling HTTPS requests.

✅ Firewalls – Inspect encrypted traffic for security threats.

## 📌 Layer 5 – Session Layer (Managing Sessions)

Devices: End-User Devices, Servers, Firewalls

Establishes, maintains, and terminates communication sessions (e.g., logging into a website).

*NOTE, in the TCP/IP model there is no seperate session layer so TCP handles connection management directly in the transport layer of the TCP/IP model*

🛠 Devices Involved:

✅ Web Servers & DNS Servers – Maintain active connections for user sessions.

✅ Firewalls – Monitor and allow/block sessions based on security policies.

## 📌 Layer 4 – Transport Layer (Data Delivery & Reliability)

Devices: End-User Devices, Firewalls

Controls how data is broken into segments and reassembled on the other end.

Uses TCP (reliable, ordered delivery) and UDP (fast, no guarantee of delivery).

🛠 Devices Involved:

✅ Computers & Smartphones – Use TCP for browsing, UDP for video streaming/gaming.

✅ Firewalls – Block unwanted TCP/UDP traffic for security reasons.

## 📌 Layer 3 – Network Layer (IP Addressing & Routing)

Devices: Routers, Modems, Firewalls

Handles logical addressing (IP addresses) and routes packets between networks.

Routers determine the best path for data to travel.

🛠 Devices Involved:

✅ Routers – Assign local IPs, route packets between networks, and connect to ISPs.

✅ Modems – Act as a bridge between your home network and the ISP.

✅ Firewalls – Inspect network traffic and apply security rules.

## 📌 Layer 2 – Data Link Layer (MAC Addressing & Framing)

Devices: Switches, Network Interface Cards (NICs), Access Points

Uses MAC addresses to ensure that data reaches the correct physical device.

Creates frames from data packets before sending them across a local network.

🛠 Devices Involved:

✅ Switches – Forward data within a local network using MAC addresses.

✅ Access Points (APs) – Convert wired signals into Wi-Fi signals.

✅ NICs (Network Interface Cards) – The physical component inside computers that connects them to networks.

## 📌 Layer 1 – Physical Layer (Transmission of Raw Data)

Devices: Cables, Modems, Wi-Fi Access Points

Transmits raw electrical, optical, or radio signals.

🛠 Devices Involved:

✅ Ethernet Cables & Fiber Optic Cables – Carry data as electrical or light signals.

✅ Modems – Convert digital data to analog for ISP transmission.

✅ Wi-Fi Access Points – Convert data into radio signals for wireless transmission.

How It All Connects in a Real-World Scenario

You type www.google.com in your browser (Layer 7 – Application).

Your device queries a DNS server to find Google’s IP address (Layer 7 & 6).

A session is established with Google's web server (Layer 5 – Session).

Your request is broken into TCP segments or UDP datagrams (Layer 4 – Transport).

The request is given an IP address and routed across the internet (Layer 3 – Network).

The packet is sent through your router & ISP network using MAC addresses (Layer 2 – Data Link).

The data travels as electrical, optical, or radio signals over cables/Wi-Fi (Layer 1 – Physical).

Google’s server receives the request, processes it, and sends back the response, following the same OSI layers in reverse.
