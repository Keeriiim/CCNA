




# Info
Netfilter is the firewall framwork while iptables is a user-space utility program that allows a system administrator to configure the IP packet filter rules of the Linux kernel firewall(manage & controll netfilter).
It is used to set up, maintain, and inspect the tables of IP packet filter rules in the Linux kernel. These tables contain chains of rules for handling network traffic, including filtering, NAT (Network Address Translation), and packet mangling.  


Tables: iptables uses different tables to define sets of rules for various tasks:  

Filter Table: This is the default table, used for filtering packets (allowing or blocking).  
NAT Table: Used for Network Address Translation, modifying the source or destination of packets. (redirect connections to other interfaces on the network) 
Mangle Table: Used for specialized packet alteration.  (Modifying and changing a packet / connection)
Raw Table: Used for configuration exemptions from connection tracking.  

![image](https://github.com/Keeriiim/CCNA/assets/117115289/e08500e1-9fe0-4c0b-9ebc-b3b2319dee44)  

Nat
- Prerouting chain: Used after the packet has entered the network interface and before it is sent out
- Postrouting chain: After the packet has left the interface (the decision has been made)

## Chain
Chains are "tags" that define and match packets to their state

# Packet flow
Incoming - processed - Output

Firewall rules: Managing input/output of packets in relation to a server  
  Ex block all incomming SSH in port 22  
  Block HTTP connections  


Target: What is going to happen with a packet  
Once a packet is matched with a rule a target is set  
1. Accept - Return 200  
2. Reject - Return Rejected  
3. Drop - No feedback

 If there is no incoming rule -> default, if no default -> accepted

# Getting started from VM
Default firewall for  
Debian: Ufw  
Centos: Firewalld  


Let's clear uninstall the services because they are interfaces containing iptables(holding some predefined rules).
```bash
iptables -F              # Clear the current tables
iptables -L              # List all chains of iptables

apt install iptables     # Installing ip tables
```
![image](https://github.com/Keeriiim/CCNA/assets/117115289/54cfecb1-2c16-4d7d-871f-b1c4066abdf2)  


When starting make sure all policies are set to ACCEPT.
```bash
iptables --policy INPUT ACCEPT
```
### If you set policy INPUT to DROP your cli will freeze and not enable you to reconnect.
```bash

```


# Blocking

## a specific ip adress
-I for top, -A for bottom of the list -j for Target  
![image](https://github.com/Keeriiim/CCNA/assets/117115289/a5c48774-d86b-470b-8e5c-43f9de30fa73)  

Subnes can also be added.  
![image](https://github.com/Keeriiim/CCNA/assets/117115289/6f1003a1-1886-4ed8-bc15-1ad5b0b3f59b)  

# Block Http traffic except my own
```bash
iptables -I INPUT -p tcp --dport 80 -j DROP       # -p tcp for protocol, --dport 80 for connection type
iptables -I INPUT -p tcp --dport 80 -s 'MyIP* ACCEPT       # -p tcp for protocol, --dport 80 for connection type

```
## Delete a rule
```bash
iptables -L --line-number                         # Lists the table with numbers for each row
iptables -D INPUT 1                               # Will -D delete from INPUT row 1
```
![image](https://github.com/Keeriiim/CCNA/assets/117115289/9daea2a9-869f-4580-a266-89b989d0f26e)  






