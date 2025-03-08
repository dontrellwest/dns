<h1>Analyzing DNS Lookups in Wireshark Using PowerShell and Azure VMs</h1>
Objective: Demonstrate how to use PowerShell to perform DNS queries between Azure VMs, capture DNS request/response traffic in Wireshark, and analyze how domain name resolution works within an Azure environment.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Powershell
- Various Command-Line Tools
- Network Protocol ICMP
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 Pro (22H2)
- Ubuntu Server 22.04


<h2>Actions and Observations</h2>

<br>

<h3>Step 1 - DNS (Domain Name System)</h3>
•	DNS acts as the “phone book of the internet,” converting human-readable domain names (like google.com) into numerical IP addresses (like 142.250.191.46), which computers use to locate servers.
<br>
•	When you visit a website, your device sends a DNS query to find the corresponding IP address. The DNS server responds with the correct IP, allowing your browser to connect.
<br>
•	Port Numbers:<br>
•	53 (UDP) – Used for most DNS queries (faster, no connection overhead).<br>
•	53 (TCP) – Used for large responses or zone transfers (less common).<br>
<br>
<br>
•	In Wireshark: Filtering for dns lets you see domain name lookups. If a website isn’t loading, checking DNS traffic can help determine if name resolution is the issue.
<br>
<img width="1512" alt="Step 7a- DNS" src="https://github.com/user-attachments/assets/608e00dd-723c-498a-b442-78d02f923c3b" />
