## The User Master Record and its Tab Pages

The user maintenance transaction allows you to create a user with classic address (_Create_ icon) or to create a technical user (_Create Technical User_ icon).

- #### User with classic address:
    
    - You can maintain personal and workplace data using the transactions and APIs of user administration.
    - You can maintain the company using transaction SUCOMP and assign it using the transactions and APIs of user administration.
- #### Technical user:
    
    A technical user does not have any address data. Use the corresponding field on the "Documentation" tab for the description.

![[Pasted image 20251008143701.png]]

A user can only logon to an SAP system if a user master record with a corresponding password exists. The scope of activity of individual users in the SAP system is defined in the master record by one or more roles, and is restricted by the assignment of the appropriate authorizations.

User master records are client-specific. You must maintain your own user master records for every client in SAP systems.

The following authorization objects are required to create and maintain user master records:

- Authorization to create or maintain a user master record, and to assign it to a user group (object _S_USER_GRP_)
- Authorization for the authorization profiles that you assign to users (object _S_USER_PRO_)
- Authorization to create and maintain authorizations (object _S_USER_AUTH_)
- Authorization to protect roles. With this authorization object, you specify which roles can be edited, and which activities (display, change, create, and so on) are intended for the role(s) (object S_USER_AGR).
- Authorization for transactions that you may assign to the role and for which you can assign authorization to start the transaction in the Role Maintenance (object S_USER_TCD)
- Authorization to restrict values that the system administrator can include in a role or change in Role Maintenance (_S_USER_VAL_)

 
In addition to the possibilities for assigning authorizations in the SAP system described in the following sections, you can ensure that your data is protected with additional measures:

- Secure communication in the network (Secure Network Communication [SNC])
    
- Secure data formats (Secure Store and Forward [SSF])
    
- Security in the Internet
    
- System passwords
    
- Database accesses
    
- Transport system
    
- Your own directory structures for the SAP system, and so on

#### Tab Page: Documentation
![[Pasted image 20251009071744.png]]

The tab _Documentation_ can be used to provide information about the users:

- _Description_: This field contains a short description of the user.
- _Person Responsible_: You can use this field to define an SU01 user who is technically and effectively responsible for this user. This can be useful for traceability in systems, especially for anonymous technical users.
- _Documentation for User_: This field contains the documentation for a user. A time stamp is automatically generated and the person who made the change is recorded for each entry. Only the creation of entries is possible. You cannot change or delete old entries.

#### Tab Page: Address
![[Pasted image 20251009072107.png]]
#### Tab Page: Logon Data
![[Pasted image 20251009072127.png]]The **_Alias_** is an alternative ID for an SAP user. You can assign an alias to a user. This means that 40 characters are available when assigning user names (longer, more descriptive names). The user can therefore be identified using either the (12 character) user name or the alias. The alias is primarily used if users are created in a Self-Service scenario from Internet transactions. In this situation, only the alias is specified and used.

**Security policy**: Sometimes users require a different security policy for logon and passwords than the default values. For example, powerful users such as administrators should have passwords with a higher level of protection than standard users. Such users should be forced to change their passwords more often or have more complex rules for their passwords. However, such requirements, if applied widely, can cause an increase in help desk requests if you force standard users to comply with such requirements.

This field could be used to choose a security policy for the user. Otherwise, the user uses the standard security policy.

**Initial password**: To assign initial passwords you may enter the password manually, generate the password, or deactivate the password. Deactivation means that the user can no longer log on using a password, but only with Single Sign-On variants (X.509 certificate, logon ticket). This is useful if you do not require password-based logon, because logon is performed exclusively in other ways. In this case, deactivating the password increases security, as passwords that are not used are usually still initial.

**_User group for authorization checks_**: To assign the user to a user group, enter the user group. This is required if you want to divide user maintenance among several user administrators. Only the administrator that has authorization for this group can maintain users of this group. If you leave the field empty, the user is not assigned to any group. This means that any user administrator can maintain the user.

It is possible to define the user group as a required entry field for specific clients. Therefore, a user can no longer be created without entering a valid user group. Changing a user group to a blank value is also no longer possible. This function has to be activated manually. For details, see SAP note 1663177 - SU01: User group as required entry field. A valid user group must be maintained; it is used as the standard user group.

**_User type:_** The system proposal is _Dialog_ (normal dialog user). The other user types can be assigned if special kinds of processing have to be performed (see the following figure).

**_Validity period:_** You can specify the validity period of the user master record with these fields. If you do not wish to restrict the validity of the user master record, leave the fields empty.

**_Other data:_** For each user or user group, you should assign an accounting number, which you can choose as required. System usage of that user is settled in the accounting system (ACCOUNTING-EXIT) using this accounting number. Useful accounting numbers, for example, are the cost center or company code of the user.

#### Tab Page: SNC
![[Pasted image 20251009073656.png]]
#### Secure Network Communications

The Secure Network Communications (SNC) functions allow you to use an external security product to secure the communications between SAP System components (for example, between application servers and front-end clients). Encryption can be used in three different areas:

- End-to-end security at the application level
    
