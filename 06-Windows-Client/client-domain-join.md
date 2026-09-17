# Windows 11 Client and Domain Join

## 1. Client Overview

A Windows 11 Pro virtual machine was created using Oracle VirtualBox and connected to the same isolated network as the Windows Server domain controller.

### Client Details

| Configuration    | Value           |
| ---------------- | --------------- |
| Operating System | Windows 11 Pro  |
| Computer Name    | DESKTOP-P0GNKL3 |
| Network          | Corporate-LAN   |
| IP Address       | 192.168.10.20   |
| Subnet Mask      | 255.255.255.0   |
| Default Gateway  | Not configured  |
| DNS Server       | 192.168.10.10   |
| Domain           | apextech.local  |

## 2. VirtualBox Network Configuration

The Windows 11 client was connected to the VirtualBox Internal Network:

`Corporate-LAN`

The server and client were therefore able to communicate through the isolated virtual network.

## 3. Windows 11 Network Configuration

A static IPv4 configuration was applied to the client:

* IP Address: `192.168.10.20`
* Subnet Mask: `255.255.255.0`
* Default Gateway: Blank
* Preferred DNS Server: `192.168.10.10`

The client was configured to use the domain controller as its DNS server.

## 4. Network Connectivity Testing

Connectivity between the client and domain controller was tested using:

`ping 192.168.10.10`

The client was eventually able to receive replies from the domain controller.

DNS resolution was also tested using:

`nslookup apextech.local`

These tests confirmed that the client could communicate with and resolve the Active Directory domain.

## 5. Domain Join

The Windows 11 client was joined to the Active Directory domain:

`apextech.local`

Domain administrator credentials were provided during the domain-join process.

After successfully joining the domain, the client was restarted.

## 6. Domain Authentication

After the restart, domain user accounts were used to test authentication.

The following accounts were successfully used from the Windows 11 client:

* `APEXTECH\arun.kumar`
* `APEXTECH\priya.sharma`
* `APEXTECH\meena.raj`

Successful authentication confirmed that the Windows 11 client was communicating correctly with the Active Directory domain controller.

## 7. Access Testing

The domain-joined client was used to test departmental file access.

Users were tested against:

* IT share
* Finance share
* HR share

Authorized users were able to access their departmental folder, while access to other departmental folders was denied.

## 8. Troubleshooting

### Issue: Initial Network Connectivity Failure

The client initially returned:

`Destination host unreachable`

The VirtualBox network configuration and IP/DNS settings were checked on both virtual machines.

Both machines were confirmed to be connected to:

`Corporate-LAN`

After correcting the configuration, communication between the client and domain controller was successful.

### Issue: Windows 11 Installation Requirements

During the Windows 11 virtual machine setup, installation requirements related to TPM and Secure Boot were encountered.

VirtualBox TPM 2.0 support was enabled for the client virtual machine, allowing the installation to proceed.

## 9. Verification

The following were successfully verified:

* Windows 11 Pro client installation
* Static IP configuration
* DNS configuration
* Connectivity to the domain controller
* DNS resolution
* Domain membership
* Domain user authentication
* Access to authorized departmental shares
* Denial of unauthorized departmental access

## 10. Skills Demonstrated

* Windows 11 administration
* TCP/IP configuration
* DNS configuration
* Network troubleshooting
* Active Directory domain joining
* Domain authentication
* Windows client administration
* SMB share access
* Access-control verification

