<h1>Manually-adding-a-virtual-machine-to-a-domain</h1>

<h2>Description</h2>

<h2>Utilities Used</h2>

- <b>Virtualbox</b>
- <b>virtual machines</b>
- <b>Windows ISO</b> 

<h2>Environments Used </h2>

- <b>Windows 10 OS</b>
- <b>Windows 10 server OS</b>

<h2>Program walk-through:</h2>

One of the first things I did is create a vm dedicated to be a client PC so that it can be later on added to a domain of another vm.

<img src="https://i.imgur.com/BCJx2tL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>   

I then created a vm dedicated to be the domain controller PC. On this vm I installed the Windows 10 server OS so I can access specific domain management tools.

<img src="https://i.imgur.com/kZhk6mZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Once the Windows 10 server OS is installed on the domain vm. I then open Windows and install Active Directory Domain Services to officially make it a domain.

<img src="https://i.imgur.com/IrUbumC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Next I configured the domain vm's network adapters settings so that other vm's/devices can communicate with it.

<img src="https://i.imgur.com/eBpFfNs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

As you can see I configured the clients network adapters settings to be on the same network as the domain vm by assigning a simimilar IP and subnet mask.

<img src="https://i.imgur.com/KKCrcO4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

But after the network configurations I was facing a communication problem between the vm's. When the client vm pinged the IP of the domain vm it was recieving a response. But when the domain vm pinged the client vm there was no response.

<img src="https://i.imgur.com/biZvrna.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

To fix the issue I enabled ICMP on the client side. This enabled will allow pings to be recieved.

<img src="https://i.imgur.com/FbeVJ5Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

When I enabled the ICMP on the client vm and the domain vm pinged the IP of the client vm in the CLI, it then recieved a response.

<img src="https://i.imgur.com/sYmV3M8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/UxPTimw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/utmF0wn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>




