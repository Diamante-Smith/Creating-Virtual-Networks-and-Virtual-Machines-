# Creating-Virtual-Networks-and-Virtual-Machines


This tutorial provides a comprehensive guide starting with the creation of resource groups for virtual machines, which will be utilized throughout the lab. We’ll then explore remote desktop access specifically from a macOS perspective. Finally, we’ll dive into performing various network-related tasks using the virtual machines, giving you hands-on experience in managing and configuring network activities.

<h2>Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (22H2)
- MacOS 

<h2>Creating Our Resources & Virtual Machines </h2> 
<br>

<h3>&#9312; Create The Resource Group</h3>

  <img width="386" alt="1" src="https://github.com/user-attachments/assets/59fd6633-f347-40e5-aeb2-0b1b92fd5acc">
  <br>
  
- Go to https://portal.azure.com/#home to get started
  
- Once your there click on/ search Resource Groups and afterward click on create
  
- For me I named mine RG-LAB-02 as this was my second lab and for the region since i'm located in the Eastcoast East US 2 worked out for me and the other labs
  <br><br>

<h3>&#9313; Create The Virtual Machine With The Virtual Network</h3>


- Here is the created resource group
  
<img width="1183" alt="2" src="https://github.com/user-attachments/assets/1ab43f3c-0c42-4dee-abcc-f9c058182d35">
 <br><br>

<img width="696" alt="3" src="https://github.com/user-attachments/assets/b4123cb6-7c80-48eb-9b97-4bbca3f431f6">
<br>

- Search for Virtual Machines and hit create 

- Select your resource group, for the virtual machine name I just made it VM1
  
- Selected my region, for availability options set that to "No infrastructure redundancy required", Security type standard, and finally image Windows 10 Pro, version 22H2 x64 Gen2
  
- Make sure for the size you choose at least 2 vcpus so that way it is not going to run slow in Azure
<br><br>
<img width="1327" alt="Screenshot 2024-07-03 at 5 19 18 PM" src="https://github.com/user-attachments/assets/aefafcab-5794-46d7-b4ae-5fa96c7ad878">
<br>
<br>

- When it comes to the networking tab set this exactly like how I got it here in the screenshot
  
<br><br>
<img width="715" alt="4" src="https://github.com/user-attachments/assets/e7ed4775-824d-432e-b2a9-484dea9e8772">

- For the second Virtual Machine it will be roughly the same process as the first but what changes for this one is the name which is VM2 and the image of this VM which is Ubuntu Server 24.04 LTS - x64 Gen 2, this will be the Linux virtual machine
  
- Make sure to hit password for Authentication type and set a username and password that you will remember, try to write it down
  
<br><br>
<img width="1463" alt="Screenshot 2024-07-03 at 5 22 18 PM" src="https://github.com/user-attachments/assets/5c5d9dd3-078f-4c3e-bcad-cb041535cda2">

- Here are the 2 VMs that we will be using 

<br><br>
<img width="1354" alt="Screenshot 2024-07-04 at 10 24 18 AM" src="https://github.com/user-attachments/assets/2500969d-7cbe-4c94-922c-50ffc8afd371">

- This is an overview of what everything looks like in the resource group with the 2 virtual machines plus their respective Network Security Groups, Virtual Networks, Disks, and Public IP Addresses 

<h2>Using Remote Desktop With MacOS</h2>

<br>

- First, make sure both VMs are on the same virtual network
  
- If they are then your ready for the next step if not make sure to wait for VM1 to finish and set up creating its virtual network before you start creating VM2
<br>
<img width="429" alt="5 (A)" src="https://github.com/user-attachments/assets/aaf609fe-9ffe-481c-b1b0-9a4ae31e8e71">
<br>

<img width="509" alt="11 (A)" src="https://github.com/user-attachments/assets/0776060c-b0ab-4157-97bf-06a71e51233e"> <br>

<br><br>

<h3>&#9314; Download Microsoft Remote Desktop </h3>
<br>
<img width="287" alt="Screenshot 2024-09-19 at 12 28 36 PM" src="https://github.com/user-attachments/assets/fc0b9142-ae88-4315-9a78-b2649a841455">

- First, go to the App Store on Mac and download this app. We are going to use remote desktop to connect to our Windows 10 virtual machine
<img width="470" alt="5" src="https://github.com/user-attachments/assets/fb9e38e9-3347-410a-ab8c-680c626ababe">

