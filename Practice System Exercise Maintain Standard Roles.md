### Task 1: Create a Role to Display a Material Master

Create a role GR##_MM_MAT_ANZ to display a material master.

#### Steps

1. Start the Role Maintenance transaction and create the predefined role. Enter a short description, and save.
    
    1. **_SAP Menu:_**
        
        **_Tools_ → _Administration_ → _User Maintenance_ → _Role Administration_ → _Roles_**, (transaction code PFCG).
        
    2. Enter the name for the role **GR##_MM_MAT_ANZ** in the _Role_ field.
        
    3. Choose _Create Single Role_.
        
    4. Under the Role Name, in the field _Description_enter: **Display a material master** .
        
    5. Then choose _Save (CTRL+S)_ to save your role.
        
2. Add the corresponding transactions in accordance with the sample authorization concept (**Roles for Transaction Codes** table from the prerequisites of this exercise).
    
    A brief extract from the table in the prerequisites is provided here to make the task more comprehensible.
    
    |Name of the Role|Transactions for this Role|
    |---|---|
    |GR##_MM_MAT_ANZ|MM03, MM04, MM19|
    
    1. Go to the _Menu_ tab page.
        
    2. Choose the _Transaction_ button and enter the following transaction codes in the _Transaction code_ field:
        
        MM03
        
        MM04
        
        MM19
        
    3. Choose _Assign Transactions_.
        
    4. Then choose _Save (CTRL+S)_ to save your role.
        
3. Create a folder with the name **WWW Links** and add a Web address with the name SAP and the URL http://www.sap.com to this folder.
    
    1. Choose the _Create Folder_ button.
        
    2. Enter **WWW Links** in the _Folder Name_ field:
        
    3. Choose _Continue (Enter)_.
        
    4. Next to the button _Transaction_, use the black triangle to choose _Other_ → _Web address or file_ in the context menu of the _Transaction_ button.
        
    5. Enter the description **SAP.com** in the _Text_ field.
        
    6. Enter the URL**https://www.sap.com** in the _Web address or file_ field.
        
    7. Choose _Copy (Enter)_.
        
    8. Then choose _Save (CTRL+S)_ to save your role.
        
4. Maintain Authorizations - Maintain authorization values for the organizational levels.
    
    1. Go to the _Authorizations_ tab page.
        
    2. Choose _Change Authorization Data_.
        
    3. Enter the following values in the _Define Organizational Levels_ window:
        
        When you maintain organizational levels, you usually only see those lines where values have been assigned. If an organizational level field has not yet been maintained, only one line is displayed. You can display multiple lines by choosing the _More Values_ button.
        
        - _Company code_: **1010**,
        
        - _Warehouse number/complex_: *****,
        
        - _Sales organization_: **1010**,
        
        - _Distribution Channel_: *****,
        
        - _Plant_: **1000, 1010, 1020**.
        
    4. Choose _Save (CTRL+S)_ to save the authorization values for the organizational levels.
        
5. Maintain Authorizations - Check the traffic light symbol status.
    
    For which authorization object class are all authorization field contents maintained?
    
    Authorization object class:
	 ![[Pasted image 20251014185255.png]]
	 
    _________________________________________________
    
    For which authorization objects of the object class MM_G do you have to supply authorization values?
    
    Authorization Objects:
    
    ![[Pasted image 20251014185235.png]]_
    _________________________________________________
    
    1. Check the _Group/object/Authorization Field_ column for authorization object class where all authorization field contents are maintained.
        
        Object class: AAAB, Cross-application Authorization Objects
        
    2. Check the _Group/object/Authorization Field_ column for authorization objects of the object class MM_G with a yellow traffic light.
        
        Authorization objects whose authorization field values are not completely maintained are flagged with a yellow traffic light.
        
        The following authorization objects are not completely maintained:
        
        - M_MATE_MAR
        - M_MATE_MAT
        - M_MATE_STA
        - M_MATE_WGR
        
6. Maintain Authorizations - Set the authorization for the maintenance status in the authorization object M_MATE_STA to full authorization.
    
    What is the status of the authorization after your change?
    
    _________________________________________________
    
    1. Expand _Authorization Object M_MATE_STA_.
        
    2. In the context menu (click the right-mouse button) of the _STATM_ field and choose _Set field Values to '*''_.
        
        Status: _Maintained_, traffic light: _Green_.
        
7. Maintain Authorizations - Set all open authorization values to full authorization.
    
    Set all open authorization values to full authorization (top set of traffic lights).
    
    What happens to the traffic light symbol for object class MM_G after you have assigned values to all open fields?
    
    _________________________________________________
    
    1. Choose the _Status_ button.
        
    2. Choose _Execute (Enter)_in the _Assign Full Authorization of Subtree_ window.
        
        The traffic light symbol for object class MM_G then switches the structure to _Green_.
        
