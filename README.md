# DNS-Protocol-Failure

## Objective

Multiple reports came in claiming the client's website is having trouble. Pulling up the website reads the message "Destination Port Unreachable". As the analyst on the case I have loaded the tcpdump tool as the packet sniffer to analyze the live traffic when I pulled up the client website to analyze the site at network layer.

## Tools Used

The tool used was tcpdump to show the ICMP packet in detail

## Steps

This the output of the tcpdump packet sniffer reporting the problem of the server. The problem I noticed immediately was the ending line "udp port 53 unreachable" which is the DNS having a problem in getting the Servers IP address.

<img width="902" height="448" alt="image" src="https://github.com/user-attachments/assets/3c74c0d2-31c2-4ff3-9d56-edf79bd7b1af" />

Analyzing the ICMP response shows the problem lies with the DNS due to port 53 being unreachable, looking at the query "35084" indicates a flag of the UDP message and the "A?" indicating a flag of the DNS failing protocol. 

Looking at the ICMP message I assume the failure must come from two sources. One being a misconfiguration in the server, or a Denial of Service (DoS) attack has successfully inflitrated with the server. Next steps will be seeing if the DNS server itself is down, or if the Firewall have blocked port 53 and why.

## Skills learned

- Understanding the tool tcpdump pooling up a ICMP response message
- Network Traffic Analysis
- Report documenting on a network layer event
