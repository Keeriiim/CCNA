












# DNS
Domain Name System (DNS) — often described as the phonebook of the internet. DNS translates domain names into IP addresses: contoso.com ➜ 192.0.2.1
DevOps professionals use DNS to map domain names to servers, services, or other resources within their infrastructure.

## What is a domain?
A domain is a human-readable name that maps to an IP address, allowing users to access websites, email services, and other internet resources without remembering numeric addresses.

ICANN (Internet Corporation for Assigned Names and Numbers) 
* A nonprofit organization that oversees the global domain name system.
* It controls the master database of all Top-Level Domains (TLDs) like .com, .org, .net, .io.

* TLDs (Top-Level Domains) like .com, .org, .net, etc. are not databases themselves — they are categories of domains.
* Each TLD has a corresponding registry that operates and maintains a database of all domain names registered under that TLD

* .com is a TLD.

Verisign is the registry that maintains the authoritative database of all .com domain names (e.g., google.com, contoso.com, etc.).

That .com database stores:

Which domain names exist

Who the registrar is

Which name servers are responsible for DNS lookups

Example: GoDaddy, Namecheap, Google Domains, etc.

The registry tracks which registrar registered the domain.

If something needs to be changed or resolved about the domain, it goes through the registrar that manages it





# DNS Records

## A Record (Address Record):
* Maps a domain name to an IPv4 address (32-bit): yourdomain.com → 203.0.113.5
* Must use public IP addresses
* If ur hosting on a local server, portforwaring must be set on the router
* If your hosting on Azure / Aws, portforwaring must be set on their plattform

## AAAA Record (IPv6 Address Record):
* Maps a domain name to an IPv6 address (128-bit). yourdomain.com -> 2001:0db8:85a3:0000:0000:8a2e:0370:7334.

## A + Dynamic DNS Record:
* Dynamic DNS (DDNS) allows you to automatically update the IP address associated with a hostname in real-time.
* A Dynamic DNS record typically requires a DNS host that supports Dynamic DNS.
* You need to install software or use a script on your device that gets the current IP and sends it to your DNS provider/host (ex cloudflare).

## CNAME (Canonical Name) record
* Creates an alias from one domain name to another.
It's often used when you want a domain or subdomain to point to another domain name.
For example, if you have a domain name www.example.com and you want it to point to example.com, you would create a CNAME record for www.example.com with the value example.com.
ANAME records are similar but are often provided by DNS hosting services as a solution for apex (root) domain aliasing, where CNAME records are not allowed.

## Subdomains vs. Path-Based URLs:
* Subdomains are used to create distinct sections or services of your website. They usually represent entirely separate areas or functionalities, like a blog (blog.example.com), a shop (shop.example.com), or a forum (forum.example.com).
* Subdomains typically indicate something different enough that it may require separate hosting or infrastructure.

* Paths (e.g., example.com/home, example.com/page1) are used to create different pages or sections on the same domain. These are simply different paths under your main domain.







# The DNS Route
1. Your computer (asks resolver) 
2. DNS Resolver (asks root Name Server) 
   * Receives DNS queries from your device -> queries other DNS servers
   * Returns the final IP address back to your device
3. Root Name Server (points to TLD server)  
   * The Root DNS servers are the starting point for all DNS lookups. They're like the index of 
     a massive internet phonebook.
   * There are 13 root server systems, labeled A to M (e.g., Root Server A, Root Server B…).
   * Each one is actually a network of servers worldwide using Anycast routing.
   * They don’t store domain info directly — just which TLD name servers to ask next (like 
     .com, .org, etc.).
4. TLD Server (e.g., .com) (points to domain’s name server)
   * Your resolver then asks the .com name servers (managed by Verisign)
   * Reply: “The name servers for abc.com are ns1.abcdns.com and ns2.abcdns.com.”
5. Authoritative Name Server for the Domain
   * It holds the actual DNS records (like A, MX, CNAME, TXT) for contoso.com.
   * “Hey ns1.contosodns.com, what is the IP address for www.contoso.com?”
   * The name server replies: “The A record for www.contoso.com is 192.0.2.1.”
  


# Configuring DNS
If you have broadband via ISP you will probably have their DNS servers. You can see the servers in the GUI of your router -> Search for Settings / Internet / WAN / DNS
**nslookup** - > Shows your DNS resolver (in my case it was my router Default Server:  dsldevice.lan Address:  ::IpV6:: )

My example :
* Computer sends DNS queries to your router (dsldevice.lan)
* The router forwards those queries to the ISP's DNS servers (192..... , 192 ....)
* These servers resolve the domain and send the answer back


## Change DNS servers 
### On your local machine
* Press Windows + R -> type ncpa.cpl
* Right click on your Ethernet adapter -> properties -> Ipv4 -> properties

![image](https://github.com/user-attachments/assets/fa372e85-4065-4fdd-8b70-75cc6871c289)

### For all devices connected to the router
* Go to the GUI of your rotuer -> find DNS settings -> choose DNS servers

**ipconfig /flushdns** Remember to clear the dns cache after a change to avoid problems 


# TL;DR:
* Changing your DNS server only changes how you get the IP, not how you get to the IP.
* Meaning -> a tracert won't mater because the DNS query is BEFORE the routing


# Devops stuff

## Service Discovery
DNS can be used for service discovery, allowing applications and services to locate each other dynamically within a network.
DevOps teams can leverage DNS-based service discovery mechanisms to enable automatic detection and communication between microservices, containers, and other components of a distributed system.

## Load Balancing:
DNS-based load balancing distributes incoming traffic across multiple servers or endpoints to improve reliability, scalability, and performance.
DevOps engineers can use DNS load balancing techniques to distribute traffic evenly among backend servers, reduce latency, and achieve high availability for applications.

## Global Traffic Management:
DNS-based global traffic management (GTM) allows organizations to route user traffic based on factors such as geographical location, network conditions, or server availability.
DevOps teams can use GTM solutions to optimize the delivery of applications and services, improve user experience, and ensure high availability across distributed environments.
DNS Management Tools:

DevOps professionals use DNS management tools and platforms to configure, monitor, and troubleshoot DNS infrastructure effectively.
These tools provide features such as DNS record management, zone management, health checks, monitoring, and automation capabilities to streamline DNS operations.
DNS Security:

DNS plays a crucial role in security, and DevOps teams need to ensure the security and integrity of their DNS infrastructure.
Best practices for DNS security include implementing DNSSEC (DNS Security Extensions), securing DNS servers against DDoS attacks, and monitoring DNS traffic for anomalies or malicious activity.
Integration with Infrastructure as Code (IaC):

DNS configuration can be managed and automated using Infrastructure as Code (IaC) tools such as Terraform, Ansible, or CloudFormation.
DevOps practitioners can define DNS resources, records, and configurations as code, enabling version control, reproducibility, and consistency in DNS management across environments.





