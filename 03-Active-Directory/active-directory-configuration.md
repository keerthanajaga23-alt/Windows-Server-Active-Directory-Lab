# Active Directory Configuration

## 1. Active Directory Overview

Active Directory Domain Services (AD DS) was configured on the Windows Server 2022 domain controller to provide centralized user authentication, account management, and access control.

### Domain Details

| Configuration     | Value          |
| ----------------- | -------------- |
| Domain Controller | APEXTECH-DC1   |
| Domain            | apextech.local |
| NetBIOS Name      | APEXTECH       |
| DNS Server        | 192.168.10.10  |

## 2. Active Directory Domain

A new Active Directory forest was created with the domain:

`apextech.local`

The Windows Server was promoted as the first domain controller for the new forest.

## 3. Organizational Units

Organizational Units (OUs) were created to organize users by department.

The following OUs were created:

* IT-Dept
* Finance-Dept
* HR-Dept

This structure provides a basic organizational model for managing users and applying department-specific policies and permissions.

## 4. Domain Users

The following domain user accounts were created:

| User           | Username       | Department |
| ------------   | ------------   | ---------- |
| Saravana Kumar | Saravana.kumar | IT         |
| Keerthi Jagath | Keerthi.Jagath | Finance    |
| Meena Raj      | Meena.raj      | HR         |

Each user was placed in the appropriate departmental OU.

## 5. Security Groups

Department-based security groups were created:

* `IT-Users`
* `Finance-Users`
* `HR-Users`

Users were added to their corresponding security groups.

### Group Membership

| Security Group | Member         |
| -------------- | ------------   |
| IT-Users       | Saravana.kumar |
| Finance-Users  | Keerthi.Jagath |
| HR-Users       | Meena.raj      |

Security groups were later used to control access to departmental shared folders.

## 6. Authentication and Account Administration

The lab provided hands-on practice with common Active Directory account administration tasks, including:

* Creating domain user accounts
* Managing security group membership
* Organizing users into OUs
* Password management
* Account lockout troubleshooting
* Account enable/disable fundamentals
* Checking user access
* Verifying domain authentication

## 7. Access Control

Security groups were used instead of assigning departmental permissions individually to each user.

For example:

`IT-Users` → access to the IT shared folder

`Finance-Users` → access to the Finance shared folder

`HR-Users` → access to the HR shared folder

This demonstrates the basic principle of managing access through security groups.

## 8. Verification

The following checks were performed:

* Confirmed the `apextech.local` domain
* Confirmed the three departmental OUs
* Confirmed domain user accounts
* Confirmed security groups
* Confirmed group membership
* Confirmed users could authenticate from the Windows 11 client
* Confirmed departmental access restrictions

## 9. Skills Demonstrated

* Active Directory Domain Services
* Domain Controller administration
* Organizational Units
* User account administration
* Security groups
* Group membership
* Authentication fundamentals
* Authorization and access control
* Basic Group Policy concepts
* Active Directory troubleshooting
* Technical documentation

