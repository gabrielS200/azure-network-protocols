<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1: Create 2 VMs in Azure (one linux VM, and Windows 10 VM)
- Step 2: Remote into the Windows 10 VM and download Wireshark to start viewing netwokr traffic
- Step 3: Use the command line while Wireshark is open to ping the Linux server and observe trafic
- Step 4:

<h2>Actions and Observations</h2>

<p>

![Screenshot 2023-08-08 191111](https://github.com/gabrielS200/azure-network-protocols/assets/141781540/715a2301-b42e-4edb-942c-ee2c2ff5d602)


</p>
<p>
Our first step in our project is to set up two VMs in Azure. Once those two VMs have been set up take the public IP adrress from the Windows VM and remote into the VM using remote desktop. Remeber that the username and password used while seetting up the VM will need to be used to remote in, so make sure that you keep those handy. While in the windows VM go to the wireshark website and download, then install Wireshark. Open Wireshark and filter the trafic to ICMP (Internet Control Messaging Protocol) trafic by typing icmp into the top bar. This is the protocol that ping uses. Once you have done that go back into Azure and find the private IP of the Linux VM. Copy that and then ping it cotinuously from the Windows VM using the commandline. Use the command ping \private IP adress\ -t. In the windows VM Wireshark should be showing the ICMP traffic. Now lets stop the pings by going into Azure and going into the network security group of the Linux VM. Then go into the Inbound security rules tab and add a rule that blocks ICMP traffic. The rule should tick the icmp protocol and deny the action. Now go back into the Windows VM and observe the change. Now the firewall from VM2 will block VM1 from pinging it. Now go back to Azure and allow icmp traffic and observe the change. Now in Wireshark filter by SSH. open powershell and SSH into the other VM using the command ssh (user)@ip adress. SSH traffic should now show up in Wireshark. Now in Wireshark filter by DHCP. We will observe DHCP traffic by typing ipconfig /renew in the commandline. Now we will observe DNS trafic. Filter by DNS in Wireshark then type, nslookup www.google.com, and observe that Wireshark shows the DNS traffic. Lastly we will observe RDP traffic by typing into the Wireshark box tcp.port == 3389. Now that we have done these steps we can now comfortably observe network trafic and gain some familiarity when it comes to what our computers are doing in the background while we use them and we have learned how to use features in Azure to block traffic using Network Security Groups.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
