### Task 1: Create a Composite Role

Create the composite role GR##_MM_WHOUSE.

Hint

Ensure that you use the _Create Comp. Role_ button on the initial screen of Role Maintenance.

#### Steps

1. Start the Role Maintenance transaction and create the predefined role. Enter a short description, and save.
    
    If you look at the tab pages, what do you notice?
    
    ___________________________________________________________
    
    ___________________________________________________________
    
    1. **_SAP Menu:_**
        
        **_Tools_ → _Administration_ → _User Maintenance_ → _Role Administration_ → _Roles_** (transaction code PFCG).
        
    2. Enter the name for the role **GR##_MM_WHOUSE** in the _Role_ field.
        
    3. Choose _Create Comp. Role_.
        
    4. Enter description **Composite role Warehouse** in the _Description_ field.
        
    5. Then choose_Save (Ctrl+S)_ to save your role.
        
    6. Check the tab pages, what do you notice?
        
        The tab page _Roles_ has been added.
        
        The tab page _Authorizations_ has been removed.
        
2. Add single roles to your composite role.
    
    Your composite role should consist of the roles of the role definition in the sample authorization concept for the work center _Warehouse_.
    
    In accordance with the sample authorization concept, these are:
    
    - GR##_MM_MAT_ANZ
    
    - GR##_MM_IM_POST
    
    Enter these in the relevant fields.
    
    1. Go to the _Roles_ tab page.
        
    2. Enter the following role names in the _Role_ column:
        
        - GR##_MM_MAT_ANZ
        
        - GR##_MM_IM_POST
        
    3. Then choose _Save (Ctrl+S)_ to save your role.
        
3. Read the menus of the inserted roles into your composite role.
    
    You can choose to make further modifications to the menu of the composite role. (Do not delete any entries. However, you can move or rename them).
    
    1. Go to the _Menu_ tab page, and choose _Import Menu_.
        
    2. Then choose_Save (Ctrl+S)_ to save your role.
        
4. Assign user GR##-MM1 and save your user assignment.
    
    1. Go to the _User_ tab page
        
    2. Enter **GR##-MM1** in the _User ID_ field.
        
    3. Then choose_Save (Ctrl+S)_ to save your role.
        
5. Perform a user master comparison.
    
    1. Choose the _User comparison_ button to enter the roles in the master record of user GR##-MM1.
        
6. Complete the maintenance of this role and return to the initial screen of transaction PFCG.
    
    1. Choose _Back (F3)_ to return to the initial screen of _Role Maintenance_.

### Task 2: Describe the Options for a User Master Comparison

#### Steps

1. Where can you perform a user master comparison? List at least two possibilities.
    
	- Transactions SU01, PFCG and PFUD
	- PFCG_Time_Dependancy
    
    1. With additional steps in transactions: SU01, PFCG, and PFUD or with the report "_pfcg_time_dependency_".
        
2. What does the report _pfcg_time_dependency_ do?
    
    1. You can schedule an automatic user master comparison at regular intervals with this report. This compares all links and relationships between roles, users, and profiles in the master records (in the background).

### Task 3: Display the User Master Record of user GR##-MM1

Display the user master record of user GR##-MM1.

#### Steps

1. Start the User Maintenance transaction and answer the following questions.
    
    **If your user GR##-MM1 does not yet have the role ADM940_PLUS, assign the role and perform a user master comparison.**
    
    Which roles is the user assigned?
	![[Pasted image 20251015071908.png]]
    
    Display the authorization profiles. How many profiles are assigned?
    ![[Pasted image 20251015071949.png]]
    ________________________ authorization profiles
    
    Why are there fewer profiles than roles?
    
    _______________________________________________
    
    1. **_SAP Menu:_**
        
        **→ _Tools_ → _Administration_ → _User Maintenance_ → _Users_**, (transaction code SU01).
        
    2. Enter the user name **GR##-MM1** in the _User_ field.
        
    3. Choose the _Display_ icon.
        
    4. Go to the _Roles_ tab page.
        
        You will find the following roles on the _Roles_ tab page.
        
        - ADM940_PLUS
            
        - GR##_BC_PORTALS
            
        - GR##_MM_IM_POST
            
        - GR##_MM_MAT_ANZ
            
        - GR##_MM_WHOUSE
            
        
    5. Go to the _Profiles_ tab page.
        
        Display the authorization profiles. How many profiles are assigned?
        
        - 4 authorization profiles
        
        Why are there fewer profiles than roles?
        
        - Because the composite role does not have its own profile.
        
    1. Choose _Back (F3)_ to return to the _User Maintenance: Initial Screen_ .

