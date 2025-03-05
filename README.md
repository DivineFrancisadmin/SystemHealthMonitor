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

<h2>Actions and Observations</h2>

<p>
Create Resource Group and Virtual Machine
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To begin, I set up my virtual machine (VM) in Azure, ensuring that it runs Windows Server or Windows 10. After deploying the VM, I log in via Remote Desktop Protocol (RDP) and open PowerShell as an administrator. This ensures I have the necessary permissions to run system health monitoring commands. Additionally, I verify my execution policy by running Get-ExecutionPolicy to check if scripts are allowed to run. If needed, I temporarily allow script execution by setting the policy to RemoteSigned using Set-ExecutionPolicy RemoteSigned -Scope Process. </p>
<br />

<p>
Writing the PowerShell Script
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, I open Notepad and write a simple PowerShell script that gathers system health metrics. The script retrieves information such as CPU usage, memory utilization, disk space, and network statistics. Once I finish writing the script, I save it as SystemHealthMonitor.ps1 in an easily accessible directory, such as C:\Scripts. Before closing Notepad, I double-check that I have saved the file with the correct .ps1 extension rather than .txt.</p>
<br />

<p>
Running the PowerShell Script
<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
With my script saved, I launch PowerShell as an administrator and navigate to the directory where the script is stored using the cd command. I then verify that my script is present by running dir. Once confirmed, I execute the script using .\SystemHealthMonitor.ps1. As the script runs, I observe the output displaying real-time system health data, confirming that the system is being monitored effectively.</p>
<br />
<p>
 Reviewing and Interpreting Results
 <p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
After executing the script, I analyze the output to understand my system’s performance. I check CPU load percentages, available memory, disk space usage, and network activity. If needed, I modify the script to collect additional data or format the output for better readability. This step helps me practice analyzing system health and troubleshooting potential performance issues. I also automated this process with Task Scheduler tool.
