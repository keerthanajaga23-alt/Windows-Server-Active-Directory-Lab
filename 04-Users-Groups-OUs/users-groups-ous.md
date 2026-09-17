# Users, Groups and Organizational Units

## 1. Organizational Units

Three departmental Organizational Units (OUs) were created in the `apextech.local` Active Directory domain.

* `IT-Dept`
* `Finance-Dept`
* `HR-Dept`

OUs were used to organize user accounts according to their departments.

## 2. User Accounts

Three domain user accounts were created for testing centralized authentication and access control.

| Full Name      | Username      | Department |
| ------------   | ------------  | ---------- |
| Saravana Kumar | Saravana.kumar| IT         |
| Keerthi Jagath | Keerthi.Jagath| Finance    |
| Meena Raj      | Meena.Raj     | HR         |

Each user account was placed in its corresponding departmental OU.

## 3. Security Groups

The following security groups were created:

* `IT-Users`
* `Finance-Users`
* `HR-Users`

Users were added to their respective departmental security groups.

| User           | Security Group |
| ------------   | -------------- |
| Saravana.kumar | IT-Users       |
| Keethi.Jagath  | Finance-Users  |
| Meena. Raj     | HR-Users       |

## 4. Why Security Groups Were Used

Security groups provide a manageable way to assign permissions to multiple users.

Instead of assigning folder permissions directly to individual users, departmental access was assigned through security groups.

For example:

`IT-Users` → IT folder

`Finance-Users` → Finance folder

`HR-Users` → HR folder

This approach makes access management easier to maintain when users are added, removed, or moved between departments.

## 5. Account Administration Practice

The lab provided hands-on practice with:

* Creating domain users
* Organizing users into OUs
* Creating security groups
* Adding users to groups
* Password management
* Account lockout troubleshooting
* Account enable/disable fundamentals
* Verifying user authentication
* Checking group membership

## 6. Verification

The Active Directory Users and Computers console was used to verify:

* Departmental OUs
* User accounts
* Security groups
* Group membership
* User organization within the domain

Domain users were subsequently tested from the Windows 11 client to verify authentication and departmental access.

## 7. Skills Demonstrated

* Active Directory user administration
* Organizational Units
* Security groups
* Group membership
* Account management
* Authentication fundamentals
* Authorization fundamentals
* Access-control administration

