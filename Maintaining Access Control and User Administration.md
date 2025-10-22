![[Pasted image 20251009112328.png]]
There are two ways in which you can control the choice of user passwords:

- You can use the system profile parameters to assign a minimum length for passwords and define how often users must set new passwords.
    
- Invalid passwords can be entered in the table of reserved passwords, _USR40_. This table is maintained with transaction SM30. The entries can also be made generically:
    
    - "**?**" denotes a single character
        
    - "*****" denotes a character string
        

Example:

- If you enter "123*" in table USR40, passwords may not begin with the character string "123*".
    
- If you define "*ABC*", passwords cannot contain the character string "ABC" in any position.
    

There are general rules for passwords that cannot be deactivated. A password:

- Must be at least six characters long (by default)
    
- Must not begin with "?" or "!"
    
- Must not be "pass"
    
- The new password must differ from the old one by at least one character

![[Pasted image 20251009112514.png]]
_login/min_password_lng_

You can set the minimum length for passwords with the parameter **_login/min_password_lng_**. By default, the password must be at least "6" and no more than "40" characters long. The parameters _login/min_password_digits_, _login/min_password_letters_, _login/min_password_lowercase_, _login/min_password_uppercase_, and _login/min_password_specials_ specify the minimum number of **digits, letters (number of upper and lower case)** or **special characters** that a password must contain. The value range is 1 to 40.

_login/password_expiration_time_

The parameter **_login/password_expiration_time_** specifies the number of days after which a user must set a new password. If the parameter is set to 0, the user does not need to change his or her password.

_login/password_max_idle_initial_

The parameter _login/password_max_idle_initial_ indicates the maximum length of time during which an initial password (a password selected by the user administrator) remains valid if it is not used. Once this period has expired, the password can no longer be used for authentication. The user administrator can reactivate the password logon by assigning a new initial password.

_login/password_max_idle_productive_

This parameter indicates the maximum length of time a productive password (a password chosen by the user) remains valid when it is not used. Once this period has expired, the password can no longer be used for authentication. The user administrator can reactivate the password logon by assigning a new initial password.

_login/min_password_diff_

With the parameter **_login/min_password_diff_**, the administrator can determine the number of different characters a new password must possess in comparison with the old one when users change their passwords. This parameter does not take effect when a new user is created or passwords are reset (==> initial password).

![[Pasted image 20251009112706.png]]
_login/fails_to_session_end_

You can set the number of failed logon attempts after which SAP GUI is terminated using the parameter **_login/fails_to_session_end_**. If the user wants to try again, he or she must restart SAP GUI.

_login/fails_to_user_lock_

You can set the number of failed logon attempts after which a user is locked in the SAP system using the parameter **_login/fails_to_user_lock_**. An entry is written in the system log at the same time. The failed logon counter is reset after a successful logon attempt.

_login/failed_user_auto_unlock_

At midnight (server time), the users that were locked as a result of incorrect logon attempts are **no longer automatically** unlocked by the system (default value since SAP NetWeaver 7.0). You reactivate this automatic unlocking with the parameter **_login/failed_user_auto_unlock_** = 1.

The administrator can unlock, lock, or assign a new password to users in user maintenance (transaction SU01).

_login/disable_multi_gui_login_

If the parameter **_login/disable_multi_gui_login_** is set to 1, a user cannot log on to a client more than once. This can be desirable for system security reasons. This parameter applies to SAP GUI logons. If the parameter is set to 1, the user has the following options when he or she logs on again: "Continue with this logon and end any other logons in the system" or "Terminate this logon". Users to whom this should not apply should be specified in the parameter **_login/multi_login_users_**, separated with commas, and with no spaces.

#### The following parameters add a new level of detail to the implementation of the password policy in the SAP system.

_login/min_password_lowercase_

**_login/min_password_lowercase_**: In accordance with the parameter value, the password must contain at least "x" lowercase letters. The default value is "0".

_login/min_password_uppercase_

**_login/min_password_uppercase_**: The parameter value defines the minimum number of uppercase letters a password must have. The default value is "0".

_login/password_change_waittime_

