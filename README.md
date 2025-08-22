# azure-network-protocols
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1 align="left">Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>

In this tutorial, we capture and analyze network traffic between Azure Virtual Machines using Wireshark, focusing on key protocols such as ICMP, SSH, DHCP, DNS, and RDP. We also configure and test Network Security Groups (NSGs) to manage inbound and outbound traffic. Through this process, we gain a better understanding of how data flows between virtual machines and how security rules can be applied to allow or block specific types of communication.</p>


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Network Protocols
- Wireshark 

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04



<h2> Observing ICMP Traffic</h2>
<ol>
  <li>Connect to the Windows 10 VM using Remote Desktop.</li>
  <li>Install Wireshark within the Windows 10 VM.</li>
  <li>Open Wireshark and apply a filter to capture only ICMP traffic (used for ping commands).</li>

  <img width="975" height="337" alt="image" src="https://github.com/user-attachments/assets/e4ac7ea8-2ab7-4daf-842c-a85e6562a4c1" />

   <li>Retrieve the private IP address of the Ubuntu VM and attempt to ping it from the Windows 10 VM.</li>
  <ul>
    <li>Observe the ping requests and replies in Wireshark.</li>
    
  <img width="975" height="475" alt="image" src="https://github.com/user-attachments/assets/686e326c-79ea-43e1-8c95-b03ab86fa962" />
   </ul>
  <li>From the Windows 10 VM, open Command Prompt or PowerShell and ping a public website (such as <code>www.google.com</code>).</li>
  <ul>
    <li>Observe the public ping traffic in Wireshark.</li>
  </ul><img width="975" height="472" alt="image" src="https://github.com/user-attachments/assets/0c3c769b-7044-45b6-9e88-1ec28fc86092" />
   <li>Initiate a continuous ping from the Windows 10 VM to the Ubuntu VM.</li>
  <li>In the Azure portal, access the Network Security Group (NSG) assigned to the Ubuntu VM and disable inbound ICMP traffic.</li>
  <img width="1150" height="815" alt="image" src="https://github.com/user-attachments/assets/aa23a4fc-d22e-4d9e-98b0-9013acef12c8" />
  <h2>Creating a Deny ICMP Rule</h2>

Step 3 -A custom inbound rule was created to block ICMP traffic. The rule uses protocol-specific filtering and a high priority to override default allow rules.
<p>
  
![Screenshot 2025-06-19 161848](https://github.com/user-attachments/assets/ae4ffec0-f553-44fc-990f-b8832affca88)


</p>
<br />
<h2> Ping Test</h2>
Step 4 - A ping test was performed after applying a custom Deny-ICMP rule in the Network Security Group. The request was blocked, confirming that the security rule is working as intended.

<p> <img width="1887" height="936" alt="image" src="https://github.com/user-attachments/assets/b06d624b-d883-4318-b82b-d0cb85a824f9" />



