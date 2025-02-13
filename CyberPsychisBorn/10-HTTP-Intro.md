# What is HTTP

HyperText Transfer Protocol - This is used whenever you view a website 

developed by Tim Berners-Lee and his team between 1989-1991. HTTP is a set of rules for communicating with web servers for the transmitting of webpage data, whether that be HTML (HTML (HyperText Markup Language) is the standard language used to create web pages.), images, videos, etc. 

## What is HTTPS (HyperText Transfer Protocol Secure) 

HTTPS is the secure version of http. https data is encrypted, so it not only stops people from seeing the data you are receiving and sending, but it also gives you assurances that youre talking to the correct web server and not something impersonating it. 

## Requests and responses 

when we access a website, your browser will need to make requests to a web server for assets, such as HTML, Images and download the responses. Before that, yu need to tell the browswer specifically how and where to access the resources

## What is a url (uniform resource locator)

If you used the internet, you used a URL before. A URL is predominantly an instruction on how to access a resource on the interne. 

```example
hhtp://user:password@tryhackme.com:80/view-room?id=13task3
```

### Scheme

```example
http:
```
This is the scheme. It instructs on what protocol to use for acceessing the resource such as HTTP, HTTPS or FTP.

### User 

```
user:password
```
some services require authentication when you log in, you can put a username and password into the URL to log in 

### Host/domain

```
tryhackme
```
the domain name or IP address of the server you wish to access 

### Port 

```
:80
```
the port you are going to connect to. Usually :80 for http and :443 for HTTPS but can be hosted on any port between 1-65535

### Path

```
view-room
```
the file name or location of the resource you are trying to access 

### Query string 

```
id=1
```
extra bits od information that can be sent to the requested path. For example, /blog?id=1 would tell the blog path that you wish to receive the blog article with the id of 1.

### Fragment 

```
#task3
```
This is a reference to a location on the actual page requested. It is commpnly used for pages wirh long content and can have a certain part of the page directly linked to it so it is viewavle to the user as soon as they access the page. 

## Making a request 

 The crowser (client) makes a request:

 Imagine i want to visit www.tryhack.com in my broser. When i type the address into my broeswer and hit enter, my broswer is like a person asking for something from the server. It makes a request to the server saying "i would like the homepage of tryhackme.com, please"

 In HTTP terms, this request would look something like 

 ```
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com/
```

 1 GET/HTTP/1.1:

The browser is asking for the homepage ("/") of the website. 

It is telling the server it is using HTTP/1.1, the language or protocol it understands 

2 HOST: tryhackme.com

The browser is saying "i want to visit tryhackme.com

3 User-agent: Mozilla/5.0 firefox/87.0

the browswer is saying "hey, i am using firefox version 87. This helps the server understand how to send back the data that works best with the browser 

4 Referer 

 https://tryhackme.com/:

The browser is saying, "I came from the page https://tryhackme.com." This can help the server know where you clicked from.

5 A blank line 

The browswr is telling the server, "thats all i have to say, please respond now"

## The server responds

Now, the web server interprets the request. It reads what the broswer is asking for ans sends a response 

The server then sends back a response (like the store giving an item i asked for) this response includes:

```
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>
<head>
    <title>TryHackMe</title>
</head>
<body>
    Welcome To TryHackMe.com
</body>
</html>
```

### Breaking it down

1 HTTP/1.1 200 OK:

The server is saying, "Here is your request! everything is good. the page is ready for you"

200 OK is a status code thad means everything is successful. 

2 Server: nginx/1.15.8

The server tells the browser which software it is using to serve the website. in this case it is nginx

3 Date: Friday, 09 april 2021 13:34:03 GMT:

The server tells you the current date and time when the response was sent 

4 Content-type: text/html 

The server is saying, "i am sending you an HTML Page (the code that makes up a webpage)"

5 content-length:98 

The server tells the browser how long the response is, so it knows how much data to expect.

6 A blank line:

The server finishes its header with a blank line to say "Im done talking about metadata, now here is the content"

7 The HTML content:

the actual web page (the body of the response). In this case 

```
<html>
<head>
    <title>TryHackMe</title>
</head>
<body>
    Welcome To TryHackMe.com
</body>
</html>
```

Now rhe broswer displays the response (your computer), gets the html content from the server and it turns into the webpage you can see and interact with. 

