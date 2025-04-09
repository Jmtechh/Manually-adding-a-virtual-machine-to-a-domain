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

One of the first steps I took was creating a virtual machine specifically designated as a **client PC**, which I later added to the domain managed by another VM.

<img src="https://i.imgur.com/BCJx2tL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>   

I then created a virtual machine designated as the **Domain Controller PC**. On this VM, I installed the **Windows Server 10 OS** to gain access to domain management tools and features.

<img src="https://i.imgur.com/kZhk6mZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Once the **Windows Server 10 OS** was installed on the domain VM, I opened Windows and installed **Active Directory Domain Services (AD DS)** to officially promote it to a domain controller.

<img src="https://i.imgur.com/IrUbumC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Next, I configured the **network adapter settings** on the **domain VM** to ensure that other virtual machines and devices could successfully communicate with it.

<img src="https://i.imgur.com/eBpFfNs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

As shown, I configured the **client VM's network adapter settings** to be on the same network as the **domain VM** by assigning a similar **IP address** and **subnet mask**.

<img src="https://i.imgur.com/KKCrcO4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

But after the network configurations I was facing a communication problem between the vm's. When the client vm pinged the IP of the domain vm it was recieving a response. But when the domain vm pinged the client vm there was no response.

<img src="https://i.imgur.com/biZvrna.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

To fix the issue I enabled ICMP on the client side. This enabled will allow pings to be recieved.

<img src="https://i.imgur.com/FbeVJ5Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

When I enabled the ICMP on the client vm and the domain vm pinged the IP of the client vm in the CLI, it then recieved a response.

<img src="https://i.imgur.com/sYmV3M8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

The next thing I did was on the client vm I went into settings and added the client to the domain of the domain vm by searching the domains name and adding it.

<img src="https://i.imgur.com/UxPTimw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

To confirm that the client vm is apart of the domain I went into the domain vm and opened up Active Directory. From there I went to the computer section which displays all connected devices that have been added to the domain.

<img src="https://i.imgur.com/utmF0wn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>




