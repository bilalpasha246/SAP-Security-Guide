### Task 1: Explaining Traffic Light Colors

Create the role _GR##_RGB_ by copying _ADM940_RGB_ without user assignments and personalization.

#### Steps

1. Start the Role Maintenance transaction and create the role GR##_RGB as a copy of the role ADM940_RGB.
    
    1. **_SAP Menu:_**
        
        **_Tools_ → _Administration_ → _User Maintenance_ → _Role Administration_ → _Roles_**, (transaction code PFCG).
        
    2. Enter the name of the role **ADM940_RGB** in the _Role_ field.
        
    3. Choose _Copy Role (Shift + F11)_.
        
    4. Enter **GR##_RGB** in the _to role_ field.
        
    5. Choose _Copy All (Enter)_.
        
    6. Choose _Change_ on the _Role Maintenance_ screen..
        
1. What traffic light colors are displayed for the authorization objects used?

![[Pasted image 20251015074858.png]]

1. What does a **red** traffic light mean?
    
    _________________________________________________
    
    1. A red traffic light stands for an unfilled organizational level field.
The Profile Generator has written a default value in the field with the field text _Plan Version_. Use the search function to find the authorization field.

Note the field value. Explain the meaning of the first character.

_________________________________________________

1. Open the search option by choosing the _Search_ icon or the menu path _Edit_ → _Find_.
    
2. Enter **plan version** in the "_or field text_" field in the _Find Field_ area.
    
3. Choose _Find Field_.
![[Pasted image 20251015075200.png]]


What does a **Yellow** traffic light mean, and which objects (role GR##_RGB) have this status?
![[Pasted image 20251015075431.png]]

What does the **Green** traffic light color mean, and what do you have to take into account here?

_________________________________________________

_________________________________________________

_________________________________________________

This must be taken into account: ____________________________________

_________________________________________________

_________________________________________________

#### Result

The Green traffic light indicates structures in which all fields are assigned a value. However, it is not possible to identify whether this is:

- An authorization default value
- An organizational level field that received the field value through the maintenance button
- A field for which the authorization default value was changed
- An organizational level field filled directly in the structure (not using the button)

### Task 2: Use Expert Mode to Merge the Existing Authorization Data

While still in the tab _Authorization_, use expert mode to merge the existing authorization data with the authorization default values again.

#### Steps

1. What choice must be made when starting the maintenance so that the Profile Generator reads default values again?
    
    _________________________________________________
    
    _________________________________________________
    
    1. On the _Authorizations_ tab page, choose the _Expert Mode for Profile Generation_ icon. Then, choose the mode _Read old status and merge with new data_.
        
    2. Choose _Back F3_ to go back to the tab _Authorizations_.
        
    3. Choose _Back F3_ to go back to the _Role Maintenance_ screen.
        
2. Start the role maintenance transaction to open the role _GR##_RGB_ and add transaction FD03 to the menu.
    
    1. While still in the Role Maintenance transaction, enter the name for the role **GR##_RGB** in the _Role_ field.
        
    2. Choose the _Change_ icon.
        
    3. Open the _Menu_ tab page.
        
    4. Choose the _Transaction_ button and enter the following transaction code in the _Transaction code_ field:
        
        - FD03
        
    5. Choose _Assign Transactions_.
        
    6. Then choose _Save (Ctrl+S)_ to save your role.
        
3. Read the authorization default values again.
    
    1. Open the _Authorizations_ tab page.
        
    2. Choose _Expert Mode for Profile Generation_ on the _Authorizations_ tab.
        
    3. Select the radio button for the option _Read old status and merge with new data_.
        
    4. Choose _Execute (Enter)_.
        
    5. Choose _Cancel (F12)_ on the _Define Organizational Levels_ window.
        
4. Which object class / authorization objects / has the status _New_?
    
    Object class:
    
    _________________________________________________
    
    Authorization objects:
    
    _________________________________________________
    
    1. Search the authorizations for a line with the entry _New_:
        ![[Pasted image 20251015080339.png]]
        Object class:
        
        - FI
        
    2. Expand the _Object Class FI_ node.
        
        Authorization objects:
        
        - F_KNA1_APP, F_KNA1_BED, F_KNA1_BUK, ...
        
5. Generate the authorization profile for your role.
    
    1. Choose the _Generate_ icon.
        
    2. In the _Generate Profile_ window, choose _Generate_.
        
    3. In the _Assign Profile Name for Generated Authorization Profile_ window, accept the proposed profile name and choose _Execute (Enter)_.
        
    4. Choose _Back (F3)_ to return to the _Change Roles_ screen.
        
6. Delete transaction FD03 in the role menu.
    
    1. Open the _Menu_ tab page.
        
    2. Select the entry _FD03 - Display Customer (Accounting)_ and choose the _Delete Node_ icon.
        
    3. Then choose _Save (Ctrl+S)_ to save your role.
        
7. Read the authorization default values again.
    
    1. Open the _Authorizations_ tab page.
        
    2. Choose _Expert Mode for Profile Generation_ on the _Authorizations_ tab.
        
    3. Select the radio button for the option _Read old status and merge with new data_.
        
    4. Choose _Execute (Enter)_.
        
    5. Choose _Cancel (F12)_on the _Define Organizational Levels_ window.
        
    
    #### Result
    
    The removed authorization values are shown in the _Deleted Authorizations and Values (Merge)_ area.
    
8. Generate the authorization profile for your role.
    
    1. Choose the _Generate_ icon.
        
    2. In the _Generate Profile_ window, choose _Generate_.
        
    3. In the _Assign Profile Name for Generated Authorization Profile_ window, accept the proposed profile name and choose _Execute (Enter)_.
        
    4. Choose _Back (F3)_ ,to return to the _Change Roles_ screen.
        
9. Complete the maintenance of this role and return to the initial screen of transaction PFCG.
    
    1. Choose _Back (F3)_ to return to the initial screen of the _Role Maintenance_.

### Task 3: Use Mass Maintenance of Authorization Values in Roles

Add further values for the field company code in the previously created roles _GR##_*_. Use the mass maintenance of authorization values in roles.

#### Steps

1. Start transaction PFCGMASSVAL.
    
    1. In the _OK code_ field, enter the transaction code PFCGMASSVAL.
        
2. Add the values 90FR, 90CA , and 90US to the values of the field company code.
    
    1. Enter **GR##_*** in the_Roles_ field.
        
    2. Select _Execute with prior simulation_ in the _Standard Selection_ area.
        
    3. Select _Change Organizational Levels_ in the _Type of field change_ area.
        
    4. In the _Change_ field, enter _Add_.
        
    5. In the _Organizational Level_ field, enter _BUKRS_.
        
    6. Choose the _Values_ button, and enter the values , _90FR_, _90CA_ and _90US_.
        
    7. Choose _Transfer (Enter)_.
        
3. Start the mass maintenance.
    
    1. Choose_Execute (F8)_.
        
        A list is displayed which shows a simulation of the respective changes.
        
        Then choose_Execute (F8)_ to perform the changes.
        
        #### Result
        
        Now the values are added to the field company code in the roles _GR##_*_ .