- We are going to need to get the Windows 10 virtual IP address

- Scroll to the right and copy the public IP address
  
- Under the PC name put the public IP address, friendly name anything you want, or Windows VM to differentiate, then click add
  
- Remember your username and password from before, put that in when clicking to connect to the virtual machine

  
<br><br>

<img width="1680" alt="6" src="https://github.com/user-attachments/assets/1877ce8d-8a4a-49a0-b483-ca827787f8b0">

<br>

<br>

- Here is the Virtual Machine which is Windows 10
  
<br><br>

<h2>Performing Activities on the Network</h2>
<br>

<h3>&#9315; Download Wireshark </h3>
<img width="694" alt="7" src="https://github.com/user-attachments/assets/85c62eb3-f601-4c3a-b230-b5da00ea9152"> 

- We are going to download Wireshark on this virtual machine, here is the link https://www.wireshark.org

- When it is done downloading open the file and go through the procedure for installing the software which we will mostly say yes and agree

- Wireshark is a protocol analyzer which lets us do traffic examination and observe traffic between the 2 virtual machines. Let’s us view traffic that's coming from and going to the Windows virtual machine  

<br><br>

<img width="1149" alt="8" src="https://github.com/user-attachments/assets/56c55bbb-48a4-4ab5-b554-5b4e3c7af88d">

- Once this is opened click on Ethernet and then the blue sharkfin button at the top left under File

<br><br>

- This will show up after you do that, to increase the size to look better at the data hold control while pressing ➕
  
- This is all the network traffic that is happening on the back end of the computer
   
<img width="1152" alt="9" src="https://github.com/user-attachments/assets/1d0a32c8-98b3-4b39-a8c1-9491fbefa172">


<br><br>
<h3>&#9316; Filter for ICMP Traffic </h3>

- The next thing we will do is filter for ICMP traffic, first type ICMP in the search bar this will show only ICMP or ping traffic

- This traffic is what ping uses, the ping command is what we use to test connectivity between 2 devices
<img width="615" alt="10" src="https://github.com/user-attachments/assets/c8758d7b-da2b-4943-9f82-680ac53e42d0">



<br><br>

- My private IP address for Linux right now is 10.0.0.5
  
<img width="509" alt="11 (A)" src="https://github.com/user-attachments/assets/0776060c-b0ab-4157-97bf-06a71e51233e">

<h3>&#9317; Launch Windows Powershell </h3>

<img width="1156" alt="11" src="https://github.com/user-attachments/assets/316ed6a1-c837-47a2-8e0d-4f158a79575a">


- Launch Windows Powershell

- Type ping in the Windows Powershell application, then type the private IP address of the Linux Virtual Machine next to ping as you see in the picture mine is 10.0.0.5

- We will attempt to ping this IP address from the Windows Virtual Machine

- The feedback we will get from The Linux VM is reply, reply, reply, reply, and in the pink will be a bunch of traffic

- Once you type in ICMP that should stop all the other spam and let you see the pings that happened

<br><br>

<img width="1026" alt="12" src="https://github.com/user-attachments/assets/c94862ab-57f5-4ac4-b78e-d88357b26127">

- Press the green shark fin under Edit in Wireshark called "Restart Current Capture" then press continue without saving to clear what’s in pink

- Redo ping again in Powershell, you may see just 4 events happen in there for example reply, reply, reply but in Wireshark, you see a couple of events happen because it captured both the request from the Windows computer A.K.A source 10.0.0.4 and captured the reply from the Destination A.K.A 10.0.0.5 Linux computer with a request from the Windows computer and reply from the Linux Computer back and forth 


<br><br>

<img width="726" alt="Screenshot 2024-09-24 at 2 29 35 PM" src="https://github.com/user-attachments/assets/460a904c-76ce-4401-8c99-13b38bfe287f">

- On the left side beneath the data in pink click on the grey Ethernet II tab down arrow and what you see highlighted starting with Source: refers to the Physical address in Powershell
  
- In Windows Powershell type ipconfig /all and hit enter
  
- The Physical Address highlighted is also the Source for the MAC address of the Windows VM and the data above is the Linux computer destination MAC address that we pinged
  
<br><br>

- When you expand the Internet Control Message Protocol (ICMP) representative of the network layer you can see data the actual payload the data that was sent in the ping

  
<img width="764" alt="Screenshot 2024-09-28 at 5 09 00 PM" src="https://github.com/user-attachments/assets/fced515f-f86f-4581-9363-a1a3c4ca64d4">

