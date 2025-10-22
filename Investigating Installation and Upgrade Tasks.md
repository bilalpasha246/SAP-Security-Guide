
Activating Role Maintenance after a **new installation** requires two steps.
### Required Steps for Operating Role Maintenance

- The SAP system profile parameter _auth/no_check_in_some_cases_ has the value "_Y_"
    
- The default tables are filled, which control the behavior of Role Maintenance when a transaction is selected in a role.
    
Both steps are described in detail in this lesson.
![[Pasted image 20251009105230.png]]

You only need to check that the profile parameter is set to the correct value.

To check this, use transaction RZ11. The figure shows transaction RZ11 after you have entered the parameter name (_auth/no_check_in_some_cases_). For _Current value_, _Y_ must be entered.

To check this, use transaction RZ11. The figure shows transaction RZ11 after you have entered the parameter name (_auth/no_check_in_some_cases_). For _Current value_, _Y_ must be entered.

You can find more details on the currently selected parameter by choosing _Documentation_.

Alternatively, you can select and check the parameter setting using report _RSPFPAR_.

![[Pasted image 20251009105325.png]]

If an administrator selects a transaction while creating a role, Role Maintenance selects the authorization objects that are checked in this transaction and maintained in Role Maintenance. Four cases can occur:

- For an authorization object against which the check is performed in the selected transaction, Role Maintenance has default values for the authorization content so that full authorization can be provided. The traffic light beside the authorization is **green**.
    
- For an authorization object against which the check is performed in the selected transaction, Role Maintenance does not have default values for the authorization content. In the example on the slide, the SAP Office transaction SO01 has been selected, from which you can access files at operating system level. For security reasons, no specifications are made as to which files can be accessed in read-only or in write mode. The traffic light beside the authorization is **yellow**.
    
- For an authorization object against which the check is performed in the selected transaction, Role Maintenance does not have default values for the authorization content, and this field is an "organizational level field". The traffic light beside the authorization is therefore **red**.
    
- It may be the case that some authorization checks during transaction processing were not maintained in Role Maintenance. The corresponding authorization objects do not appear in the profile overview.


SAP delivers the tables _USOBX_ and _USOBT_. These tables are filled with default values and are used for the initial fill of the customer tables _USOBX__**_C_** and _USOBT__**_C_**. After the initial fill, you can modify the customer tables, and therefore the behavior of Role Maintenance, if required.

Table _USOBX_ defines which authorization checks are to be performed within a transaction and which are not (despite programmed _authority-check_ command). This table also determines which authorization checks are maintained in Role Maintenance.

Table _USOBT_ defines for each transaction and for each authorization object which default values an authorization created from the authorization object should have in Role Maintenance.

Under menu item 1, _Initially Fill the Customer Tables_, transaction SU25 copies the SAP defaults from _USOBX_ and _USOBT_ to the customer tables _USOBX__**_C_** and _USOBT__**_C_**. You can use Role Maintenance as of this point.

![[Pasted image 20251009105727.png]]After the customer tables _USOBX_**__C_** and _USOBT_**__C_** have been filled, you can maintain them to adjust the behavior of Role Maintenance and the authorization checks to be performed for each transaction. The tables are maintained in transaction SU24.

This transaction displays the authorization default values of a transaction.
The behavior of objects is governed by the maintenance status of the authorization object and the check indicator.

1.  Authorization Default Status
    
    Possible values for the authorization default status are as follows.
    
    ### Authorization Default Status:
    
    - #### Yes
        
        By setting this default status, developers inform administrators that the user requires an authorization for this object to execute the core functionality of the application.
        
        If this application is added to a role, the Profile Generator adds an authorization for this object in the role. The fields of the authorizations are predefined with the proposed values.
        
    - #### Yes, Without Values
        
        By setting this default status, developers inform administrators that the user requires an authorization for this object to execute the core functionality of the application. However, the developers cannot specify any values, since these are only determined in the customer system.
        
        If the administrator adds the application to a role, the Profile Generator places an empty authorization for this object in the role.
        
    - #### No
        
        By setting this authorization default status, developers inform administrators that a user does not require an authorization for this object to execute the core functionality of this application.
        
        If this application is added to a role, the Profile Generator does not place an authorization for this object in the role.

#### Check Indicator

The following check indicator values are supported.

### Check Indicator

- #### Check
    
    Default check indicator.
    
    The appropriate authorization object is always checked.
    
- #### Do Not Check
    
    The authorization check for this authorization object is deactivated. The system does not check whether the user has a suitable authorization.
    
    This indicator cannot be chosen for HR and Basis authorization objects.

1. Maintenance status of authorization object
    
    The maintenance status of an authorization object indicates whether authorization default data has been maintained correctly for the object.
    
    Possible values are
    
    - 'Maintained' (green icon) - _Default status_ (and any authorization field values) have been maintained completely.
        
    - 'Not maintained' (red icon) - The authorization default status has not yet been maintained or another priority 1 error has occurred.
        
    - 'Maintained with warning' (yellow icon) - Authorization field values have not been maintained correctly for the object; a priority 2 (or lower) warning exists.
        
    - 'Do not check' (gray icon) - The authorization check has been disabled for the object (_Check Indicator_ is set to "Do not check").

After an upgrade, transactions that were selected in the menu of existing roles can be protected using additional authorization objects in the target release. This means that tables _USOBT_C_ and _USOBX_C_ have to be updated as well as the existing roles.

