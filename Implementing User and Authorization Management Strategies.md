## User and Authorization Administration

In today's system landscapes, an administrator has many tasks to perform to structure and maintain user master records and roles. These activities should also be subjected to an authorization check and should not all be available to one administrator. You can use the object presented on the following pages to flexibly create a principle of dual or treble control.

### Daily Tasks and Activities of an Administrator

- Create, maintain, lock and unlock users, and change passwords
    
- Create and maintain roles
    
- Maintain transaction selections and authorization data in roles
    
- Generate authorization profiles
    
- Assign roles and profiles
    
- Transport roles
    
- Monitor using the Information System
    
- Archive change documents
    

The administrator uses the transactions SU01 and PFCG for the activities listed above. When these transaction codes are used, the following objects are checked in the program code.

![[Pasted image 20251015090805.png]]

The object User Master Record Maintenance: User Groups (_S_USER_GRP_) defines the user groups for which an administrator has authorization and the activities that are allowed.

The object _S_USER_GRP_ can be used to grant administration rights for only a certain user group in decentralized administration.

Authorization object S_USER_SAS is checked in transactions SU01, SU10, PFCG, and PFUD when roles, profiles, and systems are assigned to users. It is a further development of the authorization objects _S_USER_GRP_, _S_USER_AGR_, _S_USER_PRO_, and _S_USER_SYS_, which were previously checked when authorizations were made.

The checking of authorization object _S_USER_SAS_ is activated by default and can be deactivated using a Customizing switch. To deactivate, use transaction SM30 to create an entry in table _PRGN_CUST_ with the _ID_**CHECK_S_USER_SAS** and the value **NO**. This means that the authorization objects _S_USER_GRP_, _S_USER_AGR_, _S_USER_PRO_, and _S_USER_SYS_, are used again.

Only one of the Role and Authorization Profile fields is ever checked. The other field can be left empty in the definition of the authorizations.

The previous object _S_USER_SYS_ can be used in decentralized administration to grant administration rights for only users in a certain system from the central user administration. The object _S_USER_SYS_ defines which system a user administrator can access from the central user administration and the activities that are allowed.![[Pasted image 20251015091045.png]]

The object Authorization: Role Check (_S_USER_AGR_) defines the role names for which an administrator is authorized and the activities that are allowed.

The object _S_USER_AGR_ can be used in decentralized administration to grant an administrator authorization access to only certain roles (such as for a module or an organizational unit).

The object Authorizations: Transactions in Roles (_S_USER_TCD_) defines the transactions that an administrator may include in a role.

The object _S_USER_TCD_ can be used to grant an administrator authorization to include only certain transactions in roles and thus prevent critical transactions from being included in roles.

The object Authorizations: Field Values for Roles (_S_USER_VAL_) defines the field values an administrator may enter in roles for a particular authorization object and particular fields.

The object _S_USER_VAL_ can be used to grant an administrator authorization to assign only certain authorizations in roles and thus prevent critical authorizations from being included in roles.
![[Pasted image 20251015091158.png]]
The object User Master Record Maintenance: Authorization Profile (_S_USER_PRO_) defines the profile names for which an administrator has authorization and the activities that are allowed.

The object _S_USER_PRO_ can be used to grant an administrator authorization to assign only certain profiles in a decentralized administration (such as for a module or an organizational unit).

The object User Master Record Maintenance: Authorizations (_S_USER_AUT_) defines the authorization object name and the authorization name for which an administrator has authorization and the activities that are allowed.

The object _S_USER_AUT_ can be used to grant an administrator authorization to create only certain authorizations in roles and thus prevent critical authorizations from being created in roles.![[Pasted image 20251015091250.png]]
This authorization object _S_USER_ADM_ checks access to general administration functions for user and authorization administration.

The object contains exactly one authorization field with the name of the administration functions. The field _S_ADM_AREA_ can have the following values:

- CHKSTDPWD: Display special users (such as SAP*) with default passwords.
- PRGN_CUST: Change the Customizing table PRGN_CUST.
- SSM_CUST: Change the Customizing table SSM_CUST.
- USR_CUST: Change the Customizing table USR_CUST.
- USR_CUST_S: Change the Customizing table USR_CUST_SYSTEM.
- ID_MODEL: Change the identity model.
- SNC4: Check canonical SNC names.

Each administration function includes the area to be administered and the activity required to do this.
## Options for Decentralization of User Administration

#### Options for Decentralization of User Administration

### Security Requirements

- An administrator may not administer users **and** maintain authorizations **and** generate authorization profiles
    
- Solution by separating functions
    
    #### Principle of dual control
    
    - User administration
        
    - Authorization maintenance and generation
        
    
    #### Principle of treble control
    
    - User administration
        
    - Authorization maintenance
        
    - Authorization generation
        

The authorization system can be used to flexibly organize maintenance of the user master records, profiles, and authorizations.

- If your company is small and is organized centrally, all the tasks connected with maintaining the user master records and the authorization components can be handled by a single user called the superuser.
    
- If you want to ensure that your system maintains a higher level of security, you can share the responsibility for maintaining the user master records and the authorizations among a user administrator and an authorization administrator, each having limited responsibility (principle of dual control).
    
- For maximum system security you can share the responsibility for maintaining the user master records and the authorizations among a user administrator, an authorization data administrator and an authorization profile administrator, each having limited responsibility (principle of treble control).
    