**_login/password_change_waittime_**: Users can change their passwords again only after waiting for a specified amount of time. The default value is "1", which means the user must wait a day to change his or her password again. User administrators, however, can change or reset the password of users as many times in a day as they need.

_login/password_charset_

**_login/password_charset_**: The default value is "1". This parameter is used only if downward compatible passwords need to be generated. It specifies which characters can be used in the password. All Unicode characters are allowed, by default.

_login/password_downwards_compatibility_

**_login/password_downwards_compatibility_**: The system generates downward compatible password hashes, which correspond to an "8" character long password. Downward compatibility is required for RFC communication with older SAP releases. The default value is "1".

![[Pasted image 20251009113033.png]]

Essentially, there are two types of special users: those created by installing the SAP system and those created when you copy clients.

During the installation of the SAP system, client _000_ is created. Depending on the SAP system that is installed clients _001_ and _066_ are created in addition. Special users are predefined in the clients. Since there are standard names and standard passwords for these users, which are known to other people, you must protect them against unauthorized access.

#### SAP System Special User, SAP*

_SAP*_ is the only user in the SAP system for which no user master record is required, since it is defined in the system code. _SAP*_ has, by default, the password "_PASS_", and unrestricted access authorizations for the system.

When you install the SAP system, a user master record is automatically created for _SAP*_ in client _000_ (and in _001_ if it exists). At first, this still has the initial password "**_06071992_**". The administrator is required to reset the password **during** installation. The installation can continue only after the password has been changed correctly. The master record created here deactivates the special properties of _SAP*_, so that only the authorizations and password defined in the user master record now apply.

#### DDIC User

This user is responsible for maintaining the ABAP Dictionary and the software logistics.

When you install the SAP system, a user master record is automatically created in client _000_ [_001_] for the user _DDIC_. With this user too, you are requested to change the standard password of "**_19920706_**" during the installation (similar to the user SAP*). Certain authorizations are predefined in the system code for the _DDIC_ user, meaning that it is, for example, the only user that can log on to the SAP system during the installation of a new release.

#### EarlyWatch User

The EarlyWatch user is delivered in client _066_ and is protected with the password "_SUPPORT_". The EarlyWatch experts at SAP work with this user. This user should not be deleted. Change the password. This user should only be used for EarlyWatch functions (monitoring and performance).

How can you counter this problem to protect the system against misuse?

- You can deactivate the special properties of _SAP*_. To do this, you must set the system profile parameter **login/no_automatic_user_sapstar** to a value greater than zero. If the parameter is active, _SAP*_ no longer has any special properties. If the user master record _SAP*_ is deleted, the logon with _PASS_ no longer works.
    
- If you want to reinstate the old behavior of _SAP*_, you must first reset the parameter and restart the system.

## Security Policy and Restricting the Log On of Users

#### Security Policy

Sometimes users require a different security policy for log on and passwords than the default values. For example, powerful users such as administrators should have passwords with a higher level of protection than standard users. Such users should be forced to change their passwords more often or have more complex rules for their passwords. However, such requirements, if applied widely, can cause an increase in help desk requests if you force standard users to comply with such requirements.

Use this field to choose a security policy for the user. Otherwise, the user uses the standard security policy.

#### Defining Security Policies

With this procedure, you create security policies with attributes, for which you explicitly do not want to use the default value. For example, you assign a new security policy called Digits, and change, as described below, the standard value for the attribute MIN_PASSWORD_DIGITS from 0 to 4. The new security policy Digits then uses the standard values for all security policy attributes, with the exception of the attribute MIN_PASSWORD_DIGITS. You can, however, also create a security policy without defining attributes. This policy then uses the default values for all security policy attributes.

Procedure:

1. Start the maintenance tool for security policies (transaction SECPOL).
    
2. In change mode, choose _New Entries_.
    
3. Enter a name in the _Security Policy_ field and a description in the _Short Text_ field.
4. Double-click the _Attributes_ node.
5. Select the security policy, and double-click the _Attributes_ node again. The change view for attributes appears.
6. Choose _New Entries_.
    
