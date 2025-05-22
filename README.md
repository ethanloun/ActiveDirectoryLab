<h1>ActiveDirectoryLab</h1>

<h2>Description</h2>
I set up an Active Directory home lab using Oracle VirtualBox to simulate a Windows domain environment. This project helped me develop a strong understanding of how Active Directory functions and how Windows networking operates within a domain. I also used PowerShell to efficiently create and manage user accounts.
<br />

<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Oracle VirtualBox</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (22H2)
- <b>Server 2019</b>

<h2>Walk-through:</h2>

<p align="center">
Booting up with Server 2019: <br/>

Setting up the first VirtualBox with Server 19. This will act as the Domain Controller.

![Image](https://github.com/user-attachments/assets/bfc1e23f-4edd-48ec-a3fd-5a716c1db07a)

<p align="center">
Identify Internet NIC: <br/>

As seen by the IPv4 Address(10.0.2.15)

![Image](https://github.com/user-attachments/assets/ca2e0c82-c22f-4b19-bbaa-3756b0113153)

<p align="center">
Identify Internal NIC: <br/>

As seen by the Autoconfiguration IPv4 Address(169.254.196.79). This was automatically assigned due to the DHCP server being unreachable.

![Image](https://github.com/user-attachments/assets/14229ad2-b9c0-41c2-8cc7-04e2eddc3a77)

<p align="center">
Assigning IP Address: <br/>

Assigning IP to Internal. Not assinging Default Gateway because the DC will serve as the Default Gateway. Using Loopback for DNS. 

![Image](https://github.com/user-attachments/assets/340aff3b-233f-4405-a691-e3d8c47726fc)

<p align="center">
Installing Active Directory Domain Services: <br/>

![Image](https://github.com/user-attachments/assets/ca2e0c82-c22f-4b19-bbaa-3756b0113153)

<p align="center">
Creating Domain: <br/>

![Image](https://github.com/user-attachments/assets/499e4cc5-8b56-498d-91ae-ebddf5f44e97)

<p align="center">
Setting up Admin Account: <br/>

Creating my own Admin Account instead of default account.

![Image](https://github.com/user-attachments/assets/5584b311-a59f-4760-855a-7281f9937f31)

<p align="center">
Domain Admin Account: <br/>

![Image](https://github.com/user-attachments/assets/2419f765-6705-4bf6-828b-2bb311dfa3af)

<p align="center">
Setting up Remote Access Server: <br/>

RAS and NAT will allow the Windows 10 Client to be on a virtual private network while still being able to access the Internet through the DC.

![Image](https://github.com/user-attachments/assets/da316d3d-b075-402d-81a1-b0a71d2eca05)

<p align="center">
Configure Network Address Translation to Internet: <br/>

Using public interface to connect to Internet, using the Internet interface.

![Image](https://github.com/user-attachments/assets/fbff6678-9b08-4ac2-83e7-0766e98514bf)

<p align="center">
Adding DHCP Server: <br/>

Allow Windows 10 Client to obtain IP Address that will let them browse the Internet.

![Image](https://github.com/user-attachments/assets/966ce7e2-5061-4fd9-a068-51dae4acbf50)

<p align="center">
Scope of DHCP: <br/>

Using Scope of 172.16.0.100-200

![Image](https://github.com/user-attachments/assets/a45786b7-d06b-446d-adcb-3f3cbc723a73)

<p align="center">
Defining Default Gateway: <br/>

Using Internal NIC as Router/Default Gateway(172.16.0.1)

![Image](https://github.com/user-attachments/assets/32d7acbb-3cbe-4bf7-bed3-850e133b828a)

<p align="center">
DNS is set up: <br/>

Domain Controller is the DNS Server otherwise I can not join the domain.

![Image](https://github.com/user-attachments/assets/f10577c8-0f94-4ae9-a22c-0e1ac71de7e3)

<p align="center">
Powershell Script to Create 1k+ Users: <br/>

All users have the username of their first inital with last name and the default password.

![Image](https://github.com/user-attachments/assets/b2ee50b7-41c2-4ade-9b2d-64432fa1af67)

<p align="center">
Creating Users: <br/>

![Image](https://github.com/user-attachments/assets/49109128-ae4c-4e7d-84dd-b746d87715a7)

<p align="center">
Users are set: <br/>

![Image](https://github.com/user-attachments/assets/17b266a8-2b51-4b4e-8dfc-94ede9e030a1)

<p align="center">
Set Up Client with Windows 10: <br/>

Setting up the second VirtualBox with Windows 10. 

![Image](https://github.com/user-attachments/assets/fd5124cb-4580-4467-9ba5-896eee0833a3)

<p align="center">
Check for Internet on Client: <br/>

![Image](https://github.com/user-attachments/assets/547cccd6-83d6-460a-b9a6-5d79b5aeed33)

<p align="center">
Ping for Connectivity: <br/>

Google resolved which means the DNS Server is working. Using the DC as the Default Gateway to reach the Internet and then sends an echo reply. 

![Image](https://github.com/user-attachments/assets/4ac75d10-ddf3-4f8b-9d58-614464aedab8)

<p align="center">
Joining Client to Domain: <br/>

Rename computer and join Domain. 

![Image](https://github.com/user-attachments/assets/9f85b72f-78d6-419d-9eb7-df244173142a)

<p align="center">
Now Member of Domain: <br/>

Checking the Address Leases I can see that the Client reached out to the DHCP and obtained an IP Address. Now I can use any of those user's names to login. 

![Image](https://github.com/user-attachments/assets/6dc98ab7-cad3-4332-81f2-d27d99b292a5)
