### Task 1: Check Security Settings

You are the data protection officer and want to check the SAP system's assignment of authorizations and security.

#### Steps

1. Display all the users _GR##*_ according to logon date and password change.
    
    Which of your users _GR##*_ are not in use?
    
    
    
    Which of your users _GR##*_ do not have a valid password?
    
    
    
    When did the user _GR##-ADM_ log on to the system?
    
![[Pasted image 20251015093318.png]]
Check the logon rules and settings for special users in the system. How can you request this information?

How many characters are set for the minimum password length?
![[Pasted image 20251015093540.png]]
_____________________________________

After how many incorrect logons is the user locked?
![[Pasted image 20251015093645.png]]
_____________________________________

Is the user automatically unlocked?
![[Pasted image 20251015093846.png]]
_____________________________________


### Task 2: Create a Security Policy

Create a security policy with the following restrictions: MIN_PASSWORD_LENGTH = 8 and PASSWORD_CHANGE_INTERVAL = 100.

#### Steps

1. Start the transaction SECPOL.
    
    1. In the _OK code_ field, enter the transaction code SECPOL.
        
2. Create an new security policy _GR##-SECPOL_.
    
    1. Choose the _Display → Change (Ctrl+F1)_ icon.
        
    2. Choose _New Entries_.
        
    3. Enter **GR##-SECPOL** in the _Security Policy_ column and enter **Policy ##** in the _Short Text_ column.
        
    4. Choose _Save (Ctrl+S)_.
        
    5. Select a transport request or create a new one:
        
        To create a new transport request choose _Create_.
        
        Enter a short description and choose _Save (Enter)_.
        
        Enter a short description and choose _Save._
        
    6. Select the line with your security policy _GR##-SECPOL_.
        
    7. Double-click _Attributes_ in the _Dialog Structure_ area.
        
    8. Choose _New Entries_.
        
    9. Enter **MIN_PASSWORD_LENGTH** in the _Policy Attribute Name_ column and enter **8** in the _Attrib. Value_ column.
        
    10. Enter **PASSWORD_CHANGE_INTERVAL** in the _Policy Attribute Name_ column and enter **100** in the _Attrib. Value_ column.
        
    11. Choose _Save (Ctrl+S)_.
        
    12. Choose _Back (F3)_ twice.
        
3. Assign the security policy to the users you have created using the _User Mass Maintenance_ transaction.
    
    |User Name|
    |---|
    |GR##-FI1|
    |GR##-FI2|
    |GR##-SD1|
    |GR##-SD2|
    |GR##-MM1|
    |GR##-MM2|
    
    1. Start the _User Mass Maintenance_ transaction.
        
        **_SAP Menu:_** **→ _Tools_ → _Administration_ → _User Maintenance_ → _User Mass Maintenance_** (transaction code SU10).
        
    2. Choose _Address Data_ in the _User selection_ area.
        
    3. Enter **GR##*** in the _Users_ field.
        
    4. Choose _Execute (F8)_.
        
    5. Choose the _Select All_ icon on the top left of the resulting table (Ctrl+A).
        
    6. Choose _Transfer_.
        
    7. Choose _Change (Shift+F6)_.
        
    8. Enter **GR##-SECPOL** in the _Security Policy_ field.
        
    9. Choose _Change_.
        
    10. Choose _Save (Ctrl+S)_.
        
    
    11. Choose _Back (F3)_ twice.

### Task 3: Explore Authorization Objects for Table Maintenance Using Standard Tools

Create authorizations so that a user can view specific tables in transaction SE16. The user must be able to display two tables. Those table names are USR40 and PRGN_CUST.

#### Steps

1. Which authorization objects give access for the display or maintenance of table contents with generic table access tools?
    
    ___________________________________________________
    
    ___________________________________________________
    
    #### Result
    
    The following authorization objects give access for the display or maintenance of table contents with generic table access tools?
    
    - S_TABU_DIS
    
    - S_TABU_NAM
    
2. Explore authorization object _S_TABU_DIS_.
    
    Display the documentation for the authorization object S_TABU_DIS.
    
    What is the main function of this authorization object?
    
    ___________________________________________________
    
    ___________________________________________________
    
    1. Navigate to the User Information System in the SAP Menu.
        
        SAP Menu: → _Tools_ → _Administration_ → _User Maintenance_ → _Information System_
        
    2. Expand the structure for the _Authorization Objects_ node, and select the report _Authorization Objects - By Object Name, Text_ by double-clicking it.
        
    3. Enter **S_TABU_DIS** in the _Authorization Object_ field.
        
    4. Choose _Execute (F8)_.
        
    5. Double-click object_S_TABU_DIS_.
        
    6. Choose _Display Object Documentation_.
        
        This authorization object checks authorizations for displaying or maintaining table contents.
        
