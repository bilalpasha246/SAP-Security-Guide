## Introduction to Central User Administration

In complex system landscapes with multiple systems and clients, the administration effort required to compare and update user master records is very high. Employees join the company, leave, or change jobs within the company. Individual users usually need to access various systems and clients to perform their work, and therefore require multiple users.
![[Pasted image 20251015142338.png]]
Since user master records are client-specific, they must be administered in each client of each and every system. For example, if you want to create a new user, you must create it manually in all the clients of all the SAP systems in which it should be valid.

User master records can be managed centrally in one client of a system. If a new client is built as a copy of another client, the new client can initially be filled with the user master records of that client. During this copy, the roles of the original client are copied together with the user master records. However, you cannot copy individual users selectively. Also, the user master records cannot be automatically synchronized sequentially.
![[Pasted image 20251015142428.png]]

The essential feature of the Central User Administration is the definition of a **central client** in a selected system. It can be used to manage the user master records for all the clients of the system landscape. For example, you can define which roles should be assigned to which users in which systems. This greatly reduces the administrative cost for authorization administration.

Hint

You can decide individually for each user which systems that user should be able to log on to.

Caution

Central User Administration does not mean that every user must exist in each system of the system landscape. In particular, users of child systems do not necessarily need to exist in the central system.

Which user master record data is administered centrally or only locally can be individually set. Local administration by a user or by an administrator could be useful for certain data of the user master record.

The authorization data is exchanged based on the ALE concept. ALE means Application Link Enabling and permits you to build and operate distributed SAP links. It includes a business-controlled message exchange between loosely linked SAP systems. The application is integrated with asynchronous communication.

### Data Distributable Using Central User Administration

- User master record data, such as the address, logon data, user defaults, and user parameters.
    
- The **assignment** of the user to roles or profiles for each child system. The advantage of administering assignments centrally is that you no longer need to log on to each system to make system-specific assignments of roles and profiles; it is all managed at one location in the central system.
    
- The initial password. When you create a new user, the initial password is distributed to the child systems as a default value. The passwords are distributed in coded form.
    
- The lock status of a user. In addition to the locks caused by incorrect logon that already existed in previous releases or those set manually by the local administrator, there is now also a new "global lock". This applies to all of the child systems in which the user is defined and can be canceled in the central system or locally if required.

## Setting Up CUA
![[Pasted image 20251015142719.png]]

Communication partners are addressed in the ALE scenario with aliases, which are called _logical systems_.

The central system itself and every sub-system is defined by name in the central system in the IMG activity → _Name Logical System_.

You can call this in two ways:

- In the transaction SALE by choosing the menu path _IDoc Interface / Application Link Enabling (ALE)_ → _Basic Settings_ → _Logical Systems_ → _Define Logical System_
    
- By calling transaction BD54
    

In the central system, **all** child systems and the central system are specified. In the child systems, the child system itself, and the central system are defined. The logical system names are assigned to the client definitions in the corresponding systems in transaction SCC4. Each logical system therefore identifies a certain client of an SAP system.


Communication between the central system and the child systems at the network level is performed using Remote Function Calls (RFCs). The technical definition of the connection is maintained in transaction SM59. All the connections to all child systems must be created in the central system, and the connection to the central system must be maintained in the child systems. The RFC connection names must be the same as the names of the logical systems. The communication must be performed using communication users with certain RFC authorizations for CUA in the relevant system.

What data is sent from where to where is defined in the ALE distribution model. User and company data is exchanged within Central User Administration. The distribution model is created and generated in, and distributed from transaction BD64 in the central system. It only needs to be generated in all of the child systems.

Central User Administration is then activated centrally in transaction SCUA.

You can find a detailed description of Central User Administration in the SAP online documentation. SAP course ADM103, "System Administration II for SAP S/4HANA and SAP Business Suite", deals with the technical implementation.
![[Pasted image 20251015143114.png]]
You can define whether each individual component of a user master record should be administered in the central system or locally in the child systems. This is defined within transaction SCUM in the central system. A _field attribute_ can be defined for each input field of the user maintenance transaction SU01.

