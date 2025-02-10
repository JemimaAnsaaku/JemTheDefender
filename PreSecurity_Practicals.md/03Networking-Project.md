# First Project - building a LAN

Today is the day 😄 I have recently finished the networking modules on TryHackMe, so I have decided a brilliant way to round off and apply what I have learned is to create my first project and include it within my Github portfolio. Knowledge is better when it is reinforced within a practical activity. I'd like to start off simple (I am a complete beginner) and build a simple LAN with client-server communication. 

## Key words:

A server: A computer or system that waits for client connections, processes requests and sends back responses. 

A client: A computer or system that connects to a server, sends requests and processes responses 

Folder: A box used for organisation 

File: A container where you store code.

## Skills I will learn.

By setting up my own LAN I will reinforce my understanding of basic networking concepts, work with TCP/IP sockets for establishing communication between client and server, handle client-server communications and requests and further understand the numerous layers of the OSI model, grasp the basics of encryption/authentification and truly understand how everything fits together in a real life scenario.

## Tools used

### Visual studio code 

This is my code editor that will allow me to write, edit and debug the networking code

### Python 

Python is one of the most beginner friendly coding languages, and is great for creating network clients and servers 

### Terminal 

This is built on my computing device (macbook) and will allow me to run commands directly on my computer such as ping, netstat, telnet.

### Netcat 

A simple tool that i can use for testing connections between the client and server

### Wireshark 

Wireshark is a network packet analyser. It will allow me to monitor the data being transferred within my network which is essential for troubleshooting and understanding client behaviour. 

### Heroku (conditional for use)

If i decide to deploy my server to test my network project with real users over the internet, Heroku is a cloud platform that is able to host. 

### Docker 

This will simulate different network environments for testing my server and client to allow me to create isolated environments for testing.

## Building LAN 
### Setting up the server
Firstly, i will look into setting the server, which is the central part of any client-server architecture. A server remember is key in processing client requests and responses. 

In my project, the server will wait and listen to client response and requests on a specific port. I will be using Python as a programming language as it beginner friendly. 

Stting up a server will establish the client-server communications over the network.

I will be writing my server code and client code in Video Studio Cose (VS) remember, which is a code editor and widely used for writing Python code due to its great support for suntax highlighting, debugging and extensions. 

Firstly, I created a LAN folder to within VS code to mark the beginning of my project. Within the project i will open a file within the LAN folder and label it Server.py (python files always end in python).

This is where I will write the server code. 

#### step 1
```python
Import socket. 
```
Socket is a built in Python module (A module in Python is a file that contains reusable code— it can be functions, variables, or classes that you can import and use in other programs. Think of it as a toolbox that helps you avoid writing the same code over and over again) that allows computers to communicate over a network. 

The import statement is used to bring in external code. Modules must be imported before they are used or python will not recognise them

This is important because without it, we wouldnt be able to create a client-server connection

#### step 2
Then we must create a socket which is like a "phone" a server will use to send and recieve data

```python
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
```
Socket.socket () creates a new socket - this is a network connection endpoint 

sockey.AF_INET tells python we are using IPv4 Addresses (regular IP addresses 4 octets)

socket.SOCK_STREAM tells python we are using TCP which is reliable and ensures data is delivered correctly 

socket.AF_INET and socket.SOCK_STREAM are constants (predefined values in the module)

Without this, the server would have no way to communicate with clients.

#### Step 3
Bind the server to an IP address 
```python
server_socket.bind(("0.0.0.0", 8080))
```
.bind(("0.0.0.0", 8080)) associates the server with an IP address and a port.

"0.0.0.0" is a special IP address that means "listen on all available network interfaces."

8080 is the port number, which is like a "door" that clients use to connect.

The .bind() method requires a tuple → ("IP", PORT).

ip is a string (dots are not allowed in python) and an ip address is not used in maths and ports are integers

If we don’t bind the server to an IP and port, the operating system won’t know where to send incoming client requests.

#### step 4
We start listening for connections 
```python
server_socket.listen(5)
```
.listen(5) puts the server into "listening mode", waiting for clients to connect.

The 5 means the server can queue up to 5 connections before rejecting new ones.

.listen() takes one argument, which is the number of queued connections.

Must be called AFTER .bind(), or Python will throw an error.

If we don’t call .listen(), the server won’t wait for connections and will close immediately.

#### step 5
Accept a connection 
```python
client_socket, client_address = server_socket.accept()
```
.accept() waits for a client to connect and , once connected:

client_socket represents the client's connection 

client_address stores the clients IP address 

Tuple unpacking → .accept() returns two values, which must be assigned to two variables.

Blocking function → The program pauses until a client connects.

Without this, the server wouldn’t know when a client is connected and couldn’t communicate with it.

#### step 6
sending a message to the client 
```python
client_socket.sendall("Hello from the server!".encode())
```
.sendall() - sends data to the client 

.encode() - converts the message into bytes, because network data must be sent as bytes. 

if we dont encode the string, the network can't send it, and we will get an error

#### step 7
closing the connection
```python
client_socket.close()
```
Once the server is done talking to the client, closing the connection is good practice to free up system resources. If we dont close the connection we might run out of available connections, causing performance errors

## Mistakes made and corrections 

### Mistake with Variable Naming (Mixing server and server_socket):

Mistake: In my initial code, I created the socket object and assigned it to the variable server but then mistakenly referenced it as server_socket in subsequent lines. This caused errors because Python was looking for a variable named server_socket, which didn’t exist in my code.

Correction: I corrected this by consistently using the same variable name, server_socket, throughout my code. I ensured that all socket operations (like bind(), listen(), and accept()) were performed on the correct object, which was the server object that I had initially created.
```python
server_socket.bind(("0.0.0.0", 8080))  # Incorrect reference
```
```python
server.bind(("0.0.0.0", 8080))  # Correct reference
```

### Mistake with the recv() Method (Not Storing Data Properly):

Mistake: Initially, I did not have a command that processed client data, so i had to add a recv() command to actually recieve it. 
