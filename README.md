<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Monitoring Network Traffic with Azure VMs</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 24.04

<h2>Project Walkthrough</h2>

<p>
  
Navigate to Microsoft Azure and create a resource group: 

![image](https://github.com/user-attachments/assets/7675e6e3-e373-4a6d-8732-7eba2ab59974)

Once my resource group is created, next I'll create the first virtual machine:
  
![image](https://github.com/user-attachments/assets/5d7b59d0-71fc-4ffc-9462-5317ba919b83)

Virtual Machine has been created:
  
![image](https://github.com/user-attachments/assets/93b692f0-f76d-4f22-95d2-67b9488b0280)

Now Azure has set up a VM, an IP for the VM, a network security group, a virtual network, a disk, and a NIC (Network Interface Card):

![image](https://github.com/user-attachments/assets/66e5ee39-11a5-4541-911e-61f8ae275112)

Creating my second virtual machine:

![image](https://github.com/user-attachments/assets/3894afec-5841-4ba8-8a76-c30868811ec8)

The second virtual machine completed:

![image](https://github.com/user-attachments/assets/9ba69bea-10d6-4add-bdb1-a527140aa38e)

In the "Virtual Machines" tab, I want to ensure both VMs will be on the same virtual network as the first one I made:

![image](https://github.com/user-attachments/assets/4eef2d99-9ad8-4dfe-893e-420e66dcb56a)

![image](https://github.com/user-attachments/assets/4a095a12-b9c5-46b3-8865-6694004fe6a9)

Now let's use RDP to connect to Windows Virtual Machine #1

![image](https://github.com/user-attachments/assets/5cd5841e-d815-4d7d-86e9-13b007e97844)

Once I have connected to the VM1, I will now download Wireshark onto the VM

![image](https://github.com/user-attachments/assets/51fb1b09-7caf-4f9a-ab40-9689345193d0)

Once Wireshark has downloaded and opened, I will select "Ethernet" to observe network traffic:

![image](https://github.com/user-attachments/assets/d7276878-5810-4fb9-b969-8946bf97b240)

To filter for ICMP (Internet Control Message Protocol) traffic, I type "ICMP" at the top of Wireshark. To make traffic, I will get the private IP address of VM2 and ping it from PowerShell:

![image](https://github.com/user-attachments/assets/c6677972-3982-4d24-9c01-28c174884bc6)

![image](https://github.com/user-attachments/assets/c2ea76fb-f8a0-4254-ad06-7221af0036a4)

Now, we can make some firewall configurations to deny any ICMP traffic. To do this I will enter a perpetual ping command into PowerShell:

![image](https://github.com/user-attachments/assets/2cad2db6-97a1-437d-ad14-1d263021aaed)

Next, I will go to VM2's network security group and create a new inbound security rule denying all ICMP traffic making sure to put its priorty highest, so it will take precedence before all other rules:

![image](https://github.com/user-attachments/assets/38972ac3-6df0-4a4e-b7f1-9b9ce2ea3046)

![image](https://github.com/user-attachments/assets/ccc96f6a-f912-4078-a1b5-d40129c38816)

To revert the change I can either switch the inbound rule to "Allow" instead of "Deny" or delete the rule:

![image](https://github.com/user-attachments/assets/8fa4793d-21b6-4bca-a01f-fe357c1958f1)

Now ICMP echo requests are back to getting responses:

![image](https://github.com/user-attachments/assets/da41053b-3b21-4855-b426-efb0e541d91a)

Now I will filter to only show SSH (Secure Shell) traffic by typing SSH into the bar at the top and I will SSH into VM2 using PowerShell:

![image](https://github.com/user-attachments/assets/4e4fd25e-61b4-419d-bd64-e4275e44da65)

I can type commands like pwd (print working directory) and observe the traffic:

![image](https://github.com/user-attachments/assets/45a399fd-e67d-4235-b29a-217268e247c5)

After filtering for DHCP (Dynamic Host Configuration Protocol) traffic, I attempted to get a new IP address by using the ipconfig /renew command:

![image](https://github.com/user-attachments/assets/2281878d-aac8-41c4-9fc7-5206fc809d85)

Filtering for DNS (Domain Name System) traffic, I can use nslookup to find IP addresses for domain names like "google.com" and "disney.com":

![image](https://github.com/user-attachments/assets/7292e479-792b-4220-9a3c-4c562e56533f)

Finally, I'll observe RDP (Remote Desktop Protocol) traffic by typing in "tcp.port == 3389" in the top bar. You'll notice there is traffic happening without us doing anything. This is because I used RDP to connect to this machine from my own computer and RDP shows us a constant live stream of whats happening:

![image](https://github.com/user-attachments/assets/7d0aadb8-7486-4587-914c-277975cbf559)

