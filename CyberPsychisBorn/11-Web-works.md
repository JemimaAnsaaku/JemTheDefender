# Putting it all together

from the previous modules, i have learned a lot about the things that go on behind the scenes when you request a webpage in your browser 

to fummarise, when you request a websire, your computer needs to know the server's ip address to talk to it, for this it uses DNS. your computer talks to the web using a sepecial set of commands called the HTTP protocol and the webserver returns the html, javascript, css, images, etc which your browser then uses to correctly format and display the website to you 

request website - dns finds web server ip - web server responds with data in the form of html, javascript, css, images, etc - view website 

## Other components

### load balancers

when a website's traffic starts getting quite large or is running an application that needs to have high availability, one server might no longer do the job. Load balancers provide two main features, ensuring high traffic websites can handle the load and providing a failover if a server becomes unresponsive. 

When you request a website with a load balancer, the load balancer uses different algorithms to help it decide which server is best to deal with the request. a couple of examples of these algorithms are round-robin, which sends it to each server in turn, or weighted which checks how many requests a server is currently dealing with and sends it to the least busy server (dont get this confused with the MX record priority system thats about mail), 

load balancers also perform periodic checks with each server to ensure they are running correctly, this is called a health check. if a server doesnt respond appropriately or at all, the load balancer will stop sending traffic until it responds appropriately again.

### CDN (Content delivery networks)

#### How Does a CDN Work?

A website owner uploads their static files (like images, JavaScript, and videos) to a CDN.
The CDN stores copies of these files on multiple servers around the world.

When a user visits the website:

The CDN finds the closest server to their location.

It sends the files from that server instead of the original website.

This makes the website load much faster because the files don’t have to travel long distances.

Static vs. Dynamic Files (Concepts Explained Clearly)

### What is a Static File?
A static file is a file that does not change when a user visits a website. Every visitor receives the exact same content from the server. These files are pre-made and stored on the server or a CDN.

Examples of Static Files:

- HTML files (if they are not modified dynamically)
- CSS files (styling)
- JavaScript files (before execution)
- Images (JPEG, PNG, GIF)
- Videos

Think of it like: A printed book 📖—once printed, every person who buys the book gets the exact same content.
2️⃣ What is a Dynamic File?

### A dynamic file is a file that changes based on user interactions, database content, or other conditions. These files are generated on the fly when requested.

Examples of Dynamic Content:
- A personalised user dashboard (e.g., "Hello, jemima!")
- A social media feed (different posts for different users)
- A shopping cart (unique items per user)
- Search results (change based on what you type)

### Databases

often websites will need a way of storing information for their users. webservers can communicate with databases to store and recall data from them. databases can range from just a simple plain text file up to complex clusters of multiple servers providing speed and resilience. I will come across some common databses MySQL, MSSQL, MongoDB, Postgres and more - each with a specific feature.

### WAF (web application firewall)

a WAF sits between your web request and the web server, its primary purpose is to protect the webserver from hacking or denial of service attacks. it analyses the web requests for common attack techniques, whether the request is from a real browser rather than a bot. it also checks if an excessive amount of web requests are being sent by utilising something called "rate limiting" which will only allow a certain amount of requests from an IP per second. If a request is deemed a potential attack, it will be dropped and never sent to the webserver

## What is a webserver

A webserver is a software that listens for incoming connections and then utilises the http protocol to deliver web content to its clients. the most common seb server softwares i will come across is apache, IIS, nginx and nodeJS. A web server delivers files from what is called its root directory, which is defined in the software settings. for example, nginx and apache share the same default location of var/www/html