8. Maintain Authorizations - Generate the authorization profile for your role.
    
    1. Choose the _Generate_ icon.
        
    2. In the _Assign Profile Name for Generated Authorization Profile_ window, accept the proposed profile name and choose _Execute (Enter)_.
        
    3. Choose _Back (F3)_ to return to the _Change Roles_ screen.
        
9. Check the status of your authorization profile in the information section of the _Authorizations_ tab and complete the maintenance of this role and return to the initial screen of transaction PFCG.
    
    What is the status of your authorization profile?
    
    ![[Pasted image 20251014190310.png]]
    
    1. Check the _Status_ field on the _Authorizations_tab
        
        Status: _Authorization profile is current_.
        
    1. Choose _Back (F3)_ to return to the initial screen of _Role Maintenance_.

### Task 2: Create a Role with Authorizations for a Warehouse Supervisor

Create a role GR##_MM_IM_POST with authorizations for a warehouse supervisor.

#### Steps

1. Start the role maintenance transaction and create the predefined role. Enter a short description, and save.
    
    1. **_SAP Menu:_**
        
        **_Tools_ → _Administration_ → _User Maintenance_ → _Role Administration_ → _Roles_**, (transaction code PFCG).
        
    2. Enter the name for the role **GR##_MM_IM_POST** in the _Role_ field.
        
    3. Choose _Create Single Role_.
        
    4. Under the Role Name, in the field _Description_enter **Warehouse supervisor**.
        
    5. Then choose _Save (CTRL+S)_ to save your role.
        
2. Add the corresponding transactions in accordance with the sample authorization concept (**Roles for Transaction Codes** table from the prerequisites of this exercise).
    
    1. Go to the _Menu_ tab page.
        
    2. Choose the _Transaction_ button and enter the following transaction codes in the _Transaction code_ field:
        
        MB1C
        
        MB90
        
        VL21
        
    3. Choose _Assign Transactions_.
        
    4. Then choose _Save (CTRL+S)_ to save your role.
        
3. Maintain Authorizations - Maintain authorization values for the organizational levels.
    
    1. Go to the the _Authorizations_ tab page.
        
    2. Choose _Change Authorization Data_.
        
    3. Enter the following values in the _Define Organizational Levels_ window:
        
        When you maintain organizational levels, you usually only see those lines where values have been assigned. If an organizational level field has not yet been maintained, only one line is displayed. You can display multiple lines by choosing the _More Values_ button.
        
        - _Shipping Point_: *****,
        
        - _Plant_: **1000, 1010, 1020**.
        
    4. Choose _Save (CTRL+S)_ to save the authorization values for the organizational levels.
        
4. Maintain Authorizations - Add the authorization values 561 and 562 to the authorization values for the _Movement Type_ field of the authorization object M_MSEG_BWA.
    
    1. Expand _Object Class MM_B_.
        
    2. Expand _Authorization Object M_MSEG_BWA_.
        
    3. Expand Authorization _Authorizat. 00_.
        
    4. Choose the _Pencil_ button on the right side of the _BWART_ field.
        
    5. Enter **561** and **562** in the _Field values_ window.
        
    6. Choose _Transfer (Enter)_.
        
5. Maintain Authorizations - Set all open authorization values to full authorization.
    
    1. Choose the _Status_ button.
        
    2. Choose _Execute (Enter)_in the _Assign Full Authorization of Subtree_ window.
        
6. Maintain Authorizations - Generate the authorization profile for your role.
    
    1. Choose the _Generate_ icon.
        
    2. In the _Assign Profile Name for Generated Authorization Profile_ window, accept the proposed profile name and choose _Execute (Enter)_.
        
    3. Choose _Back (F3)_ to return to the _Change Roles_ screen.
        
7. Complete the maintenance of this role and return to the initial screen of transaction PFCG.
    
    1. Choose _Back (F3)_ to return to the initial screen of the _Role Maintenance_.

![[Pasted image 20251014202915.png]]

### Task 4: Create a Role and Assign it to All Users

Create a role GR##_BC_PORTALS. The content of the role should be copied by choosing **From Other Role** on the "Menu" tab page. This role should then be assigned to all "GR##*" users and contain functions of general interest.

#### Steps