### Task 5: Create a **Derived** Role

Create a **derived** role GR##_MM_IM_POST1010 with authorizations for a warehouse supervisor in plant _1010_.

#### Steps

1. Create a **derived** role GR##_MM_IM_POST1010 . Assign the imparting role GR##_MM_IM_POST and save your role.
    
    Display the inheritance hierarchy of the roles (choose _Ctrl+Shift+F3_ or the _Inheritance Hierarchy_ icon).
    
    1. Start the role maintenance transaction:
        
        _SAP Menu:_**_Tools_ → _Administration_ → _User Maintenance_ → _Role Administration_ → _Roles_**, (transaction code: PFCG).
        
    2. Enter the name for the role **GR##_MM_IM_POST1010** in the _Role_ field.
        
    3. Choose _Create Single Role_.
        
    4. Enter description **Warehouse supervisor in plant 1010** in the _Description_ field.
        
    5. Enter **GR##_MM_IM_POST** in the _Derive from Role_ field.
        
    6. Then choose_Save (Ctrl+S)_ to save your role.
        
2. Display the inheritance hierarchy of the roles.
    
    1. _Menu:_ → _Role_ → _Inheritance (Ctrl+Shift+F3)_
        
    2. Select role _GR##_MM_IM_POST1010_ and choose _Choose (F2)_.
        
3. Can you add other applications (menu entries, transaction codes, and reports, for example) or delete existing applications?

	![[Pasted image 20251015072543.png]]
    
    1. Go to the _Menu_ tab page.
        
        No, since the menu of role GR##_MM_IM_POST is inherited from the role GR##_MM_IM_POST1010.
        
4. Maintain Authorizations - Define the organizational levels.
    
    Plant: _1010_
    
    Did the system copy the authorizations of the imparting role?
    
    _________________________
    
    1. Go to the the _Authorizations_ tab page.
        
    2. Choose _Change Authorization Data_.
        
    3. Enter the following values in the _Define Organizational Levels_ window:
        
        - _Plant_: **1010**,
        
    4. Choose _Save (Ctrl+S)_ to save the authorization values for the organizational levels.
        
        Did the system copy the authorizations of the imparting role?
        
        No, they must either be maintained here directly or copied as described in the next exercise task.
        
    5. Choose _Save (Ctrl+S)_ to save the profile values .
        
    6. In the _Assign Profile Name for Generated Authorization Profile_ window, accept the proposed profile name and choose _Execute (Enter)_.
        
5. Maintain Authorizations - Copy the authorization data from the imparting role.
    
    1. Choose _Copy data (Ctrl+Shift+F7)_.
        
    2. Choose _Continue (Enter)_ to save the profile values .
        
        The authorizations are then copied from the _imparting role_ (reference role).
        
    3. Choose _Save (Ctrl+S)_ to save the profile values .
        
    4. Choose _Organizational levels_ to check the value for the organizational level plant.
        
        The plants _1000_, _1010_, and _1020_ were **not** copied from the reference since this is an organizational level field which was previously set in the derived role.
        
    5. Choose _Save (CTRL+S)_ to save the authorization values for the organizational levels.
        
6. Maintain Authorizations - Generate the authorization profile for your role.
    
    1. Choose the _Generate_ icon.
        
    2. In the _Assign Profile Name for Generated Authorization Profile_ window, accept the proposed profile name and choose _Execute (Enter)_.
        
    3. Choose _Back (F3)_ to return to the _Change Roles_ screen.
        
    4. Choose _Back (F3)_ to return to the initial screen of the _Role Maintenance_.