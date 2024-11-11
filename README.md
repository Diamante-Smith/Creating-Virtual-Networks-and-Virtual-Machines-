
![6320f4525eab744205bc21b6_Microsoft-Azure-Logo](https://github.com/user-attachments/assets/9cd1e085-8a21-48c1-bab9-07e21fd18ded)

<h1> Creating Virtual Networks and Virtual Machines </h1>


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

<img width="625" alt="Screenshot 2024-10-27 at 3 05 26 PM" src="https://github.com/user-attachments/assets/d26c907f-1e8c-4a5d-bea9-7c255eb8bd0b">

  
- Make sure for the size you choose at least 2 vcpus so that way it is not going to run slow in Azure

- Compose a password and username that are both easily remembered and secure, and then record them down for safekeeping.
  
<br><br>
<img width="1327" alt="Screenshot 2024-07-03 at 5 19 18 PM" src="https://github.com/user-attachments/assets/aefafcab-5794-46d7-b4ae-5fa96c7ad878">


<br>

- Regarding the networking tab, my virtual network name was automatically assigned this name. To change the name scheme, please click on “Create New.”
  
<br>
  <img width="678" alt="Screenshot 2024-10-27 at 4 05 38 PM" src="https://github.com/user-attachments/assets/f5f5191b-ded8-4f50-a585-9e12873e3a41">


- I have updated the name to Lab2-Vnet. Please confirm by pressing OK, and this will be the new name for the virtual network.
  
<br><br>
<img width="715" alt="4" src="https://github.com/user-attachments/assets/e7ed4775-824d-432e-b2a9-484dea9e8772">

- The procedure for establishing the second virtual machine will closely resemble that of the first. However, there are key distinctions: this virtual machine will be designated as VM2, and it will utilize the image Ubuntu Server 24.04 LTS - x64 Gen 2. This configuration will represent our Linux virtual machine.

  <br>

  <img width="622" alt="Screenshot 2024-10-27 at 3 11 23 PM" src="https://github.com/user-attachments/assets/905af917-cc4f-4e63-ae03-9576d04e81a8">

  
- Please ensure that you select "password" as the Authentication type. Additionally, create a username and password that you will easily remember. It is advisable to document this information for future reference.
  
<br><br>
<img width="1463" alt="Screenshot 2024-07-03 at 5 22 18 PM" src="https://github.com/user-attachments/assets/5c5d9dd3-078f-4c3e-bcad-cb041535cda2">

- Here are the 2 Virtual Machines that we will be using 

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

- Go to the App Store on Mac and download this app. We are going to use remote desktop to connect to our Windows 10 virtual machine
<img width="470" alt="5" src="https://github.com/user-attachments/assets/fb9e38e9-3347-410a-ab8c-680c626ababe">

- We are going to need to get the Windows 10 virtual IP address

- Scroll to the right and copy the public IP address
  
- Under the PC name put the public IP address, friendly name anything you want, or Windows VM to differentiate, then click add
  
- Remember your username and password from before, put that in when clicking to connect to the virtual machine

  
<br><br>

<img width="783" alt="Screenshot 2024-10-27 at 3 36 21 PM" src="https://github.com/user-attachments/assets/dc85a02c-20d6-4d5d-a668-0dac622c2645">

- If you are confident that you have entered all the information accurately, yet you are still unable to establish a remote desktop connection to the virtual machine, the issue may be related to the password.

- To reset your password, please access the Azure portal. Select your Windows virtual machine, navigate to the "Help" section, and click on "Reset password." Enter your new password and then select "Update." This process should effectively resolve the issue.

<br><br>
<img width="1680" alt="6" src="https://github.com/user-attachments/assets/1877ce8d-8a4a-49a0-b483-ca827787f8b0">


<br>

- Here is the Virtual Machine which is Windows 10
  
<br><br>

<h2>Performing Activities on the Network</h2>
<br>

<h3>&#9315; Download Wireshark </h3>
<img width="694" alt="7" src="https://github.com/user-attachments/assets/85c62eb3-f601-4c3a-b230-b5da00ea9152"> 

- We are going to download Wireshark on this virtual machine, here is the link https://www.wireshark.org

- We will be downloading Windowsx64 Installer, so click this

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

<img width="1363" alt="Screenshot 2024-10-27 at 4 51 10 PM" src="https://github.com/user-attachments/assets/26c5add5-c7f5-44fe-abe4-8ccae110cf34">


- On the left side beneath the data in pink click on the grey Ethernet II tab down arrow and what you see highlighted starting with Source: refers to the Physical address in Powershell
  
- In Windows Powershell type ipconfig /all and hit enter
  
- The Physical Address highlighted is also the Source for the MAC address of the Windows VM and back to Wireshark the data above Source: is the Linux computer destination MAC address that we pinged
  
<br><br>

- When you expand the Internet Protocol A.K.A representative of the network layer of the OSI model layer 3 you can see the source address and destination address

<img width="1021" alt="Screenshot 2024-10-27 at 4 57 10 PM" src="https://github.com/user-attachments/assets/5666db96-fd42-425c-8338-2b6c38dfd401">

<br><br>

- The Windows virtual machine source address 10.0.0.4 is the private IP address that would be the IPv4 highlighted in the Windows Power shell with 10.0.0.5 in Wireshark being the Linux VM's Private IP address

  <br><br>

<img width="301" alt="Screenshot 2024-10-27 at 4 57 49 PM" src="https://github.com/user-attachments/assets/9e9222a1-5b9e-49ef-9a74-a81c8eabd693">

- When you expand the Internet Control Message Protocol (ICMP) you can see data the actual payload of the data that was sent in the ping

<br><br>

<img width="1036" alt="13" src="https://github.com/user-attachments/assets/363639c4-1b52-4f03-8a8f-69bd4383c586">

- What you see here is the ICMP Echo request so it is from the Windows computer and under that is the Echo reply from the Linux computer

- The data in here will essentially be reversed the source and destination possibly being flipped and the IP address source becomes the Linux computer and the destination becomes the Windows computer and this keeps going on throughout all the pings

- Next, we will do a perpetual Ping put in Windows Powershell Ping the IP address of the Linux computer 10.0.0.5 and then -t example (ping 10.0.0.5 -t) this will make the data ping forever while Wireshark captures them as well in the background

<br><br>
<h3>&#9318; Configuring a firewall to Block all incoming ping traffic </h3>

- In this step, we are going to block all incoming ping traffic coming from the Windows Virtual Machine to the Linux Virtual Machine and then observe what happens afterward

<img width="800" alt="14" src="https://github.com/user-attachments/assets/e567af13-3c65-4805-b9e9-e84d0804d353">

<br><br>

<img width="218" alt="Screenshot 2024-11-07 at 1 02 57 PM" src="https://github.com/user-attachments/assets/5da89e34-d908-422b-bc18-fe9b61b7be6d">
<br><br>

- Go ahead and jump straight into the Azure portal and search for Network Security Groups -> Click on your Linux VM -> Hit the Settings down arrow

<br><br>


<img width="689" alt="Screenshot 2024-11-07 at 1 09 32 PM" src="https://github.com/user-attachments/assets/12201d99-8a30-4b98-affd-23960dab78fd">

- This is the firewall for the Linux computer

- For this step hit the drop-down arrow for settings and click on inbound security rules, with this we will create a rule for traffic coming inbound to the virtual machine
  <br><br>

<img width="599" alt="Screenshot 2024-10-11 at 2 51 18 PM" src="https://github.com/user-attachments/assets/8a519d7d-4d5e-4ef1-a0bb-c9a7fdc39275">

<br><br>

- Click on Add to begin the process of creating a rule
<br><br>

<img width="466" alt="Screenshot 2024-11-07 at 1 24 16 PM" src="https://github.com/user-attachments/assets/aa7c1b27-e80a-44db-99bf-606efc543f8d">


- What I have displayed is what you should put in

- There is an asterisk (which is referred to as any) placed in the destination port since ICMP doesn’t use a port

- Deny is selected to prevent ICMP from being pinged so the firewall will drop the traffic

- Priority is set to 290 because it would allow the rule to be evaluated first

- Then hit add

<br>

<img width="347" alt="17" src="https://github.com/user-attachments/assets/82a8711e-942f-4858-83f5-a593b031aa6e">


- As you can see once the rule takes effect in Powershell everything will start to time out because the Linux virtual machine will begin to ignore the traffic and not reply to it

- The rule we made denies incoming ICMP traffic from any source to any destination for the Linux virtual machine 

<br><br>

<img width="1119" alt="18" src="https://github.com/user-attachments/assets/cdf4f238-08e0-4a55-8ed5-681f3f56867c">

- In Wireshark what also changed is that instead of getting a steady request/ reply response it changed to just request because no response was found and the firewall is blocking the replies

- P.S. This can go on forever
  
<br><br>

<img width="457" alt="Screenshot 2024-11-07 at 1 34 38 PM" src="https://github.com/user-attachments/assets/a7f03bce-cf05-40ff-8a6f-80d9f8840225">


<br><br>

<img width="1439" alt="Screenshot 2024-11-07 at 1 30 48 PM" src="https://github.com/user-attachments/assets/b679a612-f828-4f14-8259-321edcd91f9f">

<img width="1437" alt="Screenshot 2024-11-07 at 1 35 02 PM" src="https://github.com/user-attachments/assets/0b8f1d94-f108-4e44-9078-b94efcdb7ee6">

<br><br>

- For this, we will be turning back on the Allow action for ICMP so that it can get a reply, to do that go back to Virtual Machines -> linux-vm -> Networking -> Network settings -> click on the highlighted Network security group -> Inbound security rules -> you can choose to delete or edit the rule
  
<br><br>

<img width="782" alt="20" src="https://github.com/user-attachments/assets/7850a198-f879-4b1a-9b12-a6b9683439d0">


<br>

<img width="727" alt="21" src="https://github.com/user-attachments/assets/d94641cb-aea4-45b0-81d7-bf4afb35c8da">

- Once the Azure resource manager picks up the requests then everything will flow back to normal like before we made that Deny (firewall) rule

- Stop the ping activity with Control + C before moving on to the next step

<br><br>

<h3>&#9319; Observe SSH traffic </h3>

<img width="1060" alt="22" src="https://github.com/user-attachments/assets/4c1357e8-9119-4725-865e-f082e03ca728">

- SSH (Secure Shell) is used to make a secure connection from 1 computer to another computer, it uses TCP port 22

- In Wireshark, we are going to type in SSH to filter for that traffic

- Go to your Linux VM and copy the private IP address located in Overview -> Properties 

- go back to your Windows VM and Open Windows Powershell, type in ssh labuser@10.0.0.5, and press enter to connect to the Linux VM with SSH, confirm a yes again to continue connecting

- Finally enter the password you made for labuser
  
<br><br>

<img width="639" alt="23" src="https://github.com/user-attachments/assets/abef1814-17fd-4e1b-9f5e-c637cc6ed52a">


- The prompt looks different now because we are connected to the Linux machine


<br><br>

<img width="607" alt="24" src="https://github.com/user-attachments/assets/41e6663f-0a91-4104-92f4-737a257abb67">

- Type id this is our user id labuser

- Type hostname mine is Linux VM2

- Type uname -a this will give out stuff about the operating system

- Type pwd shows the labuser file path

- Type touch file.txt this creates a file on the Linux machine

- Type ls shows that the file was created

<br><br>

<img width="1114" alt="28" src="https://github.com/user-attachments/assets/9dda896b-60a9-4bcb-8d56-b88ae75335d9">

- Instead of SSH In Wireshark type in tcp.port==22 this will filter out all of the traffic that uses TCP port 22 
  
- Type in PowerShell ls and press enter because SSH uses TCP port 22 we can see in Wireshark it is being filtered out 
<br><br>

<img width="236" alt="26" src="https://github.com/user-attachments/assets/c38cb7e6-761a-40fd-a25b-9ba52c6b0bf0">

- Type in Powershell exit this will drop the connection and log us out
  
- Type in hostname to verify which VM you are back in
  
<br><br>

<h3>&#9320; Observe DHCP traffic </h3>


<img width="934" alt="30" src="https://github.com/user-attachments/assets/bb7359ca-ae43-4fbf-8594-47413b23cb72">

- In Wireshark, we are going to filter for DHCP traffic only

- DHCP uses ports 67 and 68 this protocol is used for the computer to assign itself an IP address to devices when they are first connected to the network

- Clear out what is in the filter and type in DHCP at the top of Wireshark you will not see any traffic running 

- Open Powershell as an administrator and type in ipconfig /renew then hit enter, if the discover packet did not show up then you have to filter out more

<br><br>
<img width="127" alt="Screenshot 2024-10-27 at 5 45 50 PM" src="https://github.com/user-attachments/assets/06a1c269-90f1-48d3-b47f-6bcbedb10dbf">
<br>


<img width="203" alt="Screenshot 2024-10-27 at 5 46 38 PM" src="https://github.com/user-attachments/assets/cb8f1f65-4057-419f-95d9-f5621ceb67dc">

<br>

<img width="121" alt="Screenshot 2024-10-27 at 5 47 27 PM" src="https://github.com/user-attachments/assets/3d0ddf6a-0dd0-4b48-a720-0e6819b60964">

<br>

<img width="210" alt="Screenshot 2024-10-27 at 5 47 57 PM" src="https://github.com/user-attachments/assets/6f1c8761-41f4-484b-8612-8f6221d91463">
<br><br>

- We will begin running a script
   
- Open Notepad and type in ipconfig /release underneath that ipconfig /renew

- Save what we typed out file -> save

- When the Save As options show up at the top type in c:\programdata

- Save the file name as dhcp.bat

- We will run this in Powershell to have it release all the IP addresses and then it should renew automatically coming back up after killing the network connection 
<br><br>

<img width="544" alt="Screenshot 2024-11-07 at 2 12 52 PM" src="https://github.com/user-attachments/assets/a39cfb36-aedc-4091-8ea8-f138d7bf237d">


- Type in Powershell cd c:\programdata to be inside the programdata

<br><br>

  <img width="533" alt="Screenshot 2024-11-07 at 2 13 10 PM" src="https://github.com/user-attachments/assets/9945f15d-973a-40ab-84ca-94fac1c8605c">


- Type ls for list and you can see dhcp.bat is in the program data that we saved

  <br><br>
  
<img width="650" alt="Screenshot 2024-11-07 at 2 14 36 PM" src="https://github.com/user-attachments/assets/b360088f-e9b4-4076-8b44-d38b533c0d44">

- To run dhcp you will first clear out the data in Wireshark then head back into Powershell and type in .\dhcp.bat and press enter

<br><br>

<img width="1015" alt="Screenshot 2024-11-07 at 2 15 41 PM" src="https://github.com/user-attachments/assets/eae60aa4-cfd2-4038-a86b-80db2b535a1b">

- The connection will die after you hit enter because Ipconfig \release happened but then automatically ipconfig \renew will kick in and restore the connection

- This is the DHCP traffic that was captured in Wireshark

- When release occurred the release packet was sent from the source computer (Windows) to the destination computer

- After the release script command of DHCP was executing the script executed ipconfig /renew making it no need to type that out cause there is no network connection anymore but the command still ran

- Discover happened with that occurring along with the other packets and so the source became zero because the IP address was released and the connection was dropped with the destination address as 255.255.255.255 a.k.a broadcast

- The DHCP server broadcasted back to my computer with a DHCP Offer request and then my computer sent a DHCP request packet to the DHCP server

- Finally, the DHCP server acknowledged the requests from them to my computer, and then an acknowledge request was sent which had my computer now acquire a new IP address 


<br><br>



<img width="644" alt="Screenshot 2024-11-07 at 2 16 50 PM" src="https://github.com/user-attachments/assets/ac6e3034-97da-4306-9133-ee6e5508fac4">

- This address was released and then re-requested by the computer

  
<br><br>


<h3>&#9321; Observe DNS traffic </h3>

<img width="1120" alt="31" src="https://github.com/user-attachments/assets/08659088-37f5-4340-a534-b810ef861dd2">

- First, we are going to filter out DNS traffic
  
- Type in the filter dns hit enter

- There will be a lot of DNS activity to make our own hit the green sharkfin at the top to restart this capture then press continue without saving to start fresh
<br><br>

<img width="600" alt="33" src="https://github.com/user-attachments/assets/0a348b78-6e73-4f50-b24e-b0e17dd1b30b">

- we are going to look for the IP address of disney.com

- In PowerShell type in nslookup disney.com and hit enter

- Once the computer reaches out to the DNS server the DNS server will find out and then tell us the IP address with a bunch of traffic following up behind


- Disney.com resolves to the IP address 130.211.198.204

<br><br>

<img width="1143" alt="32" src="https://github.com/user-attachments/assets/16281162-e100-407f-8ff9-2d1d4ede39e3">


- This is spam that happened on the back end of the nslookup for Disney

- DNS (resolves host names like human-readable names into IP addresses)

<br><br>


<img width="1002" alt="Screenshot 2024-10-27 at 5 54 22 PM" src="https://github.com/user-attachments/assets/a71ce1cc-3ab0-48b8-871a-b090c94a1d46">



- If you copy and paste the address 130.211.198.204 in a browser it will show something in correlation to Disney sometimes

- Sometimes you can load a modern website based on the IP address


<br><br>



<img width="1149" alt="34" src="https://github.com/user-attachments/assets/f8452888-503c-4793-8ef9-cb49428530c2">

- DNS uses TCP and UDP port 53

- In Wireshark type in udp.port==53 and you will still see all the DNS traffic the double equal sign means or

- DNS uses TCP in between DNS servers when they are sharing information, but when your computer looks up DNS records it uses UDP 

<br><br>

<h3>&#9322; Observe RDP traffic </h3>

<img width="599" alt="35" src="https://github.com/user-attachments/assets/7d7c7176-6bc4-46e3-8901-64485e385795">

- RDP (is used when remotely connecting from 1 computer to another to gain a remote desktop  GUI, the computer being connected is typically "listening" for a connection on TCP port 3389

- This remote desktop that we are using is an RDP connection

<br><br>

<img width="1034" alt="Screenshot 2024-11-07 at 2 31 36 PM" src="https://github.com/user-attachments/assets/bccfaf7c-3987-468e-9ab3-ad3835c48bbe">

- When filtering for tcp.port==3389 as you see there is a lot of spam because RDP is constantly streaming a picture from the server to our local machine; constantly sending stuff

- Compared to SSH which only sends traffic when your doing a single keystroke, it sends the keystroke to the server your connected too but RDP has to send an actual photograph



























