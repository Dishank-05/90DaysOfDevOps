## Task 1: DNS – How Names Become IPs

### What happens when we type google.com in a browser?

When we type google.com, First it check whether google.com exist or not ... it asks DNS Resolver for this google.com domain . The resolver queries DNS server to find IP address , once ip is found the browser connects to that IP using http/https

### DNS Record Types

- **A Record** – Maps domain name to IPv4 address
- **AAAA Record** – Maps domain name to IPv6 address
- **CNAME** – Alias of one domain to another
- **MX** – Mail server record for receiving emails
- **NS** – Name server record (authoritative DNS server)

## dig google.com Output

- **A Record IP:** 142.250.195.14  
- **TTL:** 128 seconds  

## Task 2: IP Addressing

An IPV4 is a 32 bit address that identifies a device on a network . It consist of 4 octets each 8 bits which ranges from 0-255

- **Public IP:** Public IP is accessbile over internet from anywhere (Example: 142.250.195.14)
- **Private IP:** Private IP is mostly accessible on private network  (Example: 172.31.7.11)

### Private IP ranges
- 10.0.0.0 – 10.255.255.255
- 172.16.0.0 – 172.31.255.255
- 192.168.0.0 – 192.168.255.255

### ip addr show command output 
- 172.31.7.11

## Task 3: CIDR & Subnetting

/24 means 24 bits are used for network portion.  
Remaining 8 bits are for hosts.

### Usable Hosts

- /24 → 256 total IPs → 254 usable hosts ( 2^32 - 2^24 -2 )= 2^8 -2 = 254
- /16 → 65,536 total IPs → 65,534 usable hosts ( 2^32 - 2^16 -2 )= 2^16 -2 = 65,534
- /28 → 16 total IPs → 14 usable hosts ( 2^32 - 2^28 -2 )= 2^4 -2 = 14

- Note : Why -2 because one of ip belongs to Network Address and other belongs to Broadcast address

### Why do we subnet?

Subnets help you to create your own private and public networks and also subnetting helps divide large networks into smaller manageable networks.
It improves security, organization, and reduces broadcast traffic.

---
### CIDR Table

| CIDR | Subnet Mask       | Total IPs | Usable Hosts |
|------|-------------------|-----------|--------------|
| /24  | 255.255.255.0     | 256       | 254          |
| /16  | 255.255.0.0       | 65536     | 65534        |
| /28  | 255.255.255.240   | 16        | 14           |

---

## Task 4: Ports – The Doors to Services

### What is a port?

A port is a logical endpoint used to identify specific services on a machine.
It allows multiple services to run on a single IP address. ( Eg Port 22 for ssh , Port 3306 for mysql)

---

### Common Ports

| Port | Service       |
|------|---------------|
| 22   | SSH           |
| 80   | HTTP          |
| 443  | HTTPS         |
| 53   | DNS           |
| 3306 | MySQL         |
| 6379 | Redis         |
| 27017| MongoDB       |

---

### ss -tulpn Output (Example)

tcp         LISTEN       0            80                                               *:3306                         *:*
tcp         LISTEN       0            128                                           [::]:22                        [::]:*


- Port 22 → SSH service
- Port 3306 → MySQL/MariaDB service

## Task 5: Putting It Together

### curl http://myapp.com:8080 — What concepts are involved?

DNS resolves myapp.com to IP.  
TCP connection is established to port 8080.  
HTTP protocol is used at application layer.

### App cannot reach database at 10.0.1.50:3306 — What to check?

Ping the server on which database is running.
Check if database service is running or not on the server
Check security group/firewall rules for port 3306.

## What I Learned (Key Takeaways)

1. DNS converts human-readable names into IP addresses using records like A and AAAA.
2. CIDR notation defines network size and determines number of usable hosts.
3. Ports allow multiple services to run on a single IP address.
