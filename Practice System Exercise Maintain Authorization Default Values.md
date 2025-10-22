### Task 1: Display the Authorization Default Values

Display the authorization default values for transaction FD03.

#### Steps

1. Start the _Maintain Authorization Default Values_ transaction (SU24).
    
    1. In the _OK code_ field, enter transaction code SU24.
        
        Note
        
        You can also start the _Maintain Authorization Default Values_ transaction in the SAP Reference Implementation Guide (SPRO):
        
        - SAP Menu: _Tools_ → _Customizing_ → _IMG_ → _Execute Project_, (transaction code: SPRO).
        
        _- IMG path: SAP Customizing Implementation Guide_ → _SAP NetWeaver_ → _Application Server_ → _System Administration_ → _Users and Authorizations_ → _Maintain Authorizations and Profiles Using Profile Generator_ → _Work on SAP Check Indicators and Field Values_.
        
        - Choose _Change Check Indicators_.
        
2. Display the authorization default values for transaction FD03 and check the following:
    
    Are there any authorization objects with the default status
    
    - _Yes_
    
    - _Yes, Without Values_
    
    - _No_
    
    ____________________
    
    To which authorization objects is the default status "_Yes_" assigned?
    
    __________________________________________________________
    
    1. Enter **FD03** in the_Transaction Code_ field.
        
    2. Choose _Execute (F8)_.
        
    
    #### Result
    
    There are authorization objects with the default status _Yes_and _Yes, Without Values_ shown.
    
    The default status "_Yes_" is assigned to the following authorization objects:
    ![[Pasted image 20251015083308.png]]
    - B_BUPA_RLT
    
    - F_KNA1_APP
    
    - F_KNA1_BED
    
    - F_KNA1_BUK
    
    - F_KNA1_GEN
    
    - F_KNA1_GRP
    
    - F_MANDATE

Which default values are assigned to the authorization fields of the authorization object _F_KNA1_APP_ → _?_

Fill in the following table.

| Object     | Field | Value (Interval) |
| ---------- | ----- | ---------------- |
| F_KNA1_BUK |       |                  |
|            |       |                  |
|            |       |                  |
|            |       |                  |
|            |       |                  |

1. The authorization default values are listed in the _Authorization Default Values_ area.
    ![[Pasted image 20251015083446.png]]
2. Check the entries in the line with authorization object _F_KNA1_APP_.


### Task 2: Compare the Automatically Entered Authorizations in a Role with Authorization Default Values

Create a role GR##_FI_FD03 and compare the automatically entered authorizations with the authorization default values from the previous task.

#### Steps

1. Start the role maintenance transaction and create the predefined role. Enter a short description, and save.
    
    1. **_SAP Menu:_**
        
        **_Tools_ → _Administration_ → _User Maintenance_ → _Role Administration_ → _Roles_** (transaction code PFCG).
        
    2. Enter the name for the role **GR##_FI_FD03** in the _Role_ field.
        
    3. Choose _Create Single Role_.
        
    4. Enter description **Check authorization default values** in the _Description_ field.
        
    5. Then choose _Save (Ctrl+S)_ to save your role.
        
2. Add the transaction FD03 to the role menu.
    
    1. Go to the _Menu_ tab page.
        
    2. Choose the _Transaction_ button and enter the following transaction code in the _Transaction code_ field:
        
        - FD03
        
    3. Choose _Assign Transactions_.
        
    4. Then choose _Save (Ctrl+S)_ to save your role.
        
3. Go to the Authorizations tab page and define the organizational levels.
    
    Define the organizational level:
    
    - Organizational level: _Company Code_= _1010_
    
    Why do you have to enter an authorization value for the company code?
    
    __________________________________________________________
    
    1. Go to the _Authorizations_ tab page.
        
    2. Choose _Change Authorization Data_.
        
    3. Enter the following values in the _Define Organizational Levels_ window:
        
        - _Company code_: **1010**,
        
    4. Why do you have to enter an authorization value for the company code?
        
        The field _company code_ has been created as an organizational level.
        
    5. Choose _Save (Ctrl+S)_ to save the authorization values for the organizational levels.
        
4. Answer the following questions.
    
    For which authorization objects did the system automatically generate authorizations?
    
	![[Pasted image 20251015083933.png]]

    Why is the status of the authorization objects F_KNA1_APP, F_KNA1_BUK, and F_KNA1_GEN set to _Standard_ and why is the traffic light symbol status set to _green_?
    
    __________________________________________________________
    
    __________________________________________________________
    
    __________________________________________________________