- Integrity and privacy protection for data transfer
    
- Secure user authentication

#### Tab Page: Defaults
Start Menu

In this field, you can specify an area menu, which you can choose using the possible entries help. The SAP menu (SAP Easy Access) then only contains the components of this area menu.

A user needs the credit management transactions to perform daily work. If you enter _FRMN_ as the start menu in that user's data, the SAP menu displays only the transactions of credit management.

In transaction SSM2, you can specify the initial menu across the entire system.

Logon Language

The system language when the user logs on. On the logon screen, the user can choose another language if required.

Output Device

A (short) name of a printer in the SAP system, specified in the device definition. The users in the SAP system use this name (or the long name) to select the output device.

Time Zone

The time zone describes the location of an object in relation to its local time. The underlying set of rules describes the time difference between the time zone and UTC in hours and minutes, and the start and end of summer time.

Decimal Notation and Date Format

Different counties use different formats for numbers and dates. Enter the format normally used in your country.


#### Tab Page: Parameters
![[Pasted image 20251009074108.png]]

Using a parameter ID, a field can be filled with default values from SAP memory.

#### Example:

A user only has authorization for company code 1000. When a transaction starts, this company code is saved to the memory using the corresponding parameter ID. On all subsequent screens, all fields referencing the company code data element are then automatically filled with the value 1000.

A field on a screen is only filled automatically with the value saved under the parameter ID of the data element, if you have explicitly allowed this in the Screen Painter.

#### Tab Page: Roles

A role is a set of functions describing a specific work area. In the role, you organize transactions, reports, or web addresses in a user menu. A role can be assigned to any number of users.![[Pasted image 20251009074139.png]]

On the _Roles_ tab page, you can use the possible entries help (F4 help) to display a list of all available roles and then select the desired entries from that list.

You can enter any number of roles in the table, and then restrict their validity using the _Valid From_ and _Valid To_ columns. If you use the input help for these columns, the system displays a calendar in which you can select the date.

Further authorizations can be assigned to a user by a reference user. In addition to the roles assigned to the user itself, the user also references the roles and authorizations that are already assigned to the reference user. The roles of the reference user can be shown or hidden (see SAP Note 2110144 - SU01: Display of reference user roles).![[Pasted image 20251009074214.png]]

#### Tab Page: Profiles

On the _Profiles_ tab page, you assign manually created authorization profiles, and therefore authorizations, to a user. The generated profiles of the roles assigned to the user are also displayed there.
![[Pasted image 20251009074233.png]]

The SAP system contains predefined profiles, such as:

- _SAP_ALL_: To assign all authorizations that exist in the SAP system to users, assign the profile _SAP_ALL_.
    
- _SAP_NEW_: A composite profile to bridge the differences in releases in the case of new or changed authorization checks for existing functions, so that your users can continue to work as normal.
#### Tab Page: Groups

The next tab page, _Groups_, is not currently fully actively used. The main use, for the _Global User Manager_, has officially been deactivated. For this reason, this tab page is not described in detail here. For more information, see SAP Note _433941_, the current online documentation, or access the latest information through the link _www.service.sap.com_.

#### Tab Page: Personalization
![[Pasted image 20251009074520.png]]
On the _Personalization_ tab page, you can make person-related settings using personalization objects. _Personalization_ is available both from role maintenance and in user maintenance. You can define values here that control the results displayed when programs are called (such as display periods: _Last 3 months_, Number of entries: _Max. 50_, and so on).

Steps for using personalization:

1. Choose the _Personalization_ tab page.
2. Go to the application component display (icon with two pages and a blue bar on the right of the display).
3. Select the component for which you want to maintain personalization data. The right side of the display lists the personalization objects provided for this component.
4. Select the desired personalization object and assign the values to be predefined in the dialog window that appears.

#### Tab Page: License Data

SAP software contains a measurement program with which every system produces the information used to determine the payment applicable for the installation.
![[Pasted image 20251009075004.png]]
The measurement program is used exclusively to determine the number of users and the utilized units of SAP products. The results are evaluated in accordance with the contractually agreed conditions.

For more information, see the current version of the document _System Measurement Guide_ (service.sap.com/licenseauditing. You can call this with or without the www prefix).

#### Tab Page: DBMS

Database Management System (DBMS) user management enables SAP NetWeaver Application Server (SAP NetWeaver AS) ABAP to manage users and their privileges on the DBMS.

In a typical SAP NetWeaver Application Server ABAP installation, you maintain the users that run applications on SAP NetWeaver Application Server ABAP. In the DBMS, you maintain a few technical users, but you do not need users in the DBMS for most of your SAP NetWeaver Application Server ABAP users. There are use cases that require you to maintain users in the DBMS.

- SAP Business Warehouse (SAP BW), needs a 1:1 user mapping to map analytic privileges of the database to the virtual analysis authorizations of the SAP BW.
    
- Your users run applications that access the database directly. You must assign privileges to the user in the database.

![[Pasted image 20251009075347.png]]

![[Pasted image 20251009080041.png]]


Most changes that can be made for individual users in the context of user management can also be made for a selected quantity of users.

