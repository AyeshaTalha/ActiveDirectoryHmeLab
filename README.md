# ActiveDirectoryHomeLab
<h2>Description:</h2>
This project guide outlines the steps to set up an Active Directory (AD) home lab using VirtualBox, incorporating a Domain Controller (DC) with two network adapters. The DC will be configured to connect to the internet through one adapter using DHCP and establish an internal network using the second adapter with a static IP address (172.16.0.1). A client machine will connect to the internal network through the DC, allowing internet access through the DC.

<h2>Project Architecture:</h2>
<p align="center">
<img src=https://imgur.com/xm5huv7.png" height="80%" width="80%">



<h2> Pre-Requisites:</h2>
Before starting, ensure you have the following:

VirtualBox installed on your host machine.
Adequate system resources (RAM, CPU) for running multiple virtual machines.
Windows Server installation ISO (e.g., Windows Server 2019 and 2010).

<h2>Project Workflow:</h2>

1. If you dont already have Virtual Box downloaded then go to virtualbox download and download the correct software according to the Operating System you are using. After downloading the Virtual Box, also download the extension pack for the Virtual Box.

<p align="center">
<img src=https://imgur.com/DRa0Hfv.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/GmKrO9q.png" height="80%" width="80%">
<br />

2. We are going to use Windows Server 2019 and Windows Server 2010 for our DC machine and Client1 machine respectively. To use these, we need to download the ISO's of these server. Go to windows server 2009 download and download the ISO's for both the servers. Make sure you remember the location where you're going to save these downloads. We are going to need that later.
<p align="center">        
<img src="https://imgur.com/v56YnjO.png" height="80%" width="80%">
<br />

3. First, let us create the first virtual machine - DC. 
<p align="center">
<img src="https://imgur.com/ELZocHt.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/EO2Xnxp.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/aAJPETh.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/RHTDsQe.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/Mul0KZL.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/H96Cd2z.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/9IdtuNb.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/uzo8kLZ.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/uzo8kLZ.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/4Y6cBBI.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/u5f6ZHO.png" height="80%" width="80%">
<br />
<p align="center">
 <img src="https://imgur.com/j2T9tD4.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/RnNMoZh.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/wVAqGuI.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/sFTcCA1.png" height="80%" width="80%">
<br />

4. Set a password for the inbuilt administrator account. I recommend using the same password for all the things in this lab so you don't forget the password. To start off, we need to setup the ip addressing. From the architecture diagram, we see that there are two NIC's attached to this DC machine. One is connected to the internet which gets its IP address automatically from our home network and the other is connected to the internal network which we have to be set manually. for our convenience let's rename the network's according to our architecture diagram and then change the internal network IP to 172.16.0.1 with subnet mask 255.255.255.0 and DNS as 127.0.0.1(loopback address).
And also change the name of the PC to DC.
<p align="center">
<img src="https://imgur.com/5VHQbyt.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/8e3dUIo.png" height="80%" width="80%">
<br /> 
<p align="center">
<img src="https://imgur.com/8aQcE30.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/X1X2G0G.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/lp98MvI.png" height="80%" width="80%">
<br /> 
<p align="center">
<img src="https://imgur.com/1WfFcVE.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/ZP5TQMg.png" height="80%" width="80%">
<br />
<img src="https://imgur.com/FnzvBeb.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/qhPUNGN.png" height="80%" width="80%">
<br /> 
<p align="center">
<img src="https://imgur.com/PO4zgz5.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/eIGbXdG.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/0OOAnWS.png" height="80%" width="80%">
<br /> 
<p align="center">
<img src="https://imgur.com/LnQKgCN.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/bOB6yX2.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/0T4Dgxw.png" height="80%" width="80%">
<br />

5.The next step would be to download Active Directory on the machine DC. Go to the Server Manager and follow the below given steps to install the Active Directory and create users.
<p align="center">
<img src="https://imgur.com/eypYhXW.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/EOa6Ubz.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/gnOLj49.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/GWVA3Ho.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/Xw6zrRD.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/EuwlskC.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/kQhVsoz.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/p7SX9VB.png" height="80%" width="80%">
<br />
 <p align="center">
<img src="https://imgur.com/ib8OCyX.png" height="80%" width="80%">
<br />

6. Now, we have to promote this machine as the domain controller.To do so, click on the little flag option on the righthand corner of the screen and click on promote this achine as the domain controller. Click on Add a new forest and enter the domain name as mydoamin.com. Follow the steps and just click next to every option and click on install. The machine will reboot.
<img src=".png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/SB2UDIJ.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/G0UViIC.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/agimhZ5.png" height="80%" width="80%">
<br />
<img src="https://imgur.com/jmnIuff.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/KQ1zHlO.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/nY3nuJt.png" height="80%" width="80%">
<br />

