# File Server, Shares and Permissions

## 1. Folder Structure

A company folder structure was created on the Windows Server for departmental file access.

The main folder was:

`C:\CompanyShares`

The following departmental folders were created:

* `C:\CompanyShares\IT`
* `C:\CompanyShares\Finance`
* `C:\CompanyShares\HR`

## 2. Security Groups

Departmental security groups were used to control access:

| Folder  | Security Group |
| ------- | -------------- |
| IT      | IT-Users       |
| Finance | Finance-Users  |
| HR      | HR-Users       |

## 3. NTFS Permissions

NTFS permissions were configured on the departmental folders.

The appropriate departmental security group was granted Modify-level access to its corresponding folder.

For example:

`IT-Users` → Modify access to the IT folder

`Finance-Users` → Modify access to the Finance folder

`HR-Users` → Modify access to the HR folder

The permissions included:

* Read
* Write
* List folder contents
* Read & execute
* Modify

Full Control was not assigned to the departmental groups.

## 4. SMB Network Shares

The departmental folders were configured as network shares so that domain users could access them from the Windows 11 client.

The share names were:

* `IT`
* `Finance`
* `HR`

The IT share initially could not be accessed because the folder had not yet been configured as an SMB share.

## 5. Troubleshooting the IT Share

### Problem

The Windows 11 client could communicate with the domain controller, but access to the IT folder failed.

### Investigation

The server's Computer Management console was checked:

`Computer Management → Shared Folders → Shares`

The IT folder was not listed as a shared folder.

### Resolution

Advanced Sharing was enabled for the IT folder.

The folder was configured as:

* Share this folder: Enabled
* Share name: `IT`
* Share permission: Everyone – Read

NTFS permissions remained responsible for controlling the user's actual file-system access.

### Verification

After the share was configured, the Windows 11 client successfully accessed:

`\\192.168.10.10\IT`

## 6. Access Control Design

The lab demonstrated department-based access control.

Users were given access through security-group membership rather than individual user permissions.

Expected access:

| User           | Department Folder | Result  |
| ------------   | ----------------- | ------- |
| Saravana Kumar | IT                | Allowed |
| Saravana Kumar | Finance           | Denied  |
| Saravana Kumar | HR                | Denied  |
| Keerthi Jagath | Finance           | Allowed |
| Keerthi Jagath | IT                | Denied  |
| Keerthi Jagath | HR                | Denied  |
| Meena Raj      | HR                | Allowed |
| Meena Raj      | IT                | Denied  |
| Meena Raj      | Finance           | Denied  |

## 7. Verification

Access was tested from the Windows 11 domain-joined client using the three domain accounts.

The tests confirmed that:

* IT users could access the IT folder.
* Finance users could access the Finance folder.
* HR users could access the HR folder.
* Users were denied access to other departmental folders.
* Authorized users could create and modify test files in their own departmental folders.

## 8. Skills Demonstrated

* Windows file-system administration
* NTFS permissions
* SMB file sharing
* Security-group-based access control
* Modify permissions
* Access verification
* Permission troubleshooting
* Least-privilege fundamentals
* Windows Server administration
