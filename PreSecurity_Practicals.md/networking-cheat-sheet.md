# Networking Cheat Sheet
## Common networking commands 
These are commands you can run in the command line (terminal) to perform common networking tasks.:

| Command |  Description | example |
|----------|-------------|---------|
| 🏓 `ping` | **Tests if another computer (server) is reachable and how long it takes to communicate.** <br> 🔹 Uses **ICMP (Internet Control Message Protocol)** to send small test messages. <br> 📊 Measures **latency (response time)** in milliseconds (ms). | 🔹 **Type:** `ping google.com` <br> 🔹 **What happens?** Your computer sends test messages to `google.com`, and Google replies. <br> ✅ **Good output:** `Reply from 142.250.64.14: bytes=32 time=12ms TTL=56` (Google is reachable, 12ms delay). <br> ❌ **Bad output:** `Request timed out` (Google is unreachable) OR `High ms values (e.g., 300ms+)` (Slow network). |
| 🏃‍♂️ `tracert` (Windows) / `traceroute` (Linux) | **Shows the path data takes to reach a destination.** <br> 📍 Lists all the **hops** (routers) between your computer and the destination. <br> ⏳ Helps find **slow points or broken connections**. | 🔹 **Type:** `tracert google.com` (Windows) / `traceroute google.com` (Linux) <br> 🔹 **What happens?** Your computer sends test messages through every router on the path. <br> ✅ **Good output:** A list of IPs showing each hop, with response times (`ms`). <br> ❌ **Bad output:** `* * *` instead of numbers → A router is **blocking traffic or too slow**. |
| 🌎 `nslookup` | **Finds the IP address of a website (DNS lookup).** <br> 🔎 Checks if a domain name (e.g., `google.com`) is correctly translating into an IP address. <br> 🛠 Useful for **troubleshooting DNS issues**. | 🔹 **Type:** `nslookup google.com` <br> 🔹 **What happens?** Your computer asks the **DNS server** for Google’s IP. <br> ✅ **Good output:** `Name: google.com, Address: 142.250.64.14` (Google is resolving correctly). <br> ❌ **Bad output:** `Non-existent domain` → The website doesn’t exist OR **your DNS settings are incorrect**. |
| 🔍 `netstat` | **Shows all active network connections.** <br> 🛡 Helps detect **open ports, active connections, and potential security risks**. <br> 📡 Useful for **checking if your PC is connected to unknown devices**. | 🔹 **Type:** `netstat -an` <br> 🔹 **What happens?** Your computer lists all active network connections. <br> ✅ **Good output:** Known addresses (`192.168.x.x` = local network, `8.8.8.8` = Google DNS). <br> ❌ **Bad output:** Strange external IPs (`unknown foreign addresses`) → **Possible malware or unauthorized access**. |
| 🏠 `ipconfig` (Windows) | **Displays your computer’s IP settings.** <br> 🏡 Shows your **IP address, subnet mask, default gateway (router), and DNS servers**. <br> 🛠 Helps troubleshoot **internet and network connection issues**. | 🔹 **Type:** `ipconfig /all` <br> 🔹 **What happens?** Your computer lists network details. <br> ✅ **Good output:** Shows IP (`192.168.1.10`), Gateway (`192.168.1.1`), and DNS (`8.8.8.8`). <br> ❌ **Bad output:** IP starts with `169.254.x.x` → **No valid IP assigned (router issue)**. |
| 🏕️ `ifconfig` (Linux) | **Displays or configures network settings (like `ipconfig`, but for Linux).** <br> 📡 Used to check **IP address, MAC address, and Wi-Fi settings**. | 🔹 **Type:** `ifconfig` <br> 🔹 **What happens?** Shows network settings like IP and MAC address. <br> ✅ **Good output:** IP (`192.168.1.x`), MAC (`00:1A:2B:3C:4D:5E`). <br> ❌ **Bad output:** No IP address → **No internet connection assigned**. |
| 🌐 `curl` | **Fetches data from a website (like a browser but in text mode).** <br> 📜 Useful for **testing if a website is online**. | 🔹 **Type:** `curl http://example.com` <br> 🔹 **What happens?** Your computer **downloads the webpage’s raw data**. <br> ✅ **Good output:** HTML content appears. <br> ❌ **Bad output:** `Connection refused` → **Website is down or blocked**. |
| 📡 `telnet` | **Checks if a port is open on a remote computer.** <br> 🔓 Used for **testing server connections** but is **not secure**. | 🔹 **Type:** `telnet example.com 80` <br> 🔹 **What happens?** If the port is open, you connect. If not, it **fails or times out**. |
| 📜 `arp` | **Displays the ARP table (IP ↔ MAC address mappings).** <br> 🛠 Useful for **checking local network connections**. | 🔹 **Type:** `arp -a` <br> 🔹 **What happens?** Shows **MAC addresses linked to IPs**. |
| 🛣️ `route` | **Shows how data is being routed.** <br> 📌 Checks if your computer knows the way to the internet. | 🔹 **Type:** `route print` <br> 🔹 **What happens?** Displays the **routing table** (network paths). |
| 🔎 `dig` | **Advanced DNS lookup tool (like `nslookup` but more detailed).** <br> 🕵️ Useful for **troubleshooting DNS and mail servers**. | 🔹 **Type:** `dig google.com` <br> 🔹 **What happens?** Returns detailed **DNS info** about `google.com`. |
| 📶 `iwconfig` (Linux) | **Manages wireless network settings (Wi-Fi).** | 🔹 **Type:** `iwconfig wlan0 essid "MyNetwork"` <br> 🔹 **What happens?** Connects `wlan0` to **MyNetwork**. |
| 📦 `tcpdump` | **Captures and analyzes network traffic (packets).** <br> 📡 Used for **network security and troubleshooting**. | 🔹 **Type:** `tcpdump -i eth0` <br> 🔹 **What happens?** Shows **live network traffic**. |
| 🤠 `whois` | **Finds out who owns a website.** <br> 🕵️ Useful for checking **domain ownership and legitimacy**. | 🔹 **Type:** `whois google.com` <br> 🔹 **What happens?** Shows domain **owner, creation date, and contact details**. |




















