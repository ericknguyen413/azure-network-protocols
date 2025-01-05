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
- Ubuntu Server 20.04

<h2>Project Walkthrough</h2>

<p>
  
Navigate to Microsoft Azure and create a resource group: 

![image](https://github.com/user-attachments/assets/7675e6e3-e373-4a6d-8732-7eba2ab59974)
</p>
<br />

<p>

Once my resource group is created, next I'll create the first virtual machine:
  
![image](https://github.com/user-attachments/assets/5d7b59d0-71fc-4ffc-9462-5317ba919b83)
</p>
<p>

</p>
<br />

Virtual Machine has been created:

<p>
  
![image](https://github.com/user-attachments/assets/93b692f0-f76d-4f22-95d2-67b9488b0280)

</p>

Now Azure has set up a VM, an IP for the VM, a network security group, a virtual network, a disk, and a NIC (Network Interface Card):

![image](https://github.com/user-attachments/assets/66e5ee39-11a5-4541-911e-61f8ae275112)

Creating my second virtual machine:

![image](https://github.com/user-attachments/assets/3894afec-5841-4ba8-8a76-c30868811ec8)

