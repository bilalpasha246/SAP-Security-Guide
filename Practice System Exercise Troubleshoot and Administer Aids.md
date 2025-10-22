### Business Example

During your daily work as an administrator, you will regularly search for special settings, authorization values, roles, and other important things. You can find these in the user information system.

### Task 1: Compare the Settings of the Authorizations Between Two Users

You are authorization administrator and are in the consolidation phase after the start of production.

#### Steps

1. Compare the settings of the authorizations between user _GR##-ADM_ and user _GR##-FI1_.
    
    Are there differences?
    ![[Pasted image 20251015132212.png]]

1. Find out which users may execute transaction MB1C.
    
    1. Navigate to the User Information System in the SAP Menu.
        
        SAP Menu: → _Tools_ → _Administration_ → _User Maintenance_ → _Information System_
        
    2. Expand the structure for the _User_ → _Users by Complex Selection Criteria_ node, and select the report _- By Authorization Values_ by double-clicking it.
        
    3. Enter **S_TCODE** in the _Authorization Object_ field.
        
    4. Choose _Input Values_.
        
    5. Enter **MB1C** in the _Value_ field.
        
    6. Choose _Execute (F8)_.
        
    
    #### Result
    
    The resulting list shows the users who may execute transaction MB1C.
![[Pasted image 20251015132602.png]]

![[Pasted image 20251015132743.png]]