7. In the field _Policy Attribute Name_, enter, for example using the input help, a security policy attribute and, in the _Attribute Value_ field, a value.

Procedure:

1. Start the maintenance tool for security policies (transaction SECPOL).
    
2. In change mode, choose _New Entries_.
    
3. Enter a name in the _Security Policy_ field and a description in the _Short Text_ field.
4. Double-click the _Attributes_ node.
5. Select the security policy, and double-click the _Attributes_ node again. The change view for attributes appears.
6. Choose _New Entries_.
    
7. In the field _Policy Attribute Name_, enter, for example using the input help, a security policy attribute and, in the _Attribute Value_ field, a value.

![[Pasted image 20251009113633.png]]

#### Assigning Security Policies to Users

The security policy could be assigned to a user by using the user maintenance tool (transaction SU01), or assign it to multiple users using mass user maintenance (transaction SU10). On the _Logon Data_ tab, enter a security policy for the user, in the _Security Policy_ field.

#### Restricting the Users' Log On While Maintenance Work is Performed in the System

During maintenance work, only certain administrators should be able to log on to the system. The logon of users to the application server could be restricted by setting the new profile parameter **_login/server_logon_restriction_**.

The following values are possible:

- 0: No restriction.
    
    All users can log on to the application server.
    
- 1: A logon to the application server is allowed only with special rights.
    
    Only those users whose assigned security policy contains the new attribute SERVER_LOGON_PRIVILEGE with the value 1 can log on to the system. To change the security policy, use transaction SECPOL. Change the relevant security policy that you have assigned only to your administrators. Include the guideline attribute SERVER_LOGON_PRIVILEGE in the security policy and set the value to 1. Users who log on to the system without special rights see the following error message: **Server is currently not generally available (restricted logon)**.
    
- 2: No logon is allowed to the application server.
    
    Users who log on to the system see the following error message: **Server is currently not available (logon not permitted)**.
    
- 3: An external logon to the application server is allowed only with special rights.
    
    Only those users whose assigned security policy contains the attribute SERVER_LOGON_PRIVILEGE with the value 1 can log on to the system externally. Users who try to log on to the system externally without special rights see the following error message: **Server is currently not generally available (restricted logon)**.
    
- 4: No external logon to the application server is allowed.
    
    Users who try to log on to the system externally without special rights see the following error message: **Server is currently not available (logon not permitted)**.


### Restricting the Logon of Users (**_login/server_logon_restriction_**)

- 0: No restriction.
    
- 1: A logon to the application server is allowed only with special rights.
    
- 2: No logon is allowed to the application server.
    
- 3: An external logon to the application server is allowed only with special rights.
    
- 4: No external logon to the application server is allowed.
    

#### Locking Inactive Users

To lock all inactive users, use the report RSUSR_LOCK_USERS with which you can automatically select and lock. On the selection screen of the report RSUSR_LOCK_USERS, select the criteria that you want to apply for locking the user. You have the option to check the result of the selection and display the users that you found or to lock the users immediately. Bear in mind that only a local user lock is set. You can execute the report online and in the background.

## Special Authorization Objects

In the area of authorizations, there are a few objects that occur regularly, and are used and specified for daily queries. To clarify their use, some of these objects are described in the following pages
![[Pasted image 20251015085243.png]]
![[Pasted image 20251015085840.png]]
Authorization object **_S_TABU_DIS_** defines which table contents may be maintained by which employees.

The authorization object **_S_TABU_DIS_** controls only complete accesses, which are made using standard table maintenance (SM31), advanced table maintenance (SM30), or the Data Browser (SE16). These group assignments are defined in table _TDDAT_.

The object consists of the following fields:

- _DICBERCLS_: Authorization group for ABAP Dictionary objects (description - maximum of 4 characters)
    
- _ACTVT_: Activity (02, 03).
    

#### Example:

_Authorization 1_:

In this case, table entries may be added, changed or deleted (_ACTVT_:=02), but only tables/views assigned to authorization group "V*" (_DICBERCLS=V*_) may be maintained.

