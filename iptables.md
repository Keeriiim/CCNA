




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
Firewall rules: Managing input/output of packets in relation to a server  
  Ex block all incomming SSH in port 22  
  Block HTTP connections  
