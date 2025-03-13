<h1>Analyzing DNS Lookups in Wireshark Using PowerShell and Azure VMs</h1>
<h2>Objective</h2>

 - Demonstrate how to use PowerShell to perform DNS queries between Azure VMs, capture DNS request/response traffic in Wireshark, and analyze how domain name resolution works within an Azure environment.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computers)
- Remote Desktop
- Powershell
- Command-Line Tools
- Network Protocol DNS
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 Pro (22H2)
- Ubuntu Server 22.04

<h2>What is DNS (Domain Name System)?</h2>

 - DNS acts as the “phone book of the internet,” converting human-readable domain names (like google.com) into numerical IP addresses (like 142.250.191.46), which computers use to locate servers.
 - When you visit a website, your device sends a DNS query to find the corresponding IP address. The DNS server responds with the correct IP, allowing your browser to connect.
 - Port Numbers:
	 - 53 (UDP) – Used for most DNS queries (faster, no connection overhead).
	 - 53 (TCP) – Used for large responses or zone transfers (less common).
 - In Wireshark: Filtering for DNS lets you see domain name lookups. If a website isn’t loading, checking DNS traffic can help determine if name resolution is the issue.


<h2>Actions and Observations</h2>

<h3>Step 1 - Filter for DNS Traffic in Wireshark</h3>

 - [ ] Open **Wireshark** and start a new **packet capture**.
 - [ ] In the **Wireshark filter bar**, type
		
		 dns
 - This will filter out all other traffic and display only  **DNS traffic**  (**port  53**).

<h3>Step 2 - Use nslookup to Query Website IP Addresses</h3>

 - [ ] Open **PowerShell** in the **Windows 10 VM**.
 - [ ] Use the  nslookup  command to find the IP address of a website:
		 
		 nslookup google.com
	 - You will see a response showing the DNS server used and the resolved IP address for  google.com.
	 - Wireshark will display the DNS request and response exchange.

 - [ ] Run the same command for another website, such as Disney:
		
		 nslookup disney.com

	 - Again, you should see the DNS traffic in Wireshark and the resolved IP address in the command line.
 <img width="1512" alt="Step 7a- DNS" src="https://github.com/user-attachments/assets/4d8254aa-2440-4529-9e59-9f9c437e41e8" />
 
<h3>Step 3 - Observe DNS Traffic in Wireshark</h3>

 - In Wireshark, you should see the following DNS packet sequence:
	 - **Query**  – Your VM sends a DNS query to the configured DNS server, asking for the IP address of the website.
	 - **Response**  – The DNS server replies with the resolved IP address.
 - Wireshark will display details such as:
	 - The  **source IP**  (your VM’s IP address).
	 - The  **destination IP**  (the DNS server’s IP address).
	 - The  **type of query**  (e.g., A record for IPv4).
	 - The  **response**  (the website’s IP address).

<h2>Summary & Significance</h2>
<h3>What You Did:</h3>

 - [ ] Used  **Wireshark**  to capture and filter DNS traffic.
 - [ ] Used  **nslookup**  to query the IP addresses of two public websites.
 - [ ] Observed the DNS request and response cycle in Wireshark.

<h3>Why This Matters:</h3

 - **DNS is critical for internet connectivity**  – without DNS, you would have to remember IP addresses instead of domain names.
 - **Wireshark allows you to confirm DNS activity**  – if a website isn’t loading, analyzing DNS traffic helps determine whether the issue is DNS-related or network-related.
 - **Understanding DNS resolution**  helps with diagnosing issues like:
	 - Slow DNS lookups
	 - Incorrect DNS server configuration
	 - DNS poisoning or spoofing attacks
 - **Testing with nslookup**  is a quick way to verify that DNS resolution is working properly
 
 - By completing this tutorial, you’ve gained practical experience with  **capturing DNS traffic**,  **understanding how DNS works**, and  **analyzing the resolution process**  in a real-world environment.




