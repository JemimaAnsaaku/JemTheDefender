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

300 - 399
