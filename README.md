<h1>System Health Monitoring with PowerShell</h1>
<h2>Description</h2>

System Health Monitoring with PowerShell is a project designed to help IT professionals monitor system performance using simple PowerShell commands. The script in this project retrieves and displays real-time information on CPU usage, memory utilization, disk space, and network activity, allowing administrators to assess system health automatically. This project is useful for IT help desk roles, system administrators, and those learning PowerShell for system management.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (for Virtual Machine deployment)
- Windows 10 (22H2)
- PowerShell
- Remote Desktop Protocol (RDP)
- System administration tools (Task Scheduler)

<h2>Langue Used </h2>

- PowerShell

<h2>High-Level Steps</h2>

- Create Resource Group and Virtual Machine
- Writing the PowerShell Script
- Running the PowerShell Script
- Reviewing and Interpreting Results

<h2>Script walk-through</h2>

<p>
Create Virtual Machines and Network Setup
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To begin the lab, I first create a Resource Group in the Azure Portal to organize all related resources. Next, I deploy a Windows 10 Virtual Machine (VM), ensuring that it creates a new Virtual Network (VNet) and Subnet for communication. Once the Windows VM is set up, I proceed to create a Linux (Ubuntu) VM, making sure that it is in the same Resource Group and Virtual Network as the Windows VM. This setup ensures both machines can communicate internally without requiring external internet access.</p>
<br />

<p>
Monitor Network Traffic with Wireshark
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once my virtual machines are running, I use Remote Desktop to connect to the Windows 10 VM. The first step is to install Wireshark, a network protocol analyzer, which will allow me to inspect network traffic in real time. After installation, I start a packet capture in Wireshark and filter for ICMP traffic. To generate ICMP traffic, I retrieve the private IP address of the Ubuntu VM and attempt to ping it from the Windows 10 VM. I observe the ping requests and replies appearing in Wireshark. Additionally, I open PowerShell or Command Prompt and attempt to ping a public website (e.g., www.google.com) to analyze outbound ICMP traffic.</p>
<br />

<p>
Configure and Test Firewall Rules (NSG)
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
With network traffic monitoring in place, I test how firewall rules impact communication. I initiate a continuous ping from the Windows 10 VM to the Ubuntu VM. Then, I navigate to the Azure Portal, locate the Network Security Group (NSG) assigned to the Ubuntu VM, and disable inbound ICMP traffic by creating a rule that blocks it. Returning to Wireshark and the command line, I observe that the ping requests stop receiving replies, indicating the firewall rule is working as expected. To restore connectivity, I re-enable ICMP traffic in the NSG and confirm that the pings resume successfully.</p>
<br />
<p>
Analyze Different Network Protocols in Wireshark
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, I use Wireshark to analyze different network protocols. I filter for SSH traffic and initiate an SSH session from the Windows VM to the Ubuntu VM using its private IP address (ssh labuser@<private IP>). As I enter commands in the Linux terminal, I observe SSH packets being captured. Then, I filter for DHCP traffic and renew my Windows 10 VM's IP address by running ipconfig /renew in PowerShell. Wireshark captures the DHCP request and response, showing how the VM acquires a new IP. Similarly, I analyze DNS traffic by using the nslookup command to find the IP addresses of google.com and disney.com, observing DNS query and response packets. Finally, I filter for RDP traffic (port 3389) and notice constant packet activity, confirming that Remote Desktop continuously transmits data to provide a live session.
