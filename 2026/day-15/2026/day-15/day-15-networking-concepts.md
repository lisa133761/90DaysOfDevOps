## Task 1: DNS – How Names Become IPs
When you type google.com in a browser, the system first queries the DNS server to translate the domain name into an IP address.
The DNS resolver checks its cache or queries DNS servers until it finds the IP for the domain.
Once the IP address is returned, the browser connects to that server using the IP.
The web server then responds and the website loads in the browser.

**DNS Record Types**

* A Record – Maps a domain name to an IPv4 address.
* AAAA Record – Maps a domain name to an IPv6 address.
* CNAME Record – Points one domain name to another domain name (alias).
* MX Record – Specifies the mail server responsible for receiving email for the domain.
* NS Record – Identifies the authoritative DNS servers for the domain.

  **dig google.com**

; <<>> DiG 9.18.39-0ubuntu0.24.04.2-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45436
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             2       IN      A       216.58.207.238

;; Query time: 1 msec
;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
;; WHEN: Thu Mar 05 03:16:25 UTC 2026
;; MSG SIZE  rcvd: 55

 ## Task 2: IP Addressing
 
 **What is an IPv4 Address?**

  * An IPv4 address is a 32-bit numeric address used to identify devices on a network.
  * It is written in four decimal numbers separated by dots (e.g., 192.168.1.10).
  * Each number ranges from 0 to 255.
    
**Public vs Private IP**

1. Public IP
 - Accessible over the internet
 - Assigned by an ISP

2. Private IP
 - Used inside local networks
 - Not directly reachable from the internet
   
**Private IP Ranges**
  10.0.0.0 – 10.255.255.255
  172.16.0.0 – 172.31.255.255
  192.168.0.0 – 192.168.255.255
  
**ip addr show**
  output : inet 172.17.0.1/16

  ## Task 3: CIDR & Subnetting
  
  1. What does /24 mean?
     /24 means the first 24 bits represent the network portion of the address, and the remaining 8 bits are used for host addresses.
   
  2. Usable Hosts

     * /24
      Total IPs: 256
      Usable Hosts: 254
      
     * /16
      Total IPs: 65,536
      Usable Hosts: 65,534
      
     * /28
      Total IPs: 16
      Usable Hosts: 14

 3. Why Do We Subnet?

   - Subnetting helps divide large networks into smaller manageable networks.
   - It improves security, organization, and efficient IP address usage.
   - It also reduces network congestion and broadcast traffic.
     
  4. CIDR Table
        CIDR	    Subnet Mask   	  Total IPs      	Usable Hosts
        /24 	   255.255.255.0	      256	           254
        /16	       255.255.0.0	      65,536	       65,534
        /28	     255.255.255.240	     16	             14

## Task 4: Ports – The Doors to Services
1. What is a Port?
   A port is a communication endpoint used by applications to send and receive data over a network.
   Ports allow multiple services to run on the same machine using different port numbers.

2. Common Ports
      Port	    Service
       22	        SSH
       80	        HTTP
       443      	HTTPS
       53	        DNS
       3306     	MySQL
       6379	      Redis
       27017     	MongoDB
 3. ss -tulpn
    output :
    Netid     State       Recv-Q      Send-Q                Local Address:Port            Peer Address:Port     Process
    udp       UNCONN      0           0                         127.0.0.1:323                  0.0.0.0:*
    udp       UNCONN      0           0                        127.0.0.54:53                   0.0.0.0:*
    udp       UNCONN      0           0                     127.0.0.53%lo:53                   0.0.0.0:*
    udp       UNCONN      0           0                172.31.24.177%ens5:68                   0.0.0.0:*
    udp       UNCONN      0           0                             [::1]:323                     [::]:*
    tcp       LISTEN      0           4096                  127.0.0.53%lo:53                   0.0.0.0:*
    tcp       LISTEN      0           4096                     127.0.0.54:53                   0.0.0.0:*
    tcp       LISTEN      0           511                         0.0.0.0:80                   0.0.0.0:*
    tcp       LISTEN      0           4096                        0.0.0.0:22                   0.0.0.0:*
    tcp       LISTEN      0           4096                      127.0.0.1:44085                0.0.0.0:*
    tcp       LISTEN      0           511                            [::]:80                      [::]:*
    tcp       LISTEN      0           4096                           [::]:22                      [::]:*

## Task 5: Putting It Together
1. curl http://myapp.com:8080
What Happens?
    First, DNS resolves the domain name (myapp.com) to an IP address.
    Then the client connects to the server using HTTP on port 8080.
    Networking concepts involved include DNS resolution, IP addressing, and ports.

2. App Can't Reach Database at 10.0.1.50:3306 – What to Check?

    First check if the database server is reachable (ping or network connectivity).
    Also check firewall rules or security groups blocking the connection.

## What I Learned

   - DNS translates domain names into IP addresses so computers can communicate.
            
   - CIDR notation helps organize IP ranges and subnet networks efficiently.
            
   - Ports allow multiple services (like SSH, HTTP, MySQL) to run on the same machine.
                        
