### Task 1: Display the Definition of a Transaction

Display the definition of transaction FB03.

#### Steps

1. Start the transaction MAINTAIN TRANSACTION (SE93).
    
    1. Choose **Menu path:**_SAP Menu_ → _Tools_ → _ABAP Workbench_ → _Development_ → _Other Tools_ → _Transactions_ (SE93).
        
    2. Enter **FB03** in the _Transaction Code_ field.
        
    3. Choose _Display_.
        
2. Which authorization object is checked when the transaction is called?
    
    Authorization object: F_BKPF_BUK

3. Which authorization values must exist for the authorization check to be positive and the transaction to be started?
		03
4. Find out which object was checked, and what authorizations you have. Use transaction SU53 to find out which object was checked, and what authorizations you have.
		SESS, SESSION_MANAGER, SMEN, SSC1, SU3, SU53, SU56

### Task 3: Analyze Authorization in the User Buffer

Describe the user buffer and display it for user "ADM940-SU53".

#### Steps

1. What do you see in the user buffer? Describe its content.
	 The authorization data for different object classes with different fields and activities based on the role name, transaction codes and objects for sending
2. How can you call the user buffer?
    1. With transaction SU56.
3. Display the buffer for your user "ADM940-SU53". How many authorization entries does this user have?
	1. S_TCODE
	2. S_USER_AGR
	3. S_USER_AUT
	4. S_USER_GRP
	5. S_DEVELOP
	6. S_OC_SEND