SAP standard tables are assigned to authorization groups. These assignments can be changed ("SM30"). **You should consider this carefully, however.** Depending on the setting, some maintenance dialogs could produce data inconsistencies thereafter.

The important tables are:

- _V_DDAT_54_: Assignment of authorization group to tables/view.
    
- _V_BRG_54_: Assignment of authorization groups to tables/views.
    

The table authorization group of a table or maintenance view can be assigned using transaction SE11 or SE54. The permitted table authorization groups are defined using transaction SE54 or those defined in the maintenance dialog V_TBRG_54.

The maximum length of a table authorization group name is only four characters. It is therefore very difficult to represent a meaningful name concept. Using a parameter namespace is not possible.

In addition to the previous maintenance tools for the authorization groups based on the table TBRG, a central maintenance environment (transactions STBRG and STBRG_OBJ) is provided. As well as the ability to define authorization groups independently of the client, these can now also be provided as workbench objects (transport object SUCU) across clients. As part of this enhancement, the authorization field for table authorization groups was extended from four to fourteen characters, so that namespace-based authorization groups could be defined and assigned for the authorization object S_TABU_DIS as of this maintenance level (see SAP note 1645260 - Enhanced maintenance of table authorization groups).

The authorization concept for generic table access using such standard transactions as SE16, SE17, SM30, SM31 or SM34 was previously only bound to the authorization object **_S_TABU_DIS_**. With SAP note 1481950 - New authorization check for generic table access, the authorization concept was enhanced with the authorization object **_S_TABU_NAM_** that checks access at the table name level. If a user does not have any S_TAB_DIS authorization for a certain table, the system also checks whether the user has an **_S_TABU_NAM_** authorization. The access is permitted if the user has an **_S_TABU_NAM_** authorization.

![[Pasted image 20251015085856.png]]

The authorization object S_TABU_NAM contains the fields:

- _ACTVT_: Activity (02, 03).
    
- TABLE: Name of table or view to be checked
    

With this object, the system checks the view names or table names directly so that an exact authorization check is possible.

![[Pasted image 20251015085933.png]]
Authorization object **_S_TABU_CLI_**: Grants authorization to maintain cross-client tables with the standard table maintenance transaction (SM31), extended table maintenance transaction (SM31), and the Data Browser, and also in the Customizing system. It also acts as an additional security measure for cross-client tables and enhances the general table maintenance authorization **_S_TABU_DIS_**.

The object has the following field:

_CLIIDMAINT_: If identifier **"X"** or **"*"** is set, cross-client tables can be maintained.
![[Pasted image 20251015090035.png]]

By introducing organization criteria, you can restrict a user's access rights to specific parts of a table. A possible use for **_S_TABU_LIN_** is to display and to change content for only a certain work area, such as a country or a plant.

As you can see in the graphic, the object consists of fields.

#### Activity:

- _02_: Add, change, or delete table entries
    
- _03_: Only display table contents.
    

#### Organizational Criterion:

Table key fields/row authorization, such as organizational criteria (defined in Customizing)

#### Attribute for Organizational Criterion:

Attributes 1 to 8 for the organizational criterion; each attribute for a certain table key field.
![[Pasted image 20251015090122.png]]
  
As is familiar from previous releases, it is possible to check programs using the authorization object _S_PROGRAM_.

The programs (reports) are combined into program authorization groups and can be protected against unauthorized access using the groups. The authorization group is stored in the properties of the programs.

You can also store your own authorization groups in SAP programs (without making modifications).

You can assign authorizations for the following activities by program groups:

- Starting a program (_SUBMIT_)
    
- Scheduling a program as a background job (_BTCSUBMIT_)
    
- Variant maintenance (_VARIANT_)
![[Pasted image 20251015090630.png]]

The object _S_PROGNAM_ is used to supplement the start authorization check for programs. Authorizations for this object are checked exclusively with method CL_SABE=>AUTH_CHECK_PROGNAM() in the context of scenarios for switchable authorizations (maintenance transaction SACF). The check does not take place with each submit command, but only if it is called explicitly. If the associated scenario is activated, all programs are checked in addition to the existing authorization checks (for example, with authorization groups).