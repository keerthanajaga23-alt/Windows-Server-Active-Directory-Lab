# Windows Server Configuration

## 1. Server Overview

A Windows Server 2022 virtual machine was created using Oracle VirtualBox as part of a self-directed Active Directory administration lab.

### Server Details

| Configuration    | Value                                  |
| ---------------- | -------------------------------------- |
| Operating System | Windows Server 2022 Desktop Experience |
| Server Name      | APEXTECH-DC1                           |
| Server Role      | Domain Controller                      |
| Domain           | apextech.local                         |
| NetBIOS Name     | APEXTECH                               |
| Network          | Corporate-LAN                          |
| IP Address       | 192.168.10.10                          |
| Subnet Mask      | 255.255.255.0                          |
| DNS Server       | 192.168.10.10                          |
| Default Gateway  | Not configured                         |

## 2. VirtualBox Network Configuration

The Windows Server virtual machine was connected to a VirtualBox Internal Network named:

`Corporate-LAN`

This isolated network was used to allow communication between the Windows Server and Windows 11 client virtual machines.

## 3. Static IP Configuration

A static IPv4 address was configured on the Windows Server.

Configuration:

* IP Address: `192.168.10.10`
* Subnet Mask: `255.255.255.0`
* Default Gateway: Blank
* Preferred DNS Server: `192.168.10.10`

The server uses itself as the DNS server because it hosts the Active Directory-integrated DNS service.

## 4. Windows Server Role

The server was configured to provide the following infrastructure services:

* Active Directory Domain Services (AD DS)
* DNS Server
* Domain Controller
* User and group administration
* Authentication and authorization
* File-sharing and access-control testing

## 5. Domain Controller Promotion

Active Directory Domain Services was installed and the server was promoted to a new domain controller.

A new forest was created with the domain:

`apextech.local`

During the promotion process:

* DNS Server was installed
* Global Catalog (GC) was enabled
* Read Only Domain Controller (RODC) was not enabled
* DNS delegation was not configured
* Default database, log, and SYSVOL paths were used
* A Directory Services Restore Mode (DSRM) password was configured

After the promotion, the server restarted and became the first domain controller for the `apextech.local` domain.

## 6. Verification

The following checks were performed after configuration:

* Confirmed the server name was `APEXTECH-DC1`
* Confirmed the server IP address was `192.168.10.10`
* Confirmed the `apextech.local` domain was available
* Confirmed Active Directory Users and Computers was accessible
* Confirmed DNS was functioning
* Confirmed the Windows 11 client could communicate with the server
* Confirmed domain users could authenticate from the Windows 11 client

## 7. Troubleshooting

### Issue: Client Could Not Initially Reach the Server

The Windows 11 client initially returned:

`Destination host unreachable`

### Investigation

The following configuration was checked:

* VirtualBox network settings
* Server network connection
* Client network connection
* Client IP address
* Server IP address
* DNS configuration

Both virtual machines were confirmed to be connected to the same `Corporate-LAN` Internal Network.

After correcting the network configuration, the client was able to communicate with the domain controller.

### Verification

The Windows 11 client successfully reached:

`192.168.10.10`

This confirmed basic network connectivity between the client and domain controller.

## 8. Skills Demonstrated

This part of the lab provided hands-on practice with:

* Windows Server administration
* Virtual machine configuration
* IPv4 configuration
* DNS fundamentals
* Active Directory Domain Services
* Domain Controller deployment
* Network troubleshooting
* Basic Windows infrastructure administration
* Technical documentation

nshot should show relevant server configuration without exposing passwords or other sensitive information.

