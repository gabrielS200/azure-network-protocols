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
- Step 3: Use the command line while Wireshark is open to ping the Linux server and observe trafic using different protocols
- Step 4: Block traffic using Network Security Group settings in Azure and oberve the changes

<h2>Actions and Observations</h2>

<p>

![Screenshot 2023-08-08 191111](https://github.com/gabrielS200/azure-network-protocols/assets/141781540/715a2301-b42e-4edb-942c-ee2c2ff5d602)

</p>
<p>
Our first step in the project is to set up two VMs in Azure. Once those two VMs have been set up, take the public IP address from the Windows VM and remote into the VM using Remote Desktop. Remember that the username and password used while setting up the VM will need to be used to remote in, so make sure that you keep those handy.

While in the Windows VM, go to the Wireshark website, download, and then install Wireshark. Open Wireshark and filter the traffic to ICMP (Internet Control Message Protocol) traffic by typing "icmp" into the top bar. This is the protocol that ping uses.

Once you have done that, go back into Azure and find the private IP of the Linux VM. Copy that and then ping it continuously from the Windows VM using the command line. Use the command "ping [private IP address] -t". In the Windows VM, Wireshark should be showing the ICMP traffic.
</p>
<br />

<p>
  
![image](https://github.com/gabrielS200/azure-network-protocols/assets/141781540/e5a55f39-d508-4104-90d6-b530a32e7be3)

</p>
<p>
Now, let's stop the pings by going into Azure and accessing the network security group of the Linux VM. Then proceed to the Inbound security rules tab and add a rule that blocks ICMP traffic. The rule should select the ICMP protocol and set the action to deny. Afterward, return to the Windows VM and observe the change. With the new rule in place, the firewall on VM2 will prevent VM1 from pinging it. Next, navigate back to Azure to allow ICMP traffic and observe the change.
</p>
<br />

<p>
  
![image](https://github.com/gabrielS200/azure-network-protocols/assets/141781540/f68dc315-a493-4e68-acbb-13123fb9834e)

</p>
<p>
Now, in Wireshark, filter by SSH. Open PowerShell and SSH into the other VM using the command "ssh (user)@ip address". SSH traffic should now be visible in Wireshark. Next, filter by DHCP in Wireshark. To observe DHCP traffic, type "ipconfig /renew" in the command line. Moving on, let's observe DNS traffic. Filter by DNS in Wireshark, then type "nslookup www.google.com" and notice that Wireshark displays the DNS traffic. Lastly, we will examine RDP traffic by typing "tcp.port == 3389" in the Wireshark filter box.

Now that we have completed these steps, we can comfortably observe network traffic and gain familiarity with what our computers are doing in the background while we use them. We have also learned how to utilize features in Azure to block traffic using Network Security Groups.
<br />