Log-on data, defaults, parameters, roles, and profiles can be changed for a particular group of users.

In user maintenance, you can make changes to a selected group of users by choosing _Environment / Mass Changes_ (transaction SU10).

Hint

On the Address, Logon Data, and Defaults tab pages, you must select the _Change_ checkbox for each change. This ensures that your changes, such as deleting the content of a field are transferred for the relevant fields.

After each mass change, a dialog box appears, asking whether you would like a log. The log shows who made changes, in which system, at which time.

The log contains several message levels, that you can expand as desired using the relevant buttons. If there is a long text for a particular message, you can also display this by choosing a button displayed next to the message.

While you can make certain specifications for the log display by choosing _Settings_, the _Color Legend_ provides information about the colors used in the display.

You can print the log or save it to a file on your PC.
#### Tab Page: Personalization![[Pasted image 20251009080133.png]]
On the _Personalization_ tab page, you can make person-related settings using personalization objects. _Personalization_ is available both from role maintenance and in user maintenance. You can define values here that control the results displayed when programs are called (such as display periods: _Last 3 months_, Number of entries: _Max. 50_, and so on).

Steps for using personalization:

1. Choose the _Personalization_ tab page.
2. Go to the application component display (icon with two pages and a blue bar on the right of the display).
3. Select the component for which you want to maintain personalization data. The right side of the display lists the personalization objects provided for this component.
4. Select the desired personalization object and assign the values to be predefined in the dialog window that appears.


#### Tab Page: License Data

SAP software contains a measurement program with which every system produces the information used to determine the payment applicable for the installation
![[Pasted image 20251009080157.png]]The measurement program is used exclusively to determine the number of users and the utilized units of SAP products. The results are evaluated in accordance with the contractually agreed conditions.

For more information, see the current version of the document _System Measurement Guide_ (service.sap.com/licenseauditing. You can call this with or without the www prefix).

#### Tab Page: DBMS
Database Management System (DBMS) user management enables SAP NetWeaver Application Server (SAP NetWeaver AS) ABAP to manage users and their privileges on the DBMS.

Hint

Currently only SAP HANA database is supported.

In a typical SAP NetWeaver Application Server ABAP installation, you maintain the users that run applications on SAP NetWeaver Application Server ABAP. In the DBMS, you maintain a few technical users, but you do not need users in the DBMS for most of your SAP NetWeaver Application Server ABAP users. There are use cases that require you to maintain users in the DBMS.

- SAP Business Warehouse (SAP BW), needs a 1:1 user mapping to map analytic privileges of the database to the virtual analysis authorizations of the SAP BW.
    
- Your users run applications that access the database directly. You must assign privileges to the user in the database.![[Pasted image 20251009080255.png]]

To simplify user management of the DBMS, you can create a connection between the user management of SAP NetWeaver Application Server ABAP and the DBMS. When you create users in SAP NetWeaver Application Server ABAP, the SAP NetWeaver Application Server ABAP creates the users in the DBMS automatically, with the same user ID and password. Setting an administrative lock on an SAP NetWeaver Application Server ABAP user also locks the corresponding DBMS user. You can also add and remove DBMS privileges for the DBMS user as far as this is allowed by the DBMS.

The necessary configuration steps are described in the online documentation: DBMS User Management, and in the following Security-Blog: http://scn.sap.com/community/security/blog/2014/10/21.


![[Pasted image 20251009080319.png]]


Most changes that can be made for individual users in the context of user management can also be made for a selected quantity of users.

Log-on data, defaults, parameters, roles, and profiles can be changed for a particular group of users.

In user maintenance, you can make changes to a selected group of users by choosing _Environment / Mass Changes_ (transaction SU10).

Hint

On the Address, Logon Data, and Defaults tab pages, you must select the _Change_ checkbox for each change. This ensures that your changes, such as deleting the content of a field are transferred for the relevant fields.

After each mass change, a dialog box appears, asking whether you would like a log. The log shows who made changes, in which system, at which time.

The log contains several message levels, that you can expand as desired using the relevant buttons. If there is a long text for a particular message, you can also display this by choosing a button displayed next to the message.

While you can make certain specifications for the log display by choosing _Settings_, the _Color Legend_ provides information about the colors used in the display.

You can print the log or save it to a file on your PC.

![[Pasted image 20251009080353.png]]**Display Change Documents:** Choose _Environment / Information System_ and then, on the overview screen that appears, "Change Documents" to display a list of changes made to user master records, authorization profiles, and authorizations.

**Archive Change Documents:** User master records and authorizations are saved in USR* tables. Using the archiving function, you can reduce the memory space occupied by the USR* tables in the database. Change documents are saved in USH* tables. The archiving function deletes change documents from the USR* tables that are no longer needed.

You can archive the following change documents or change records relating to user master records and authorizations from the USH* tables:

- Changes to authorizations (archiving object _US_AUTH_)
    
- Changes to authorization profiles (archiving object _US_PROF_)
    
- Changes to the authorizations assigned to a user (archiving object _US_USER_)
    
- Changes to a user's password or to defaults stored in the user master record (archiving object _US_PASS_)