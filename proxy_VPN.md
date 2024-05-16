- [Forwarded Proxy Server](#forwarded-proxy-server)
- [HAproxy](#haproxy)
- [Reverse proxy](#reverse-proxy)
- [Forwarded Proxy vs VPN](forwarded-proxy-vs-vpn#)
- [](#)

# Info
A proxy typically refers to a server or a software system that acts as an intermediary between for example a user's device and the internet. 
Proxy helps with:
1. Acting like a Firewall.
2. Better management for sending & recieveing requests.
3. Caching.
4. Encryption/Decryption.
5. Security, masking the IP either of the client or the Server


# Forwarded Proxy Server
A proxy typically refers to a server or a software system that acts as an intermediary between a user's device and the internet. 
When you connect to the internet through a proxy, your device sends requests to the proxy server, which then forwards those requests to the internet on your behalf.    

With this setup:
* The caching can store static content for faster loading, saves bandwith & increase efficiency
* Block unwanted sites to be visited -> increase in productivity
* Enables one to bypass restricted sites (those who banned ur ip, banned a certain country etc)
![image](https://github.com/Keeriiim/CCNA/assets/117115289/5a5d6eeb-b88a-48f5-87c0-52a8c4831a74)


# Reverse proxy
Reverse proxy is a server that is within the LAN on the serveside.
Another benefit is that this way the proxy will work as a loadbalancer. 
Examples: HAproxy, Nginx

With this setup:
* The proxy helps zipping the request into a smaller size.
* proxy helps loadbalancing
* Helps with caching
* Instead of each server having it's certificate, the proxy get's the certificate
![image](https://github.com/Keeriiim/CCNA/assets/117115289/ca1f6583-0500-4d01-8bee-32263c19054f)


# Forwarded Proxy vs VPN
![image](https://github.com/Keeriiim/CCNA/assets/117115289/a6521540-4e0d-48f5-a664-a300b0607911)  
![image](https://github.com/Keeriiim/CCNA/assets/117115289/07b3e977-3eca-49dd-bf39-7f15d95e1575)  

# VPN
![image](https://github.com/Keeriiim/CCNA/assets/117115289/e0692179-cdb1-4885-82bb-2ee96e29d760)






 
