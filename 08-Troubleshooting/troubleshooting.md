# Troubleshooting

## 1. Overview

Several configuration and connectivity issues were encountered while building and testing the Windows Server and Active Directory lab.

The troubleshooting process followed a structured approach:

1. Understand the problem
2. Gather information
3. Check basic configuration
4. Isolate the issue
5. Identify the cause
6. Apply a solution
7. Verify the result
8. Document the outcome

---

## 2. Client Could Not Initially Ping Domain Controller

### Problem

The Windows 11 client initially could not communicate with the domain controller.

The ping test returned:

`Destination host unreachable`

### Investigation

The following items were checked:

* VirtualBox network configuration
* Server network connection
* Client network connection
* Server IP address
* Client IP address
* DNS configuration
* Internal Network name

Both virtual machines were checked to ensure they were connected to:

`Corporate-LAN`

### Resolution

The network configuration was corrected so that both machines were connected to the same VirtualBox Internal Network.

### Verification

The client was subsequently able to ping:

`192.168.10.10`

This confirmed network connectivity between the client and domain controller.

---

## 3. Windows 11 Could Not Initially Access the IT Share

### Problem

The Windows 11 client could communicate with the domain controller, but access to the IT folder failed.

### Investigation

The server was checked using:

`Computer Management → Shared Folders → Shares`

The IT folder was not listed as a shared folder.

### Root Cause

The IT folder existed locally on the server but had not been configured as an SMB network share.

### Resolution

Advanced Sharing was enabled for the IT folder.

The configuration was:

* Share this folder: Enabled
* Share name: `IT`
* Share permission: Everyone – Read

NTFS permissions continued to control the actual file-system access.

### Verification

The client was able to access:

`\\192.168.10.10\IT`

The issue was resolved.

---

## 4. Domain User Logon Test on Domain Controller

### Problem

An attempt was made to test a domain user directly on the domain controller.

Windows displayed a logon-rights error indicating that the user had not been granted the requested logon type on that computer.

### Investigation

The issue was related to the security policy controlling interactive logon rights on the domain controller.

The Local Security Policy interface was also checked during troubleshooting.

### Resolution

No unnecessary security-policy changes were made to allow normal users to log on interactively to the domain controller.

Instead, domain-user authentication and access were tested from the Windows 11 domain-joined client.

### Verification

The following domain accounts successfully logged in from the Windows 11 client:

* `APEXTECH\sarvana.kumar`
* `APEXTECH\keerthi.jagath`
* `APEXTECH\meena.raj`

The users were then tested against the appropriate departmental shares.

---

## 5. Windows 11 Installation Requirement

### Problem

The Windows 11 virtual machine initially encountered installation requirements related to TPM and Secure Boot.

### Resolution

TPM 2.0 support was enabled in the VirtualBox virtual machine configuration.

The Windows 11 installation was then completed successfully.

### Verification

The Windows 11 Pro client was successfully installed and used as the domain-joined workstation for the lab.

---

## 6. Troubleshooting Skills Demonstrated

This lab provided practical experience with:

* Network connectivity troubleshooting
* IP configuration verification
* DNS troubleshooting
* SMB share troubleshooting
* NTFS permission troubleshooting
* Active Directory authentication troubleshooting
* Windows security-policy awareness
* Virtual machine configuration
* Structured root-cause analysis
* Verification after corrective actions
* Technical documentation

## 7. Key Learning

The troubleshooting process demonstrated the importance of checking the simplest configuration items first, isolating the problem before making changes, and verifying the result after applying a solution.

The lab also reinforced the importance of testing domain-user access from an appropriate client workstation rather than unnecessarily changing security policies on a domain controller.

