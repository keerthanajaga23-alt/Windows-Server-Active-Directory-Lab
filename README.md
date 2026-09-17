# Windows-Server-Active-Directory-Lab

## Project Overview

This is a self-directed hands-on IT infrastructure lab built using Oracle VirtualBox to practice Windows Server administration, Active Directory, DNS, Windows client domain management, SMB file sharing, NTFS permissions, and department-based access control.

The lab simulates a small company environment with separate IT, Finance, and HR departments.

## Objectives

The main objectives of this project were to:

* Build and configure a Windows Server 2022 environment
* Install and configure Active Directory Domain Services (AD DS)
* Create and manage a Windows domain
* Configure DNS for the Active Directory environment
* Create Organizational Units (OUs), users, and security groups
* Configure department-based access control
* Configure SMB network shares and NTFS permissions
* Join a Windows 11 client to the domain
* Test domain authentication and authorization
* Troubleshoot network, DNS, domain, and file-sharing issues
* Document and verify the results

## Lab Environment

| Component         | Configuration                          |
| ----------------- | -------------------------------------- |
| Virtualization    | Oracle VirtualBox                      |
| Domain Controller | Windows Server 2022 Desktop Experience |
| Client            | Windows 11 Pro                         |
| Domain            | `apextech.local`                       |
| Domain Controller | `APEXTECH-DC1`                         |
| DC IP Address     | `192.168.10.10`                        |
| Client IP Address | `192.168.10.20`                        |
| Network           | VirtualBox Internal Network            |
| Network Name      | `Corporate-LAN`                        |
| DNS Server        | `192.168.10.10`                        |

## Lab Architecture

The lab consists of a Windows Server 2022 Domain Controller and a Windows 11 client connected through a VirtualBox Internal Network.

```text
                    Corporate-LAN
                         |
             +-----------+-----------+
             |                       |
     APEXTECH-DC1              Windows 11 Client
   Windows Server 2022          Windows 11 Pro
     192.168.10.10              192.168.10.20
             |
       apextech.local
             |
     +-------+-------+
     |       |       |
    IT    Finance    HR
```

## Active Directory Structure

### Organizational Units

The following Organizational Units were created:

* `IT-Dept`
* `Finance-Dept`
* `HR-Dept`

### Users

| User             | Username        | Department |
| ------------     | --------------  | ---------- |
| Saravana Kumar   | `saravana.kumar`| IT         |
| Keerthi Jagath   | `Keerthi.Jagath`| Finance    |
| Meena Raj        | `Meena.Raj`     | HR         |

### Security Groups

* `IT-Users`
* `Finance-Users`
* `HR-Users`

Each user was added to the security group corresponding to their department.

## File Sharing and Access Control

The following folder structure was created on the Domain Controller:

```
C:\CompanyShares
├── IT
├── Finance
└── HR
```

Department-based permissions were configured using security groups.

| Folder  | Authorized Group | Access |
| ------- | ---------------- | ------ |
| IT      | `IT-Users`       | Modify |
| Finance | `Finance-Users`  | Modify |
| HR      | `HR-Users`       | Modify |

Access was tested using domain users to verify that users could access their own department's resources while being denied access to other departments.

## Windows 11 Client

A Windows 11 Pro client was configured on the same VirtualBox Internal Network.

The client was configured with:

* IP address: `192.168.10.20`
* Subnet mask: `255.255.255.0`
* DNS server: `192.168.10.10`

Connectivity and DNS were verified using:

```cmd
ping 192.168.10.10
```

```cmd
nslookup apextech.local
```

The Windows 11 client was successfully joined to the `apextech.local` domain.

## Access-Control Testing

Domain users were used to verify department-based access.

| User           | IT     | Finance | HR      |
| ------------   | -------| ------- | ------- |
| Saravana Kumar | Allowed| Denied  | Denied  |
| Keerthi Jagath | Denied | Allowed |  Denied |
| Meena Raj      | Denied | Denied  | Allowed |

Users were able to create and modify files in their authorized department share.

## Troubleshooting

During the lab, I encountered and resolved several issues, including:

### Network Connectivity

The Windows 11 client initially could not communicate with the Domain Controller. VirtualBox network configuration and IP settings were checked and corrected.

### DNS and Domain Connectivity

The client was configured to use the Domain Controller as its DNS server. DNS and connectivity were verified before joining the domain.

### SMB File Sharing

The client could ping the Domain Controller but initially could not access the IT network share. Investigation showed that the IT folder had not yet been configured as an SMB share. The folder was then shared and access was successfully verified.

### Domain User Testing

Initial attempts to test domain-user access directly on the Domain Controller resulted in a logon-rights restriction. A separate Windows 11 client was used to perform domain-user authentication and file-access testing instead.

## Skills Demonstrated

* Windows Server administration
* Active Directory Domain Services
* DNS fundamentals
* User and group administration
* Organizational Unit management
* Security group management
* Authentication and authorization
* NTFS permissions
* SMB file sharing
* Windows 11 domain joining
* Network troubleshooting
* DNS troubleshooting
* Access-control testing
* Structured troubleshooting
* Technical documentation

## Key Learning

This project helped me understand how Active Directory, DNS, domain authentication, security groups, NTFS permissions, SMB shares, and authorization work together in a Windows-based IT environment.

It also gave me practical experience troubleshooting issues rather than only following configuration steps.

## Project Status

**Completed**

The core Active Directory, Windows client, file-sharing, permissions, authentication, and access-control testing objectives have been completed.

## Future Improvements

Possible future enhancements include:

* DHCP configuration
* Additional Windows client machines
* Group Policy management
* PowerShell automation
* Centralized event-log monitoring
* Backup and recovery testing
* Additional IT support troubleshooting scenarios

## Disclaimer
This is a self-directed educational lab created for hands-on learning and portfolio development. It is not professional employment experience or a production corporate environment.
This is a self-directed educational lab created for hands-on learning and portfolio development. It is not professional employment experience or a production corporate environment.
