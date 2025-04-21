<h1>Manually-adding-a-virtual-machine-to-a-domain</h1>

<h2>Description</h2>
The aim of this lab is to put a vm under the control of an existing domain without using DHCP.

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

However, after completing the network configurations, I encountered a communication issue between the virtual machines. While the **client VM** was able to successfully **ping** the **domain VM's IP address** and receive a response, the **domain VM** could not receive a response when attempting to ping the **client VM**.

<img src="https://i.imgur.com/biZvrna.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

To resolve the issue, I enabled **ICMP (Internet Control Message Protocol)** on the **client side**, allowing it to receive and respond to ping requests.

<img src="https://i.imgur.com/FbeVJ5Z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

After enabling **ICMP** on the **client VM**, the **domain VM** was able to successfully receive a response when it pinged the client VM's IP address via the **command line interface (CLI)**.

<img src="https://i.imgur.com/sYmV3M8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Next, on the **client VM**, I accessed the system settings and joined it to the **domain** managed by the **domain VM** by searching for the domain name and adding the client to it.

<img src="https://i.imgur.com/UxPTimw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

To confirm that the **client VM** was successfully added to the domain, I opened **Active Directory** on the **domain VM**. I then navigated to the **Computers** section, which displays all devices currently connected to the domain.

<img src="https://i.imgur.com/utmF0wn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>