## HTTP Methods 

HTTP methods are a way for the client to show their intended action when making an HTTP request. There are a lot of http methods, but we will cover the most common ones, although mostly youll deal with the GET and POST method.

GET request

this is used from getting information from a server 

POST REQUEST

This is used for sub,itting data to the web server and potentially creating new records

PUT REQUEST

This is used for submitting data to the webserver to update information

DELETE REQUEST

Used for deleting information/records from a web server

## HTTP STATUS CODES

I have previously learned about how when a server reponds, the first line is always containing the status codes which informs the client of the outcome of their request and potentially how to handle it. they can be broken down into 5 different ranges.

100 - 199 = information response - these are sent to tell the client the first part of their request has been accepted and they should continue sending the rest of their request (these requests are now no longer common)

200 - 299 = success  - this range of status codes is used to tell the client that their request was successful

300 - 399 = redirection - these are used to reditect the clients request to another resoucr. this can be wither to a different webpage or different websitee.

400-499 = client errors - used to inform the client that there was an error with their request.

500-599 =server errors - errors happening on server side and usually indicate a major problem with the server handling request. 

specific common codes 

| HTTP code | definition |
|------------|-------------|
|200 | OK	The request was completed successfully.|
|201 | Created	A resource has been created (for example a new user or new blog post).|
|301 | Moved Permanently	This redirects the client's browser to a new webpage or tells search engines that the page has moved somewhere else and to look there instead.|
|302 |Found	Similar to the above permanent redirect, but as the name suggests, this is only a temporary change and it may change again in the near future.|
|400 | Bad Request	This tells the browser that something was either wrong or missing in their request. This could sometimes be used if the web server resource that is being requested expected a certain parameter that the client didn't send.|
|401 | Not Authorised	You are not currently allowed to view this resource until you have authorised with the web application, most commonly with a username and password.|
|403 | Forbidden	You do not have permission to view this resource whether you are logged in or not|
|405 | Method Not Allowed	The resource does not allow this method request, for example, you send a GET request to the resource /create-account when it was expecting a POST request instead |
|404 | Page Not Found	The page/resource you requested does not exist.|
|500 |Internal Service Error	The server has encountered some kind of error with your request that it doesn't know how to handle properly |
|503 | Service Unavailable	This server cannot handle your request as it's either overloaded or down for maintenance.|

## Headers

Headers are additional bits of data you can send to a web server when making requests. Although they are not strictly required when making a http request, youll find it difficult to view a website properly. 

Headers are sent from the client (usually your browser) to the server 

### Host

Some web serverss host multiple websites by providing the host headers so by providing the host headers you can tell it which one we require. Otherwise you will just recieve the default website from the server. 

### User-Agent 

This is your browser software and version number. telling the webserver your browser software helps it format the website properly for your browser and also some elements of html (skeleton structure: headings, paragraphs images, buttons, links etc), javascript (interactivity and functionality - animations, pop ups, buttons, dynamic updates, etc) and css (cascading style sheets: design and styling - fonts colours and layout) are only available in certain browswers.

### Content length 

When sending  data to a web server such as in a form, the content length tells the web server how much data to expect in the web request. This way the server can ensure it isnt missing any data. 

### Accept-encoding 

tells the web server what types of compression methods the browser supports so the data can be made smaller for transmitting over the internet 

## Cookie

Data sent to the server to help remember your information 

## Common response headers 

headers that are returned from the web server to the client after a request

### set-cookie 

- information to store which gets sent back to the web server on each request 

### cache-control

How long to store the content of the response in the browsers cache before it requests it again 

### content-type 

- tells the client what kind of data is being returned i.e., html, css, javascript, images, etc. Using the content-type header the browser then knows how to process the data 

### content-encoding

- what method has been used to compress the data to make it smaller when sending over the internet 

## cookies 

small pieces of data that websires store on my browser to remember things about me. comapnies do this to:

remember me - ie keep me logged in 

track preferences - like dark mode or language preferences 

for analytics - track visitors and improve their site 

ads and tracking - show me relevant ads based on my browsing history

because http is stateless (does not keep track of previous requests) cookies can be used to remind a web server of who you are, some personal settings for the website or whether you have been to the website before 

The cookie wont typically be a clear-text string where you can see the password, but a token