1. Which fields does authorization object S_TABU_DIS contain?

	![[Pasted image 20251015112959.png]]
	
    
    1. Take the fields of S_TABU_DIS from the _Defined fields_ in the documentation:
        
        - DICBERLCS (Authorization Group)
        
        - ACTVT (activity)
        
        Authorization object S_TABU_DIS provides access for all tables of an authorization groups.
        
    2. Choose _Close_.
        
    3. Choose _Cancel (F12)_.
        
    4. Choose _Back (F3)_ to return to the _Authorization Objects by Complex Selection Criteria_ screen.
        
2. Explore authorization object _S_TABU_NAM_.
    
    Display the documentation for the authorization object S_TABU_NAM.
    
    What is the main function of this authorization object?
    ![[Pasted image 20251015113342.png]]
    
    1. Navigate to the User Information System in the SAP Menu.
        
        SAP Menu: → _Tools_ → _Administration_ → _User Maintenance_ → _Information System_
        
    2. Expand the structure for the _Authorization Objects_ node, and select the report _Authorization Objects - By Object Name, Text_ by double-clicking it.
        
    3. Enter **S_TABU_NAM** in the _Authorization Object_ field.
        
    4. Choose _Execute (F8)_.
        
    5. Double-click object_S_TABU_NAM_.
        
    6. Choose _Display Object Documentation_.
        
        This authorization object checks authorizations for displaying or maintaining table contents.
        
3. Which fields does authorization object S_TABU_NAM contain?
    
    ___________________________________________________
    
    ___________________________________________________
    
    1. Take the fields of S_TABU_NAM from the _Defined fields_ in the documentation:
        
        - TABLE (table or view name)
        
        - ACTVT (activity)
        
        Authorization object S_TABU_DIS provides access for a table or a view. The object is only checked if the authorization check for object S_TABU_DIS failed.
        
    2. Choose _Close_.
        
    3. Choose _Cancel (F12)_.
        
    4. Choose _Back (F3)_ to return to the _Authorization Objects by Complex Selection Criteria_ screen.

### Task 4: Find the Authorization Group Assigned to a Table

Find the authorization group assigned to table USR40.

Then, find all tables assigned to authorization group SUSR.

#### Steps

1. Find the authorization group assigned to table USR40.
    
    Table group assigned to table USR40:
	![[Pasted image 20251015113944.png]]
    
    1. **Start the _Generate Table Maintenance Dialog_ transaction (SE54).**
        
        SAP Menu: **_Tools_ → _ABAP Workbench_ → _Development_ → _Other Tools_ → _General Table Maintenance Dialog_**, (transaction code: SE54).
        
    2. Select "Assign Authoriz. Group" and choose _Display_.
        
    3. Enter **USR40** in the _Table/View_ field.
	        
    4. Choose _Execute (F8)_.
        
        Table USR40 is assigned to the authorization group _SUSR_
        
    5. Choose _Back (F3)_ twice to return to the start screen of transaction SE54.
        
2. How many tables are assigned to authorization group _SUSR_?
    
    _________________________________
    
    1. **Start the _Generate Table Maintenance Dialog_ transaction (SE54).**
        
        SAP Menu: **_Tools_ → _ABAP Workbench_ → _Development_ → _Other Tools_ → _General Table Maintenance Dialog_** (transaction code: SE54).
        
    2. Select "Assign Authoriz. Group" and choose _Display_.
        
    3. Enter **SUSR** in the _Authorization Group_ field.
        
    4. Choose _Execute (F8)_.
        
        52 tables are assigned to the authorization group _SUSR_.
        
    1. Choose _Back (F3)_ twice to return to the start screen of transaction SE54.

![[Pasted image 20251015114335.png]]


### Task 5: Create a Role for Reading Tables USR40 and PRGN_CUST

Create a role for reading tables USR40 and PRGN_CUST. Access to table USR40 should be assigned by authorization object S_TABU_DIS and access to table PRGN_CUST should be assigned by authorization object S_TABU_NAM.

#### Steps

1. Start Role Maintenance, create the role _GR##_TAB_ANZ_, and write a short description.
    
    1. **_SAP Menu:_**
        
        **_Tools_ → _Administration_ → _User Maintenance_ → _Role Administration_ → _Roles_** (transaction code PFCG).
        
    2. Enter the name for the role **GR##_TAB_ANZ** in the _Role_ field.
        
    3. Choose _Create Single Role_.
        
    4. Enter description **Display tables** in the _Description_ field.
        
    5. Then choose _Save (Ctrl+S)_ to save your role.
        
2. Add the transaction SE16 to the role menu.
    
    1. Go to the _Menu_ tab page.
        
    2. Choose the _Transaction_ button and enter the following transaction code in the _Transaction code_ field:
        
        - SE16
        
    3. Choose _Assign Transactions_.
        
    4. Then choose _Save (Ctrl+S)_ to save your role.
        
