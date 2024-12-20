# Vulnerability Managment on Windows 10 VM using Nessus

<h2>Features</h2>

- Using and configuring Nessus Essentials
- Scanning a Windows 10 virtual machine for potential vulnerabilities
- Remediating any found critical vulnerabilites on the VM

<h2>Prerequisites</h2>

- Internet Connection
- Nessus Version 10.8.3
- VMWare Workstation
- Windows 10 Home ISO Image

<h2>Setting up the Windows 10 VM for a Credential Scan</h2>

Note: the Windows Defender Firewall is turned off on the VM for this project due to the Linux Mint system I am scanning from and the Windows VM not being on the same domain. This allows Nessus to scan for vulnrabilities without needing to join them both to the same domian.
- To setup the VM for a Nessus credential scan, I first went to Services using the search function on the taskbar, and then set Remote Registry to automatic.
- Next, I went to Registry Editor and went to Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System where I created a DWORD Value named "LocalAccountTokenFilterPolicy" and set the value to 1.
- Finally, I restarted the VM

<h2>Configuring Nessus</h2>

- I then went to Nessus and clicked New Scan > Basic Network Scan
- I then made the name of the scan "Windows 10 VM." and filled out the target section with the IP of the VM (In this example, 192.168.1.250)
![Screenshot from 2024-12-18 22-44-32](https://github.com/user-attachments/assets/06f8eaa7-d0d3-407f-8514-e68d26cbbcc9)
- After configuring the name and IP address for the scan, I clicked on the credentials tab, clicked Windows under the Host category, and filled out the username for the VM (Test User) and the password. All other settings were left as default
![Screenshot from 2024-12-18 22-44-54](https://github.com/user-attachments/assets/af805788-5a9a-43ea-8a7e-104ca7fe9f5e)
- Finally, I clicked save

<h2>Scanning the VM</h2>

- To scan the VM, I clicked the launch button and waited for vulnerabilities to be found
![Screenshot from 2024-12-18 22-52-34](https://github.com/user-attachments/assets/cc57c7bb-d8fb-4fe0-869d-2cc03e11200d)

<h2>Analyzing the Results</h2>

- To see the results, I clicked on Windows VM on Nessus in the My Scans folder. Under the host section, I can see the amount of vulnerabilities the virtual machine has. In detail, there are 13 critical vulnerabilities, 51 high vulnerabilites, 9 medium vulnerabilities, 2 low vulnerabilities, and 178 info vulnerabilities.
![Screenshot from 2024-12-19 01-25-09](https://github.com/user-attachments/assets/34f93488-4d47-4971-b4c8-aa84e42a6f77)
- In the Vulnerabilities section, I can see the vulnerabilities on the VM in detail. To fully understand a specific vulnerability, I can click on it and be given information on how it can be exploited and what I can do to remedy it.
  - For example, I can go to the medium vulnerability "IP Forwarding Enabled" and get specific information on it. The description states, "The remote host has IP forwarding enabled. An attacker can exploit this to route packets through the host and potentially bypass some firewalls / routers / NAC filtering. Unless the remote host is a router, it is recommended that you disable IP forwarding." The solution to the vulnerability is to "...set the key 'IPEnableRouter' to 0 under HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Tcpip\Parameters"
![Screenshot from 2024-12-19 01-27-26](https://github.com/user-attachments/assets/fa3d5c79-eefc-4d9f-b08c-b16206c14cfa)
![Screenshot from 2024-12-19 01-28-01](https://github.com/user-attachments/assets/16834d1f-e647-440b-b94d-b4683397ee05)

<h2>Fixing the Vulnerabilities</h2>

- Under the Remediations section, I can see what I can do to fix vulnerabilites on the VM
![Screenshot from 2024-12-19 01-34-48](https://github.com/user-attachments/assets/eafec16e-0780-4d20-b91d-ca53805a8c3b)
- The first step I will take is to update the OS to it's latest version
  - To do this, I go to Update and Security > Windows Update in settings and press "Check for Updates." Any update the system requires will automatically start after pressing this.
![Screenshot from 2024-12-19 01-38-39](https://github.com/user-attachments/assets/32cc7dd8-34af-46c6-bc78-2c41162173f5)
- After updating the VM, I will launch another scan to see if any critical vulnerabilites need fixed that wasn't remedied by the updates
- As you can see by the following screenshot, simply updating the VM has fixed all of the critical vulnerabilities
![Screenshot from 2024-12-19 02-04-02](https://github.com/user-attachments/assets/e2fac15b-5f76-4531-9578-951c95eef706)

<h2>Conclusion</h2>
This project shows my skills and aptitude in vulnerability managment. By using Nessus, I was able to scan for vulnerabilities on a Windows 10 machine. By the end of the project, I was able to remedy all critical vulnerbilities. This project has deepened my understanding of vulnerability managment.











