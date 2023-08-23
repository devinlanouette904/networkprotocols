<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Setup resources in Microsoft Azure 
- Download Wireshark 
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic

<h2>Actions and Observations</h2>

<p>
<img width="500" alt="image" src="https://github.com/devinlanouette904/networkprotocols/assets/142081954/2ccd0b3f-55c6-4fdc-a149-fa34c68b7708">

</p>
<p>
First, to observe a few network protocols on the virtual machines, I installed and opened Wireshark on the Windows 10 VM. 
</p>
<br />

<p>
<img width="500" alt="image" src="https://github.com/devinlanouette904/networkprotocols/assets/142081954/7fc47441-07b7-417e-9c03-686f94fb7597">
  
</p>
<p>
Next, I filtered for ICMP traffic only, pinged the Ubuntu VM's private IP address within the command prompt on the Windows 10 VM, and observed the traffic.  
</p>
<br />

<p>
<img width="500" alt="image" src="https://github.com/devinlanouette904/networkprotocols/assets/142081954/e65c3d27-59a1-4387-a426-471ea0dbe8f8">

</p>
<p>
Next, I initiated a perpetual ping from the Windows 10 VM to the Ubuntu VM. After observing the traffic for a while, I opened the Network Security Group of the Ubuntu VM and disabled inbound ICMP traffic. I then observed the traffic in Wireshark again, noticing when the command line request times out, and when there is no longer any reply pings in Wireshark. 
</p>
<br />
<img width="500" alt="image" src="https://github.com/devinlanouette904/networkprotocols/assets/142081954/e9d58e24-225b-411f-9be8-31a4669cdda5">

</p>
<p>
Next, I filtered for SSH traffic only (tcp.port == 22). Then, I accessed the Ubuntu VM's command line using SSH from the Windows 10 VM. I entered various commands and observed the traffic within Wireshark.
</p>
<br />
<img width="500" alt="image" src="https://github.com/devinlanouette904/networkprotocols/assets/142081954/eb991378-389c-4573-9839-b165d518b123">

</p>
<p>
Next, I filtered for DHCP traffic only (udp.port == 67). Then, I attempted to issue the Windows 10 VM a new IP address using ipconfig /renew in the command line and observed the traffic in Wireshark.
</p>
<br />
<img width="500" alt="image" src="https://github.com/devinlanouette904/networkprotocols/assets/142081954/27b381d6-9a36-4e31-8617-bf025ed78804">

</p>
<p>
Next, I filtered for DNS traffic only (udp.port == 53). Then, I used the command nslookup in the command line to find google.com's IP address and observed the traffic within Wireshark.
