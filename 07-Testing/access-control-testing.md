# Access Control Testing and Verification

## 1. Testing Objective

The purpose of testing was to verify that:

* Domain users could authenticate successfully.
* Users could access their authorized departmental folder.
* Users could modify files in their authorized folder.
* Users were denied access to other departments' folders.
* The Active Directory security groups were correctly controlling access.

All testing was performed from the Windows 11 domain-joined client.

## 2. User Authentication Testing

The following domain accounts were tested:

| User            | Domain Account          | Authentication |
| ------------    | ---------------------   | -------------- |
| Saravana Kumar  | APEXTECH\saravana.kumar | Successful     |
| Keerthi Jagath  | APEXTECH\keerthi.jagath | Successful     |
| Meena Raj       | APEXTECH\meena.raj      | Successful     |

Successful login confirmed that the Windows 11 client could authenticate users against the `apextech.local` domain.

## 3. Department Access Testing

### Saravana Kumar — IT

Saravana Kumar was tested as a member of:

`IT-Users`

Result:

* IT folder → **Allowed**
* Finance folder → **Denied**
* HR folder → **Denied**

Saravana was able to create and modify a test file in the IT folder.

### Keerthi Jagath — Finance

Priya Sharma was tested as a member of:

`Finance-Users`

Result:

* Finance folder → **Allowed**
* IT folder → **Denied**
* HR folder → **Denied**

Priya was able to create and modify a test file in the Finance folder.

### Meena Raj — HR

Meena Raj was tested as a member of:

`HR-Users`

Result:

* HR folder → **Allowed**
* IT folder → **Denied**
* Finance folder → **Denied**

Meena was able to create and modify a test file in the HR folder.

## 4. Test Results

| User          | IT      | Finance | HR      |
| ------------  | ------- | ------- | ------- |
|Saravana Kumar | Allowed | Denied  | Denied  |
|Keerthi Jagath | Denied  | Allowed | Denied  |
|Meena Raj      | Denied  | Denied | Allowed |

The results matched the intended department-based access-control design.

## 5. File Modification Testing

Authorized users were also tested for file modification.

The following actions were successfully performed in the authorized departmental folders:

* Create a test file
* Save the file
* Modify the file
* Verify the file

This confirmed that the configured NTFS Modify permissions were functioning as intended.

## 6. Troubleshooting During Testing

### Domain Controller Direct Login Test

An attempt was initially made to test a domain user's access directly on the domain controller.

Windows displayed a logon-rights error indicating that the user had not been granted the requested logon type on that computer.

The test was not changed by modifying domain-controller logon security policies.

Instead, testing was moved to the Windows 11 client, which is the appropriate workstation environment for validating normal domain-user access.

The domain users successfully authenticated and completed the required access tests from the client.

## 7. Verification Summary

The completed tests confirmed:

* Active Directory authentication was functioning.
* Domain users were correctly associated with departmental security groups.
* NTFS permissions were correctly applied.
* SMB shares were accessible from the domain-joined client.
* Authorized users could create and modify files.
* Unauthorized departmental access was denied.
* The access-control design worked as intended.

## 8. Skills Demonstrated

* User authentication testing
* Active Directory verification
* Security-group testing
* NTFS permission testing
* SMB share testing
* Access-control troubleshooting
* Domain-user troubleshooting
* Verification and documentation

