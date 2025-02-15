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

These changes to what you end up seeing are being done in what is called the BACKEND with the use of programming and scripting languages. it is called backend because what is being done is all done behing the scenes. you cant view the website's html source and see everything happening in the backend, while the html is the result of processing FROM the back end. Everything you see from the browser is front end. 
### Databases

often websites will need a way of storing information for their users. webservers can communicate with databases to store and recall data from them. databases can range from just a simple plain text file up to complex clusters of multiple servers providing speed and resilience. I will come across some common databses MySQL, MSSQL, MongoDB, Postgres and more - each with a specific feature.

### WAF (web application firewall)

a WAF sits between your web request and the web server, its primary purpose is to protect the webserver from hacking or denial of service attacks. it analyses the web requests for common attack techniques, whether the request is from a real browser rather than a bot. it also checks if an excessive amount of web requests are being sent by utilising something called "rate limiting" which will only allow a certain amount of requests from an IP per second. If a request is deemed a potential attack, it will be dropped and never sent to the webserver

## What is a webserver

A webserver is a software that listens for incoming connections and then utilises the http protocol to deliver web content to its clients. the most common seb server softwares i will come across is apache, IIS, nginx and nodeJS. A web server delivers files from what is called its root directory, which is defined in the software settings. for example, nginx and apache share the same default location of /var/www/html in Linux operating systems, and IIS uses C:\inetpub\wwwroot for the Windows operating systems. So, for example, if you requested the file http://www.example.com/picture.jpg, it would send the file /var/www/html/picture.jpg from its local hard drive.

### virtual hosts 

web severs can host multiple websites with different domain names, to achieve this, they use virtual hosts. the web server software checks the hostname being requested from the http being requested from the http headers and matches that against its virtual hosts (vitrual hosts are just text-based configuration files). if it finds a match, the correct website will be provided. if no match is found, the default website will be provided instead. 

virtual hosts can have their root directory mapped onto different locations upon the hard drive. for example, one.com being mapped to /var/www/website_one, and two.com being mapped to /var/www/website_two. 

there is no limit to the number of different websites you can host on a web server. 

### scripting and backend languages 

#### Frontend (Client-Side):

What is it?

The frontend refers to everything that users interact with directly on a website. It includes the design, layout, and content of the page.

Technologies Involved:

HTML – To structure the content (like paragraphs, headings, links).

CSS – To style the content (like colors, fonts, layout).

JavaScript – To make the page interactive (like form validation, animations, and event handling).

#### Where is it used?

The frontend runs in the user’s browser (like Chrome, Firefox, etc.). Everything you see and interact with directly (like buttons, menus, forms) is part of the frontend.

Example of Frontend Tasks:

Displaying text and images.

Animating transitions.

Showing or hiding elements when you click a button.

#### Backend (Server-Side):

What is it?

The backend is everything that happens on the server, behind the scenes. It's where the logic, data management, and database interactions happen. The backend doesn't interact directly with the user but supports the frontend by sending data, processing user inputs, and making decisions.

Technologies Involved:

Programming Languages – PHP, Python, Ruby, Node.js, Perl, etc. These are used to handle the logic of the website.

Databases – SQL, MongoDB, etc., for storing and retrieving data.

Servers – Like Apache or Nginx to serve web pages.

Where is it used?

The backend runs on a server (not on the user’s computer). When you request a page, the frontend asks the backend for data, and the backend sends it back to be displayed by the frontend.

Example of Backend Tasks:

Processing form submissions (like a contact form).

Handling user authentication (like login or registration).

Interacting with a database to store or retrieve data (e.g., showing a list of products from a database).