- The Windows virtual machine source address 10.0.0.4 is the private IP address that would be the IPv4 highlighted in the Windows Power shell 

<br><br>
<img width="1036" alt="13" src="https://github.com/user-attachments/assets/363639c4-1b52-4f03-8a8f-69bd4383c586">

- What you see here is the ICMP Echo request so it is from the Windows computer and under that is the reply from the Linux computer

- The data in here will essentially be reversed the source and destination possibly being flipped and the IP address source becomes the Linux computer and the destination becomes the Windows computer and this keeps going on throughout all the pings

- Next, we will do a perpetual Ping put in Windows Powershell Ping the IP address of the Linux computer 10.0.0.5 and then -t this will make the data ping forever while Wireshark captures them as well in the background

<br><br>
<h3>&#9316; Block all incoming ping traffic </h3>

<img width="800" alt="14" src="https://github.com/user-attachments/assets/e567af13-3c65-4805-b9e9-e84d0804d353">

In this step, we are going to block all incoming ping traffic and then observe what happens afterward 

- Go ahead and jump straight into your Linux virtual machine, hit the networking down arrow, then hit network settings 
<br><br>

<img width="1447" alt="15" src="https://github.com/user-attachments/assets/37751a88-ec8f-435a-9b91-e42ad8b128bc"><br><br>

<img width="352" alt="16" src="https://github.com/user-attachments/assets/2bae8d71-f9bf-4403-9d87-6ef495cd50dc"><br><br>

<img width="347" alt="17" src="https://github.com/user-attachments/assets/82a8711e-942f-4858-83f5-a593b031aa6e"><br><br>

<img width="1119" alt="18" src="https://github.com/user-attachments/assets/cdf4f238-08e0-4a55-8ed5-681f3f56867c"><br><br>

<img width="423" alt="19" src="https://github.com/user-attachments/assets/f5542cd3-bc37-455b-b24f-eeaa448e248e"><br><br>

<img width="782" alt="20" src="https://github.com/user-attachments/assets/7850a198-f879-4b1a-9b12-a6b9683439d0"><br><br>

<img width="727" alt="21" src="https://github.com/user-attachments/assets/d94641cb-aea4-45b0-81d7-bf4afb35c8da"><br><br>

<img width="1060" alt="22" src="https://github.com/user-attachments/assets/4c1357e8-9119-4725-865e-f082e03ca728"><br><br>

<img width="639" alt="23" src="https://github.com/user-attachments/assets/abef1814-17fd-4e1b-9f5e-c637cc6ed52a"><br><br>

<img width="607" alt="24" src="https://github.com/user-attachments/assets/41e6663f-0a91-4104-92f4-737a257abb67"><br><br>

<img width="454" alt="25" src="https://github.com/user-attachments/assets/07c8687e-878b-4036-84a6-ddeadaccd877"><br><br>

<img width="236" alt="26" src="https://github.com/user-attachments/assets/c38cb7e6-761a-40fd-a25b-9ba52c6b0bf0"><br><br>

<img width="637" alt="27" src="https://github.com/user-attachments/assets/f7c1fd87-1b5b-4ea1-8606-b58b9fd3eb4f"><br><br>

<img width="1114" alt="28" src="https://github.com/user-attachments/assets/9dda896b-60a9-4bcb-8d56-b88ae75335d9"><br><br>

<img width="665" alt="29" src="https://github.com/user-attachments/assets/39e9fcdf-a542-4270-80bf-18efeaa82299"><br><br>

<img width="934" alt="30" src="https://github.com/user-attachments/assets/bb7359ca-ae43-4fbf-8594-47413b23cb72"><br><br>


<img width="1120" alt="31" src="https://github.com/user-attachments/assets/08659088-37f5-4340-a534-b810ef861dd2"><br><br>

<img width="1143" alt="32" src="https://github.com/user-attachments/assets/16281162-e100-407f-8ff9-2d1d4ede39e3"><br><br>

<img width="600" alt="33" src="https://github.com/user-attachments/assets/0a348b78-6e73-4f50-b24e-b0e17dd1b30b"><br><br>

<img width="1149" alt="34" src="https://github.com/user-attachments/assets/f8452888-503c-4793-8ef9-cb49428530c2"><br><br>

<img width="599" alt="35" src="https://github.com/user-attachments/assets/7d7c7176-6bc4-46e3-8901-64485e385795"><br><br>



