3. Go to the Authorizations tab page and define the authorizations.
    
    Define the following authorizations:
    
    |Object|Field|Value (Interval)|
    |---|---|---|
    |S_TABU_DIS|DICBERCLS|SUSR|
    ||ACTVT|Display|
    
    |Object|Field|Value (Interval)|
    |---|---|---|
    |S_TABU_NAM|TABLE|PRGN_CUST|
    ||ACTVT|Display|
    
    1. Go to the _Authorizations_ tab page.
        
    2. Choose _Change Authorization Data_.
        
    3. Expand _Object Class BC_A_.
        
    4. Expand _Authorization Object S_TABU_DIS_.
        
    5. Expand Authorization _Authorizat. 00_.
        
    6. Choose the _Pencil_ icon to the right of the _DICBERCLS_ field..
        
    7. Enter **SUSR** in the _Field values_ window.
        
    8. Choose _Transfer (Enter)_.
        
    9. Expand _Authorization Object S_TABU_NAM_.
        
    10. Expand Authorization _Authorizat. 00_.
        
    11. Choose the _Pencil_ icon to the right of the _TABLE_ field.
        
    12. Enter **PRGN_CUST** in the _Field values_ window.
        
    13. Choose _Transfer (Enter)_.
        
4. If necessary: Maintain Authorizations - Set all open authorization values to full authorization.
    
    1. Choose the _Status_ button.
        
    2. Choose _Execute (Enter)_ in the _Assign Full Authorization of Subtree_ window.
        
5. Maintain Authorizations - Generate the authorization profile for your role.
    
    1. Choose the _Generate_ icon.
        
    2. In the _Assign Profile Name for Generated Authorization Profile_ window, accept the proposed profile name and choose _Execute (Enter)_.
        
    3. Choose _Back (F3)_ to return to the _Change Roles_ screen.
        
6. Assign the role to your user _GR##-FI1_. Perform a user master comparison and exit role maintenance.
    
    1. Go to the _User_ tab page.
        
    2. Enter **GR##-FI1** in the _User ID_ column.
        
    3. Choose _Save (Crtl+S)_.
        
    4. Choose _User Comparison_.
        
    5. Choose _Full Comparison_ on the _Compare Role User Master Record_ window.
        
    6. Choose _Cancel (F12)_ on the _Compare Role User Master Record_ window.
        
    7. Choose _Back (F3)_ to return to the _Role Maintenance_ screen.


### Task 6: Log On as GR##-FI1 and Check the Table Authorizations

Log on as GR##-FI1. Call transaction SE16, and answer the following questions:

Use the password automatically generated in the exercise for the _user master record_ or assign a new initial password in user maintenance.

Change the password when you log on: ______________________

#### Steps

1. Log on to the system as user GR##-FI1.
    
    1. Start _SAP Logon_.
        
    2. Select system _T41_ and choose _Log On_.
        
    3. Enter the user name **GR##-FI1** in the _User_ field.
        
    4. Enter the generated password in the _Password_ field.
        
        Use the password automatically generated in the exercise for the _user master record_ or assign a new initial password in user maintenance.
        
    5. Choose _Enter_.
        
    6. Enter a new productive password of your choice in the _New Password_ and the _Repeat Password_ fields.
        
        New password : ______________________
        
    7. Choose_Transfer (Enter)_.
        
    8. Choose_Continue (Enter)_.
        
2. Can you display table USR40? Why?
    
    ___________________________________________________
    
    ___________________________________________________
    
    1. Start transaction SE16 (Data Browser) from the _User menu_.
        
    2. Enter **USR40** in the _Table Name_ field.
        
    3. Choose _Table Contents (F7)_.
        
    4. Choose _Execute (F8)_.
        
    5. Choose _Back (F3)_ twice, to return to the _Data Browser: Initial Screen_.
        
    
    #### Result
    
    Yes, you can display table USR40. When this table is displayed, authorization group _SUSR_, which is in the user master record, is checked.
    
3. Can you display table USREFUSVAR? Why?
    
    ___________________________________________________
    
    ___________________________________________________
    
    1. Start transaction SE16 (Data Browser) from the _User menu_.
        
    2. Enter **USREFUSVAR** in the _Table Name_ field.
        
    3. Choose _Table Contents (F7)_.
        
    4. Choose _Execute (F8)_.
        
    5. Choose _Back (F3)_ twice, to return to the _Data Browser: Initial Screen_.
        
    
    #### Result
    
    Yes, you can display table USREFUSVAR. This table is also assigned to the authorization group _SUSR_.
    
4. Can you display table PRGN_CUST? Why?
    
    ___________________________________________________
    
    ___________________________________________________
    
    1. Start transaction SE16 (Data Browser) from the _User menu_.
        
    2. Enter **PRGN_CUST** in the _Table Name_ field.
        
    3. Choose _Table Contents (F7)_.
        
    4. Choose _Execute (F8)_.
        
    5. Choose _Back (F3)_ twice, to return to the _Data Browser: Initial Screen_.
        
    6. Log off the system.
        
    
    #### Result
    
    Yes, you can display table PRGN_CUST. When this table is displayed, authorization is checked by authorization object _S_TABU_NAM_.