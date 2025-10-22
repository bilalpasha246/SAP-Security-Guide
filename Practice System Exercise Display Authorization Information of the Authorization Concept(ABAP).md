### Task 1: Access the Training System Landscape

Log in to your training landscape and log on to your training system.

#### Steps

1. Log in to your Training Landscape
    
    Follow the guidance of your instructor.
    
2. Log on to the SAP GUI on the training system T41 as user ADM940-##.
    
    1. Start SAP Logon.
    2. Select system T41 and choose Log On.
    3. Enter **ADM940-##** in the User field.
    4. Enter the initial password **Welcome1** in the Password field.
    5. Enter your log-on language (**EN** or **DE**) in the Language field.
    6. Choose Enter.
    7. Enter a password of your choice in the New Password and the Repeat Password fields.
    8. Choose Transfer (Enter).
    9. Choose Continue (Enter).
    

### Task 2: Display the Master Record of User ADM940-##.

Display the master record of user ADM940-##.

#### Steps

1. Are roles assigned to the user? If yes, which ones?
	**ADM940_DEMO_MENU**
	ADM940_DISPLAY
	ADM940_PLUS
	ADM940_USER
2. Is an authorization profile assigned to the user? If yes, which one/s?
	ADM940_DISPLAY
	ADM940_PLUS
	ADM940_USER

### Task 3: Display the Details for an Authorization Profile

#### Steps

1. Display the details for the authorization profile for role ADM940_PLUS.
    
    Hint
    
    Double-click the profile name to go to the detail screen of the authorization profile.
    
    Expand the tree structure of the authorization profile.
    
    Do you have authorizations for the following authorization objects?
    
    - F_BKPF_BUK? No
    
    - PLOG? No
    
    - S_TCODE? Yes
    
    - S_USER_GRP? Yes
    
2. Which authorization fields does the object S_USER_GRP consist of?

	ACTVT Activity

	CLASS User group in user master maintenance

3. Which authorization values do you have for the authorization object S_USER_GRP?

	Authorization combination 1:

	Field 1) ACTVT 05 Field 2) Z*

	Authorization combination 2:

	Field 1) ACTVT 03 Field 2) Class **

### Task 4: Analyze Authorization Objects Using the User Information System

Display various authorization information in the User Information System.

#### Steps

1. Navigate to the User Information System in the SAP Menu.
    
    1. SAP Menu: → _Tools_ → _Administration_ → _User Maintenance_ → _Information System_ folder.
        
2. Select the authorization object S_USER_GRP.
    
    1. Expand the structure for the _Authorization Objects_ node, and select the report _Authorization Objects - By Object Name, Text_ by double-clicking it.
        
    2. Enter **S_USER_GRP** in the _Authorization Object_ field.
        
    3. Choose _Execute (F8)_.
        
    4. Double click Object _S_USER_GRP_.
        
3. To which authorization object class is the authorization object S_USER_GRP assigned?
    
    1. You are in the pop up: _Display Authorization Object_. Which content has the field Class?
		    BC_A
        
4. Display the documentation for this authorization object and find out in which transactions the authorization object is checked, and what activities are possible.
    
    In which transactions is the authorization object checked?
    
    - SU01

	- SU01D

	- SU10

	- SUGR  
	    You can use the CHECK_S_USER_GRD switch in Customizing table PRGN_CUST to switch the authorization check for user group administration to the new authorization object S_USER_GRD system-wide. Administrative operations on user groups are then protected with this new authorization object.  
	    F4 help for users and the assignment of users to a user group in transaction SUGR are still protected by authorization object S_USER_GRP however.

	- PFCG (assignment of users to role)
    
    What activities are possible?
    
    - **01**: Create

	- **02**: Change

	- **03**: Display

	- **05**: Lock, unlock  
    In addition to locking/unlocking a user, the password-related actions (setting a new initial password and reading password data) are also protected with this activity.

	- **06**: Delete

	- **08**: Display change documents
	
	- **22**: Assign users to roles (activity groups)  
	    If authorization object S_USER_SAS is used for role and profile assignments (by default, as of SAP_BASIS Version 7.31), this activity is no longer checked for S_USER_GRP (see SAP Note 536101).
	
	- **24**: Archiving Change Documents  
	    This activity is required in order to be able to archive change documents for users and authorizations. (Transaction SARA for archiving objects US_AUTH, US_PROF, US_USER, or US_PASS)  
	    This is also checked if you reload archived change documents into temporary tables (see SAP Note 1079207, point 2).
	
	- **36**: Extended maintenance  
	    It is used to explicitly protect against changes to non-password-based logon data of users. A check for this activity instead of activity 02 can be activated using the customizing switch CHECK_NONPW_LGNDATA. (See SAP Note 1882254)
	
	- **50**: Move  
	    You can use the Customizing switch CHECK_MOVE_4_CNG_GRP to retain a restriction of the user administrators responsible for creating/changing for one or more user groups.  
	    This activity (50) can be used to transfer users from their own responsibility (user group) to the responsibility of another user administrator (see SAP Note 1663177).
	
	- **78**: Assign  
	    This activity is checked whenever you change group assignments that are not the user group for the authorization check ('Logon Data' tab page).
	
	- **68**: Model:  
	    Model the assignment of systems or roles to users in user administrations, so that you can later derive the actual assignments from this model.  
	    **This activity was only relevant for the Global User Manager and has therefore been obsolete since SAP Note 433941.**
	
	- **PP**: Set productive password  
	    This value is only relevant if used by SAP Identity Management (SAP IDM).
	
	- **F4**: Address data display in input help
5. How many authorization objects have a name that begins with S_USER?
		17

6. Find out about the authorization object S_USER_TCD by displaying the documentation.
	What is controlled with this authorization object
		Authorization objects control the transactions that system administrators can assign to a role, as well as the transactions for which they can assign transaction code authorization (object S_TCODE).  
		Note that in the Profile Generator, you can only maintain intervals of transactions if you have full authorization for S_USER_TCD for authorization object S_TCODE. Otherwise you can only maintain individual values for the object S_TCODE.
	 Which authorization field(s) does the object consist of?
	 TCD

### Task 5: Analyze the Role ADM940_SD_SALES Using the User Information System

#### Steps

1. Navigate to the User Information System in the SAP Menu.
    
    1. SAP Menu: → _Tools_ → _Administration_ → _User Maintenance_ → _Information System_ folder.
        
2. Use Report _Roles by Complex Selection Criteria node_ → _By Role Name_ with the role ADM940_SD_SALES.
    
    1. Expand the structure for the _Roles_ node, then expand the structure for the_Roles by Complex Selection Criteria node_, and choose the report _By Role Name_ by double-clicking it.
        
    2. Enter **ADM940_SD_SALES** in the _Role_ field.
        
    3. Choose _Execute (F8)_.
        
3. Display the transaction assignment for the role.
    
    Do these roles allow you to start transactions that start with "_X_"?
    Yes
	 XD01
	 XD02
	 XD03
	 
    Does this role provide authorization to call transaction VA03?
    
    Yes
    
    Does this role provide authorization to call transaction MM03?
	
	No