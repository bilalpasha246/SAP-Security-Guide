### Business Example

Almost all companies use PCs and software programs to support their employees in their daily work. However, to work with this technology, the users require access and authorizations to call the programs. A control method in an SAP system is the user master record and its roles and profiles.

### Task 1: Create a user group

Create a new user group ZGR## with a description of your choice.

### Task 2: Create a User Master Record

Create a user master record for a dialog user GR##-ADM.

#### Steps

1. Start transaction _User Maintenance_ (SU01).
    
    1. Choose **_SAP Menu:_ **→ _Tools_ → _Administration_ → _User Maintenance_ → _Users_**, (transaction code SU01).**
        
    2. Enter **GR##-ADM** in the _User_ field and choose _Create (F8)_.
        
    3. Select the_Address_ tab page.
        
        Enter **Admuser##** in the _Last name_ field.
        
        Enter your choice of data in the other fields.
        
    4. Select the_Documentation_ tab page.
        
        Enter **User for Group ##** in the _Description_ field.
        
        Enter **ADM940-##** in the _Person Responsible_ field.
1. Enter an initial password of your choice and assign the user to user group ZGR##.
    
    Initial password: Init1234
    
    2. Select the_Logon Data_ tab page.
        
        Enter **Init1234** in the _New Password_ and the _Repeat Password_ field.
        
        Enter **ZGR##** in the _User group_ field.

1. Assign the log-on language that you have used yourself for logging on.
    
    1. Select the_Defaults_ tab page.
        
        Enter the log-on language of your choice in the _Logon Language_ field.
        
2. Save your user master record.
    
    1. Choose _Save (Ctrl+S)_.
        
    2. Go back to the _SAP Easy Access_ menu.

### Task 3: Assign a Predefined Role to Your New User Master Record

Assign a predefined role _ADM940_BC_ADMIN_ to your new user master record.

#### Steps

1. Start transaction _User Maintenance_ (SU01).
    
    1. Choose **_SAP Menu:_ **→ _Tools_ → _Administration_ → _User Maintenance_ → _Users_**, (transaction code SU01).**
        
    2. Enter **GR##-ADM** in the _User_ field and choose _Change (Shift+F6)_.
        
    3. Select the_Roles_ tab page.
        
    4. On the _Roles_ tab, enter **ADM940_BC_ADMIN** in the _Role_ column and press Enter.
        
2. Save your user master record.
    
    1. Choose _Save (Ctrl+S)_.
        
    2. Go back to the _SAP Easy Access_ menu.

### Task 4: Check the User Master Record

Check the user master record of your user GR##-ADM.

#### Steps

1. Check whether a role is assigned to your user GR##-ADM.
    
    Assigned role:
    
    ADM940_BC_ADMIN
    
Link your user with another role. Choose the role ADM940_PLUS.
Are authorization profiles assigned to your user?

Which authorization profile(s)?

___________Profile for role ADM940_BC_ADMIN________;

Profile for role ADM940_PLUS___________________.

### Task 5: Display the Change Documents for a User

Display the change documents for your user GR##-ADM by calling up the information system for users and authorizations and selecting the report _For Users_ under _Change Documents_ for users and authorizations.

#### Steps

1. Display the change documents for your user GR##-ADM by calling up the information system for users and authorizations and selecting the report _For Users_ under _Change Documents_ for users and authorizations.


### Task 6: Log On to the System with the Credentials of the Created User

Try to log on to the system as user GR##-ADM without _Language_ information.

#### Steps

1. Start _SAP Logon_ and log on to the system as user GR##-ADM.
    
    1. Start _SAP Logon_.
        
    2. Select system _T41_ and choose _Log On_.
        
    3. Enter **GR##-ADM** in the _User_ field.
        
    4. Enter the initial password **Init1234** in the _Password_ field.
        
    5. Leave the _Language_ field empty.
        
    6. Choose _Enter_.
        
    7. Enter a password of your choice, for example **Welcome1** in the _New Password_ and the _Repeat Password_ fields.
        
    8. Choose _Transfer (Enter)_.
        
    9. Choose _Continue (Enter)_.
        
2. Do you need to enter a log-on language?
    
    _NO___________________

Check the user menu (Ctrl+F10):

If you want to see the transaction codes in the user menu, select on the top menu _Extras_ → _Settings_ and select _Display Technical Name_.

Which functions does it contain? List some examples.

______________________________________________

![[Pasted image 20251014182454.png]]

Check the user buffer by calling the _Analyze User Buffer_ transaction.

How many authorizations exist?

____________________

For which authorization objects? List some examples.

______________________________________________

![[Pasted image 20251014182735.png]]
### Task 7: Create Users Using the User Mass Maintenance Transaction

Create additional user master records using the _User Mass Maintenance_ transaction.

#### Steps

1. Start the _User Mass Maintenance_ transaction.
    
    1. **_SAP Menu:_**
        
        **→ _Tools_ → _Administration_ → _User Maintenance_ → _User Mass Maintenance_**, (transaction code SU10).
        
2. Create the following six user names.
    
    |User Name|
    |---|
    |GR##-FI1|
    |GR##-FI2|
    |GR##-SD1|
    |GR##-SD2|
    |GR##-MM1|
    |GR##-MM2|
    
    1. In the _User_ column, enter the user names listed in the table and choose the _Create (F8)_ icon.
        
3. Assign the user group ZGR## to all users.
    
    1. Select the_Logon Data_ tab page.
        
        Enter **ZGR##** in the _User group_ field.
        
4. Assign the log-on language that you have used yourself for logging on.
    
    1. Select the_Defaults_ tab page.
        
        Enter the log-on language of your choice in the _Logon Language_ field.
        
5. Save your user master record.
    
    1. Choose _Save (Ctrl+S)_ to save your result and to create the users.
        
6. Check the result in the change log for a given user entry.
    
    You can copy the generated initial passwords into the tables in the exercise section.
![[Pasted image 20251014183216.png]]

  Logon
  data for user GR08-FI1 changed
 
 
  The password was changed
 
 
  Generated password for user
  GR08-FI1: +kd9~aAbK]4JN~]]#tZE{lVk6WlBNt(6~A}hYB]=
 
 
  User GR08-FI1 created
 
 
  Logon data for user GR08-FI2
  changed
 
 
  The password was changed
 
 
  Generated password for user
  GR08-FI2: t5Zy3${WUB#W-eQnrv]&uu\hgU3&Apj%$5~~]Dy4
 
 
  User GR08-FI2 created
 
 
  Logon data for user GR08-MM1
  changed
 
 
  The password was changed
 
 
  Generated password for user
  GR08-MM1: W[>MkN=gXu%=R2F22@7(vrnDMaKSeHXx\ySY3(>c
 
 
  User GR08-MM1 created
 
 
  Logon data for user GR08-MM2
  changed
 
 
  The password was changed
 
 
  Generated password for user
  GR08-MM2: bL&%9M}>w{wdDcz9B#cv&tJ9a5JlHQ%EYPE\7rCo
 
 
  User GR08-MM2 created
 
 
  Logon data for user GR08-SD1
  changed
 
 
  The password was changed
 
 
  Generated password for user
  GR08-SD1: 8WtnhmgQ7cpg$e%6)S6=f92L5Bq$J8ZwFEZZpdj]
 
 
  User GR08-SD1 created
 
 
  Logon data for user GR08-SD2
  changed
 
 
  The password was changed
 
 
  Generated password for user
  GR08-SD2: 4H(rT4CVRQwv9UB%>m-QT(u#{fr\fgpnB75J62H}
 
 
  User GR08-SD2 created
 