The authorization checks added in the target release require that tables _USOBX_C_ and _USOBT_C_ as well as the roles created in the source release be updated to the latest version. To do this, you can use the transaction SU25, step _Postprocess of Settings After Upgrading to Higher Release_.

![[Pasted image 20251009110541.png]]Consequently, a comparison procedure is required, which is performed using the step _Postprocess the Settings After Upgrading to a Higher Release_.

Automatic Comparison with SU22 Data

This compares Role Maintenance data from the previous release with the data for the current release. New default values are written in the customer tables for Role Maintenance. You only need to perform a manual adjustment later (in step _2B_) for transactions in which you changed the settings for authorization default values. You can also display a list of the roles to be checked (step _2C_).

Modification Comparison with SU22 Data

If you have made changes to the authorization values in transaction SU24, you can compare these with the new SAP defaults. You can see the values delivered by SAP and the values that you changed next to each other, and you can make an adjustment, if desired. You can assign the authorization default values by double-clicking the relevant line.

Search for Obsolete Applications

This step searches for obsolete, locked, or no-longer-existing transactions or function modules so you are able to adapt PFCG roles for correct authorization in the new SAP release.

Update of Application Groups in Role Menu

You have inserted application groups (for example, SAP Fiori tile catalogs) into the menu of roles. The applications contained in the application groups were also included in the role menu as sub nodes of the groups. If you add applications to a group or delete applications from a group, you must update the role menu.

Roles to be Checked

This step guides you through all the roles that are affected by newly-added authorization checks and that have to be changed to correspond. You can jump directly to Role Maintenance.

### New Functionality in SU25: Deactivating Merge Mode in Step "Roles to be Checked"

Transaction SU25 is required after an upgrade to update the customer-specific authorization default values and roles. Step _Roles to be Checked_ provides a list of roles which are affected by the newly added or changed authorization default values. The roles that authorization data must be merged with get the "Profile comparison required" status (merge mode) and are marked with red traffic lights. The merge mode triggers an automatic merging when we go into Role Maintenance in transaction PFCG. This automatic merging is often undesired because role administrators may want to display the original authorization data first before the merge process.

With the new functionality in Step _Roles to be Checked_, you can now select a set of roles that have a red status and deactivate the merge mode using function key F7. All the roles that you process in this manner get a new yellow status. When you now navigate back to transaction PFCG, the system no longer merges the roles automatically, but displays the relevant authorization data. To take advantage of this new feature, import the relevant Support Package, see SAP Note 1417883.

As long as one role has a yellow status, the function key F8 can be used to reactivate the merge mode. You can change between the active and inactive mode as many times as required. Whenever step _Roles to be Checked_ is called again, roles with an inactive merge mode are automatically transferred to active mode.

Additional information related to this new function enhancement:

- Meaning of the Statuses
    
    The role statuses in Step _Roles to be Checked_ are not identical to the authorization statuses of roles in the Authorizations of Role Maintenance. Step _Roles to be Checked_ refers only to whether or not the authorization data should or can be merged. The status of the related authorization profiles in PFCG is irrelevant. The exact status definitions are as follows:
    
    - Red: The authorization data must and can be merged (merge mode is active).
        
    - Yellow: The authorization data must be merged, but this is not possible (merge mode is inactive)
        
    - Green: The authorization data has already been merged.
        
- Role Lock
    
    During a status change, the roles are temporarily locked. Roles that cannot be locked remain in their old status.
    
- Roles that Have a Green Status
    
    For roles which the authorization data has already been merged, you can never change the status. Selecting these roles does not have any effect. Once you have transferred all the roles in the list to green status by merging the authorization data, you do not have to perform any further activities in step _Roles to be Checked_. As a result, the functions for changing the merge mode and the selection functions are not available.


![[Pasted image 20251009111258.png]]If you use a very large number of roles, it can be useful for reasons of time, to do without the postprocessing initially, and to assign the role _SAP_NEW_ to the users manually. The role SAP_NEW is used to bridge the differences in releases in the case of new or changed authorization checks for existing functions, so that your users can continue to work as normal.

The role SAP_NEW must use be generated in accordance with the system environment in transaction SU25_Manually Adjust Selected Roles_ → _Generate Standard Role SAP_NE or SAP_NEW_F4_ or using the report **REGENERATE_SAP_NEW**.

After generation, the role _SAP_NEW_ contains authorizations for all new checks in existing transactions.

The role _SAP_NEW_ guarantees backward compatibility of the authorizations if a new release or an update or authorization checks introduce checks for previously unprotected functions.
### Workbench for Switchable Authorization Scenarios

A central switchable authorization check is needed for different application scenarios and as a requirement for security-relevant corrections to the authorization concept.

If SAP delivers new authorization checks in already established business processes via corrections delivered in a Note or Support Package, these checks should be available in the customer's landscape, but they should not affect production processes. You can identify new authorization checks with scenario names in the delivered code. A scenario groups together the new or changed authorization checks of a business process. The switchable authorization scenario construct is a simple way of introducing tighter security requirements scenario-by-scenario, according to customer requirements. The cross-application solution of switchable authorization checking creates the necessary transparency about the degree of conversion of tighter authorization concepts.

For details on this Switchable Authorization Scenarios, refer to SAP notes 1908870 - SACF: Workbench for switchable authorization scenarios and 1922808 - SACF: FAQ - Supplementary application information.