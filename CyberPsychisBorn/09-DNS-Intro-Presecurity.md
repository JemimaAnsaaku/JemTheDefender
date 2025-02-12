
# DNS in detail

DNS (domain name system) provides a simple way for us to communicate with devices on the internet without remembering complex numbers. Like every house with a unique address for sending mail directly to it, every computer on the internet has its own unique address to communicate with it called an IP address. When you want to visit a website, it isnt convinient to remember this complicared set of words, which is where DNS can help. So instead od remembering an ip address you can remember the website name ie google.com instead. 

### Domain Hierachy
A TLD (top-level domain) is the most righthand part of a domain name. For example, the tryhackme.com TLD is .com. There are two types of TLD, gTLD (generic top level domain) and ccTLD (Country Code Top Level Domain). Historicallym a gTLD was meant to tell the user the domain name's purpose. For example a ".com" would be for commercial purposes, ".org" would be for an organisation, ".edu" for education and ".gov" for the goverment. And a ccTLD was used for geographical purposes, for example, ".ca" = sites based in canada, ".co.uk" = sites basied in the UK, etc. Due to such demaand, there is an influc of new gTLDs ranging from .online, .club, .website, etc. There are over 2000 gTLDs.

### Second-level Domain
Taking 'tryhackme.com' as an example, the second level domain is tryhackme. When registering a domain name, the second level is limited to 63 characters and the TLD can only use a-z 0-9 and hyphens(cannot start or end with hyphens or hae consecutive -- hyphens.

## subdomain 

A subdomain sits on the left hand side of the second-level domain using a period to seperate it. for example, in the name admin.tryhackme.com, the admin part is the th subdomain. A subdomain has the same creative restrictions as a second level domain. you can use multiple subdomain splits with periods to create longer names such as secure.admin.tryhackme.com but the length must be kept to 253 characters or less. there is no limit to the number of subdomains you can create for your name.

## DNS record types 
A DNS isnt just for websites though, multiple types of DNS record exist. We will go over some of the most common ones youre likely to come across

resolve - to find, determine, or translate a reference into its actual value or destination

### Arecord 
These records resolve to IPv4 addresses (4 octets). -  example 104.26.10.229. When you enter example.com in your browser, your computer asks a DNS server:
"What is the IP address for example.com?" The DNS server resolves (finds and returns) the IPv4 address. our browser now knows where to go and connects to

### AAAA record 
These records resolve to IPv6 addresses for example 2606:4700:20::681a:be5. Similar to an A record, but resolves to an IPv6 address instead of IPv4. IPv6 is the next-generation IP system because we are running out of IPv4 addresses. If your computer supports IPv6, it may prefer using AAAA records instead of A records.

### CNAME record 
These records resolve to another domain name.  Redirects one domain name to another domain name, rather than an IP address. If you visit store.tryhackme.com, the DNS resolves (redirects) you to shops.shopify.com. Now, another DNS request is made to find the IP address of shops.shopify.com.
Now, another DNS request is made to find the IP address of shops.shopify.com.

### MX Record (mail exchange record
specifies the mail server responsible for recieving emails for a domain
```example
tryhackme.com → alt1.aspmx.l.google.com
```
if someone ends an email to user@tryhackme.com, their email provider asks "where should i deliver emails for tryhackme.com?" The DNS resolves this request and returns alt1.aspmx.l.google.com, meaning google handles the emails. Some MX records have priority numbers (lower numbers=higher priority). If the main mail server is down, emails are sent to the back up server instead. 

Example of MX Records for tryhackme.com

Let’s say tryhackme.com has these MX records:

| priority | mail server (MX Record) |
|-----------|-----------------|
| 10 | mail1.tryhackme.com (Primary Mail Server)|
| 20 | mail2.tryhackme.com (Backup Mail Server) |
| 30 | mail3.tryhackme.com (Second Backup Mail Server) |

the priority number decide which server to use first (lowest number = highest priority) 

the emails will be going to main1.tryhackme.com in this case.

### TXT record (text record)
stores text-based data in a DNS record. for example in email security, it prevents email spoofing (fake emails pretending to be from your domain)
```example
v=spf1 include:_spf.google.com ~all
```
A TXT record is a special type of record that stores text-based information about a domain. unline A, AAAA, MX record or CNAME records (whoch help direct traffic, TXT records do not point to IP addresses or servers. Instead they store text data that can be used for security, authentication or verification. 

eample: Email Security (SPF, DKIM, DMARC)

TXT records help prevent spam, phishing, and email spoofing by defining rules about which servers are allowed to send emails on behalf of a domain.

## What happens when you make a DNS request

1. When you request a domain name, your computer first checks its local cache (temporary storage location) to see if you've previously looked up the address recently. If not, a request to your recursive domain (A recursive DNS server is a specific type of DNS server that handles the entire process of resolving a domain name to an IP address for a client) will be made. 

2. A recursive DNS server is usually provitded by your ISP, but you can also choose your own. This server also has a local cache of recently looked up domain names. If a result is found locally, this is sent back to your computer and your request ends here (this is common for popular services such as facebook, google, etc) if the request cannot be found locally, a journey begins to find the correct answer, starting with the internet's root DNS servers

3. The root servers act as the DNS backbone of the internet; their job is to redirect you to the Top lvel domain server, depending on the request for example, if you request www.tryhackme.con, the root server will recognise the the top level domain .com and refer you to the correct TLD server that deals with .com addresses.
4. 
5. the tld server holds records for where to find the authoriative server to answer the dns request. Authoritative DNS server = nameserver. Nameserver is the server that is responsible for storing the DNS records for a paticular domain name and where any updates to your domain name DNS records would be made. depending on the record type, the DNS record is then sent back to the recursive DNS server where a local copy will be cached for future requests and then relayed bacl ro rhe orifinal client that made the resquest. DNS records all come with a TTL (time to live) value This value is a number represented in seconds that the response should be saved for locally until you have to look it up again. Caching saves on having to make a DNS request every time you communicate with a server.
