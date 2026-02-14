# Day 14 – Networking Fundamentals & Hands-on Checks

## Quick Concepts

- OSI vs TCP/IP Model
 - OSI model is a 7 layer model which is a theoretical framework used for teaching purpose and TCP/IP Model is actually 4 layer model that internet actually runs on.

 Layer 1: Physical Layer :- Actual hardware like cables andn wifi etc
 Layer 2: Data Link Layer :- Handles communication between two devices on same network It uses MAC addresses.
 Layer 3: Network Layer :- Handles routing between different networks.This is where IP Addresses live.
 Layer 4: Transport Layer :- Manages rules of connection protocols (Eg: TCP or UDP)
 Layer 5: Session Layer :- It maintains session with particular endpoint 
 Layer 6: Presentation Layer :- Data formation and encoding takes place over here.
 Layer 7: Application Layer :- Application layer where actual application resides ( DNS,HTTP/HTTPS)

 - TCP/IP Model is also the same, It's just combines OSI Layers into four functional group
    1. Network Layer : Combination of Layer 1 and Layer 2 of OSI
    2. Internet Layer : Equivalent to Layer 3 of OSI
    3. Transport Layer : Equivalent to Layer 4 of OSI 
    4. Application Layer : Combination of 5,6,&7 of OSI

## Networking Commands

- hostname -I : Shows the IP address of your machine (private IP in EC2)
- ping google.com : Sends ICMP packets to check if a host is reachable/alive and measure latency
- traceroute google.com : Shows the path (hops) taken by packets from your machine to the target host
- ss -tulpn : Lists all listening ports with their protocols, states, and owning process
- curl -I https://google.com : Sends a HEAD request to a URL to check HTTP status and headers
- nslookup google.com : Resolves a domain name to its IP using DNS server
- netstat -an | head : Shows active network connections, listening ports, and their states
- nc -zv localhost 22 : Checks if 22 port is on a host is reachable or not 

## Mini Task: Port Probe & Interpret

-  ss -tulpn : Checks listening ports and nc -zv localhost 22 checks port connectivity and reachability.... if it's not then check whether sshd service is active or not if its active then check whether firewall is blocking these port

## Notes

- ping command will give you the fastest signal to check if something is broken like if there is a need to check whether remote server is alive or not 
- If there is a issue with DNS or DNS fails and 500 status code shows up then application layer should be inspected because dns queries takes place over here.
- Two followups to check in incident ping command to check if server is responding or not and nc -zv <host> <port> to check service is listening and reachable