- Since you can assign specific authorizations for the user and administrator maintenance, the administrators need not be privileged users in your IT department. Normal users can be responsible for maintaining the user master records and authorizations.![[Pasted image 20251015091432.png]]

Sharing the administrative tasks among three administrators is called the **principle of treble control**.

The superuser sets up all the user master records, profiles, and authorizations for the administrator.

The **authorization data administrator** creates the roles, selects transactions, and maintains the authorization data. He or she simply saves the data in Role Maintenance since he or she does not have the necessary authorization for generating the profile. He or she accepts the proposed profile name "T-...". The **authorization data administrator** may not change users, nor generate profiles.

The **authorization profile administrator** starts transaction SUPC and chooses _All Roles_. He or she then restricts his or her selection, for example by entering the ID of the role to be edited. On the next screen, he or she chooses _Display Profile_ to check the data. If all the data is correct, he or she generates the authorization profile. The **authorization profile administrator** may not change users, change the data for roles, nor generate profiles containing authorization objects beginning with _S_USER*_.

The **user administrator** then assigns this role to a user (from the user maintenance transaction SU01). The profile is entered for the user. The **user administrator** may not change data for roles, nor change or generate profiles.

The principle of dual control combines the tasks and authorizations of the authorization data administrator and those of the authorization profile administrator.![[Pasted image 20251015091832.png]]

With decentralized user administration, there are several user administrators each responsible for administration of a certain group of users.

The administration tasks in decentralized user administration can be shared according to different criteria:

- #### Application Area / Module
    
    The users are assigned to decentralized user administrators, each of whom is responsible for a business application or an SAP module.
    
- #### Locations
    
    The users are assigned to decentralized user administrators, each of whom is responsible for all users at that location.
    
- #### Departments
    
    The users are assigned to decentralized user administrators, each of whom is responsible for all the users in the department.
    

Technically, decentralization is implemented by grouping users to form user groups. Each decentralized user administrator may only administer the users assigned to the user group for which he or she is responsible. Accordingly, each decentralized user administrator may only assign the roles needed for his or her application module, location, or department.

### Scenario 1, Principle of Dual Control

- #### Central User Administration
    
    - One user administrator for all users
        
    - Unlimited authorizations for all user administration tasks of the user administrator
        
- #### Central Maintenance of Roles and Profiles
    
    One administrator performs both roles
    
    - Authorization data administrator
        
    - Authorization profile administrator
        
    - All authorizations for maintaining the roles and profiles
![[Pasted image 20251015092048.png]]

### Scenario 2, Principle of Treble Control

- #### Decentralized User Administration (Production System)
    
    One **user administrator for each application area** (FI, MM):
    
    - Authorized to maintain a certain user group
        
    - Authorized to assign a certain number of roles and profiles
        
    - No other restrictions in the specific user administration tasks
        
- #### Central Maintenance of Roles and Profiles
    
    Separation of responsibilities:
    
    - One authorization data administrator
        
    - One authorization profile administrator
        
    - No other restrictions with regard to specific roles or profiles for both administrators
![[Pasted image 20251015092217.png]]

This scenario has two user groups, each of which is administered by its own user administrator in the production system.

- The group of FI users (_FI_USER_) is administered by the FI user administrator.
    
- The group of MM users (_MM_USER_) is administered by the MM user administrator.
    

The decentralized user administrators must be restricted as follows:

- Administration of the user group for which they are responsible (_S_USER_GRP_)
    
- Assignment of the relevant roles and profiles for the user group (_S_USER_AGR_, _S_USER_PRO_)
    

The users must be assigned to the appropriate groups (_FI_USER_, _MM_USER_).

**Caution**: Users not belonging to any group can be administered by both user administrators.

### Scenario 3, Principle of Treble Control, Decentralized User Administration in PRD

- #### Central Creation and Deletion for All Users (prod.)
    
- #### Decentralized User Administration (Production System)
    
    One user administrator for each application area (FI, MM):
    
    - Authorized to maintain a certain user group
        
    - Authorized to assign a certain number of roles and profiles
        
    - Authorized for only certain user administration tasks (change, lock/unlock, reset password)
        
- #### Central Maintenance of Roles and Profiles
    
    Separation of responsibilities:
    
    - One authorization data administrator
        
    - One authorization profile administrator
        
    - No other restrictions with regard to specific roles or profiles for both administrators

![[Pasted image 20251015092526.png]]

This scenario has two user groups, each of which is administered by its own user administrator in the production system:

- The group of FI users (_FI_USER_) is administered by the FI user administrator.
    
- The group of MM users (_MM_USER_) is administered by the MM user administrator.
    

In contrast to scenario 2, the user administrators may only perform the following activities for users in their group:

- Lock / unlock users
    
- Change passwords
    
- Assign roles and profiles
    

A central user administrator creates and deletes the users.

The decentralized user administrators must be restricted as follows:

- Administration of the user group for which they are responsible (_S_USER_GRP_)
    
- Activities in user administration (_S_USER_GRP_)
    
- Assignment of the relevant roles and profiles for the user group (_S_USER_AGR_, _S_USER_PRO_)
    

The users must be assigned to the appropriate groups (_FI_USER_, _MM_USER_).