7. When the machine reboots now you can see the MYDOMAIN/ADMIN account instead of just the ADMINISTRATOR account that we saw earlier. This means that our machine now is the domain controller of the domain Mydomain.com. Sign in with the admin password.
<p align="center">
<img src="https://imgur.com/8RpuM2U.png" height="80%" width="80%">
<br />

8. Now we are going to create our own dedicated Admin account istead of using the built-in Admin account. To do so, click on Start>Windows Administrative Tools>Active Directory Users and Computers. Right click on mydomain>new>organizational unit. Create an OU named Admins. To create a new user in the OU, right click on Admins>new>user. Create a new user called Ayesha Talha with a login Id. To make this user as admin, right click on the user > properties > member of > Add. In the object names section, add Domain Admins and apply changes. now sign out of the current admin profile by clicking on start > profile > sign out. On the main menu, click on other user and now you can login with the credentials of the admin user we just created. 
<p align="center">
<img src="https://imgur.com/8MANqQz.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/qtvynkK.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/tjKQlx5.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/MagaNkf.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/zRPVDQq.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/Wcw4lvt.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/qQkUlVy.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/oMctKWz.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/RzV5WiF.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/7a80Hs7.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/lE1gVNk.png" height="80%" width="80%">
<br />
 
9. Sign out of the current admin profile by clicking on start > profile > sign out. On the main menu, click on other user and now you can login with the credentials of the admin user we just created.
<p align="center">
<img src="https://imgur.com/yxlBfOb.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/SjyTbj5.png" height="80%" width="80%">
<br />

10. The next thing we are going to do is install RAS/NAT (RemoteAccessServer / NetworkAddressTranslation). This server will allow our Client which is on the private virtual network to have access to the internet through DC. Go to Server Manager. Click on Add Roles and Features. 
<p align="center">
<img src="https://imgur.com/LY4FNCD.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/n3SmKEG.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/tlVabDY.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/jqMQo4x.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/1uYRvel.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/oPkKU56.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/zUPWVoY.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/IGAPyQT.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/WWKqa6q.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/uLTwATN.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/SVXiJ8t.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/5DqfAR9.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/QVGttta.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/thtPFMj.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/JVcyfOa.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/aiCi0vE.png" height="80%" width="80%">
<br />

11. Now we have to setup a DHCP server on our Domain Controller. This will allow the users on the Client machine to get an IP address and browse on the internet eventhough there are on a private network. Go to the Server Manager > Add Roles and Features > DHCP Server > Next > Install.
<p align="center">
<img src="https://imgur.com/O5NDDMz.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/1RXOa2z.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/vdrqRU5.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/6pL7FgD.png" height="80%" width="80%">
<br />
<p align="center">
<img src=".png" height="80%" width="80%">
<br />
<p align="center">
<img src=".png" height="80%" width="80%">
<br />

12. Now, we are going to create a bunch of users in the Active Directory. Open the internet explorer and Go to this [link](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbmx2TXhCQ1g0TjZPNTJkSkw0TGI0dkYtX25jQXxBQ3Jtc0treF9aVktJaTZRZ2pUZ1ZBVEw1NWs1MWtoaVBRek9nM08ycEdZVlNYdjVmZ1FfWWZhazFIem9IZXBYZHhzVDJVOTI3WmhYQkpZc2pPWXdSSXFlTVEtLVNiQlpDM3JybDRaWmJmOXVzdi1aU0gya0ZKZw&q=https%3A%2F%2Fgithub.com%2Fjoshmadakor1%2FAD_PS%2Farchive%2Frefs%2Fheads%2Fmaster.zip&v=MHsI8hJmggI) , download the script and save it on the desktop so it would be easy for us to access it. Open the text file that contains the names of users to be created and add your name to the list. 
<p align="center">
<img src="https://imgur.com/vENrR3M.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/QNSffit.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/4eBrhmB.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/QBdC9Tv.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/RX7RsR7.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/QQoGvNa.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/jxoS7vv.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/N6xKSDw.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/w3GnCa1.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/fp8eGJ5.png" height="80%" width="80%">
<br />
<p align="center">
<img src=".png" height="80%" width="80%">
<br />
<p align="center">
<img src=".png" height="80%" width="80%">
<br />

13. Let's go ahead and create the second machine Client1. Go to Virtual Box and create a new VM named Client1. Configure the network settings to connect to the internal network rather than to the internet. Use the Windows 10 ISO we downloaded in Step 2. Configure it with minimum settings.
<p align="center">
<img src="https://imgur.com/CYZorF6.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/XCG05DT.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/wigmcww.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/49roaKl.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/EjhWllb.png" height="80%" width="80%">
<br />
<p align="center">
<img src="https://imgur.com/OztacqF.png" height="80%" width="80%">
<br />

14. 