1. Start the role maintenance transaction and create the predefined role. Enter a short description, and save.
    
    1. While still in the Role Maintenance transaction, enter the name for the role **GR##_BC_PORTALS** in the _Role_ field.
        
    2. Choose _Create Single Role_.
        
    3. Under the Role Name, in the field _Description_enter **General role for communication, workflow, and so on**.
        
    4. Then choose _Save (Ctrl+S)_ to save your role.
        
2. Go to the Menu tab page and copy the menu from the predefined role SAP_BC_SRV_USER by selecting all transactions.
    
    1. Go to the _Menu_ tab page.
        
    2. Choose _From Menus_ → _From Anther Role_ → _Local_.
        
    3. Enter **SAP_BC_SRV_USER** in the _Single Role_ field.
        
    4. Choose _Start Search_.
        
    5. Choose _Copy_.
        
    6. Select all items and choose _Add_.
        
    7. Then choose _Save (Ctrl+S)_ to save your role.
        
3. Maintain Authorizations - Set all open authorization values to full authorization.
    
    1. Go to the _Authorizations_ tab page.
        
    2. Choose _Change Authorization Data_.
        
    3. Choose the _Status_ button.
        
    4. Choose _Execute (Enter)_ in the _Assign Full Authorization of Subtree_ window.
        
4. Maintain Authorizations - Generate the authorization profile for your role.
    
    1. Choose the _Generate_ icon.
        
    2. In the _Assign Profile Name for Generated Authorization Profile_ window, accept the proposed profile name and choose _Execute (Enter)_.
        
    3. Choose _Back (F3)_ to return to the _Change Roles_ screen.
        
5. Assign the role to all users.
    
    What is the status of the _User_ tab page?
    ![[Pasted image 20251015070717.png]]
    
    Assign your role to all users that you have created with the user name "GR##*", with your group ID (the users GR##-FI1, GR##-FI2, GR##-SD1, GR##-SD2, GR##-MM1, GR##-MM2 should exist with the user group ZGR##, from another lesson of the SAP course ADM940).
    
    Check the settings for the user comparison (menu: _Utilities_ → _User Settings_). Ensure that a user master adjustment (record comparison) is automatically performed when you save.
    
    1. Check the status of the _User_ tab page.
        
        The _User_ tab page is "red", which means that no users have yet been assigned to this role.
        
    2. Go to the _User_ tab page.
        
    3. Assign the following users by entering the names into the _User ID_ column.
        
        |User name|
        |---|
        |GR##-FI1|
        |GR##-FI2|
        |GR##-SD1|
        |GR##-SD2|
        |GR##-MM1|
        |GR##-MM2|
        
6. Save your role and perform a user comparison
    
    What happens to the status of the "User" tab after you have saved.
    ![[Pasted image 20251015070742.png]]
    
    1. Choose _Save (Crtl+S)_
        
        The status display of the tab page is yellow.
        
    2. Choose _User Comparison_.
        
        The user comparison enters the generated profiles for a role (if the validity period includes today's date), and the role itself, in the user master record.
        
    3. Choose _Full Comparison_ on the _Compare Role User Master Record_ window.
        
        The _Status_ field indicates: _Comparison of user master record completed_.
        
    4. Choose _Cancel (F12)_ on the _Compare Role User Master Record_ window.
        
        You can activate automatic user adjustment when saving a role by choosing _Utilities_ → _User Settings_ and selecting the appropriate checkbox (_Automatic User Adjustment when Saving Role_).
        
        The status display of the tab page is green.
        
    5. Choose _Back (F3)_ to return to the _Role Maintenance_ screen.
        
7. Assign the role _ADM940_PLUS_ to all of your users ("GR##-*").
    
    Save your user assignments, and perform a master record comparison.
    
    Hint
    
    With this exercise, it is possible that participants lock each other when saving the settings. If this happens, wait a moment and try again. After the comparison, exit the transaction PFCG.
    
    1. While still in the Role Maintenance transaction, enter the name for the role: **ADM940_PLUS** in the _Role_ field.
        
    2. Choose the _Change_ icon.
        
    3. Go to the _User_ tab page.
        
    4. Assign the following users by entering the names into the _User ID_ column.
        
        |User name|
        |---|
        |GR##-FI1|
        |GR##-FI2|
        |GR##-SD1|
        |GR##-SD2|
        |GR##-MM1|
        |GR##-MM2|
        
    5. Choose _User Comparison_.
        
    6. Choose _Yes_ on the _Save the role_ window.
        
    7. Choose _Full Comparison_ on the _Compare Role User Master Record_ window.
        
    8. Choose _Cancel (F12)_ on the _Compare Role User Master Record_ window.
        
    9. Choose _Back (F3)_ to return to the _Role Maintenance_ screen.