- If a field of the user maintenance transaction has field attribute **global**, data for this field can only be maintained in the central system. The data is automatically distributed to child systems when it is saved. Such fields are in display mode in the user maintenance transaction of the child systems, that is, you cannot change these fields.
    
- If you use field attribute **default**, a default value, which is automatically distributed to the child systems when it is saved, can be maintained when you create a user in the central system. After distribution, the data is only maintained locally in the child systems and cannot be returned.
    
- If you use field attribute **Redistribution**, the data can be maintained in both the central system and the child systems. If a change is made to the child system, the data is returned to the central system and passed on to other existing child systems from there.
    
- The field attribute **local** means that the data for the corresponding field can only be administered locally in the child systems. When fields of this type are changed in the central system, this data is not distributed to the child systems.
    
- The field attributed **everywhere** is used if you can want to be able to change data locally **and** globally. In the case of local maintenance, however, no redistribution takes place.


## Integration of Existing Systems
![[Pasted image 20251015143335.png]]
The integration of existing systems in the central user administration depends on whether there is a complete new installation of the system infrastructure, or the user master records are built completely anew in all existing systems, or whether the central user administration is set up at a time at which there are already users in the relevant systems that must be migrated to the central user administration.

For a new installation, all the users are newly created in the central system and distributed by Central User Administration. Distribution ensures that the user data is consistent in all systems.

If Central User Administration is installed at a later time, the existing users of the system infrastructure must be copied to the central system. This procedure is called migration. The user identifications copied from the child systems must be compared and adjusted in the central system.

Roles that were already developed and assigned to users in the old systems must be identified by name in the central system. Only then can the users be assigned centrally to roles. The old assignment between users and roles can be copied if required.![[Pasted image 20251015143542.png]]

Existing user master records are migrated to the central system with transaction SCUG in the central system. This procedure can only be performed once for each child system. "User identification" is the SAP logon name to which a combination of the first and last names is assigned.

If the user identification to be copied is not yet contained in Central User Administration, it is entered as _new user_. New users including their user master records can be copied to the central system and then maintained there.

If the user identification to be copied is already in Central User Administration with the identical first and last names, it is entered as _identical user_. Identical users can be copied to the central system. The old system assignment including the valid roles and profile assignment are recorded there.

If the user identification to be copied is already in Central User Administration with a different first or last name, it is entered as a _different user_. If the name given in the central system is correct, the user can be copied.

If the name given in the child system is correct, the first or last name must be corrected in the central system using transaction SU01. If, on the other hand, there are two different people with identical user IDs, you create a new user ID for the user in the child system, delete the old user ID in the child system, and copy the user to the central system.

Transaction SCUG shows the copied users under _Already central users_.![[Pasted image 20251015145217.png]]
After activating Central User Administration, the appearance of user maintenance transaction SU01 changes.

An additional _Systems_ tab, under which the logical systems to which the user is distributed are entered, appears in the central system. The user is only known in these child systems and in the central system. The column _Systems_ also appears on the _Roles_ and _Profiles_ tab pages. You can therefore define the assignment of users to roles and profiles individually for each child system. The data is distributed to the appropriate child systems when you choose _Save_.

Existing roles are still maintained and new roles are still built in the child systems. To assign users in the central system the roles and profiles defined in the child system, there is the _Text comparison_ button in the _Roles_ and _Profiles_ tab pages in the central system. The names of the roles and profiles defined in the child systems are stored in the central system together with their short texts. The names of the roles and profiles are available in the central system in the value help (F4 help). Since the information in the child systems might change, you should occasionally repeat the text comparison.

Only the fields of SU01 for which the field attributes were not defined as "global" accept input in the child systems. It is not possible to create or copy users in the child systems.

## Determining Cross-System Information on Users

There are a number of evaluation options available using the Users node of the user information system (SUIM). Using Central User Administration (CUA) cross-system information on users can be evaluated in the central system.

When evaluating the users on a child system, you have the option to determine the CUA systems in which a certain user exists or to determine all or some of the users in one or more CUA systems. It is also possible to search for users with no system assignment.