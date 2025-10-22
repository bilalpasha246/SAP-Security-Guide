## Authorization Trace for OData Services

The system trace for authorization checks shows the check of the start authorizations for the OData services. They are indicated by the **S_SERVICE** authorization object. Column **Application Name** shows the original application name of the OData service and column**Value 1** shows the hash code-based key entry.

![Screenshot on authorization trace for OData Services.](https://learning.sap.com/service/media/topic/cca75b72-03ad-4392-bbdf-35bbd723bcc6/ADM945_24_en-US_media/ADM945_24_en-US_images/AuthorizationTrace.png "Screenshot on authorization trace for OData Services.")

To analyze missing start authorizations for OData services you can also use the system trace for authorization checks. If an entry for an OData service is missing in the role menu, the role maintenance cannot propose a start authorization for this service. 

In the example above the start authorization of the OData Service FIN_USER_DEFAULTPARAMETER_SRV is not checked during the execution of the application.

## CDS View Results in Authorization Trace

You evaluate the user trace with transaction STUSERTRACE. The system also displays trace entries that were written due to the CDS access control of a CDS entity.

![Illustration showing CDS View Results in Authorization Trace.](https://learning.sap.com/service/media/topic/d3917195-efe2-4f3c-b15d-33ca56565f5b/ADM945_24_en-US_media/ADM945_24_en-US_images/CDS_View_Results_in_Authorization_Trace.png "Illustration showing CDS View Results in Authorization Trace.")

If access was made via access control of a CDS entity, the **CDS Entity** column contains the name of the view that was access.

When you click the name of the CDS entity, the fields used during the access control are displayed:

**Filter**

         Fields of the authorization object for which a user must have authorization (such as activity "03" for display authorization).

**Requested Fields**

         The user's authorizations are read for these fields of the authorization object and are used to select the business data. These fields are highlighted in blue in the output list.

The underlying DCL role is linked to authorization trace via the _CDS Access Control_ button.

![Screenshots showing the example of CDS View Results in Authorization Trace.](https://learning.sap.com/service/media/topic/d3917195-efe2-4f3c-b15d-33ca56565f5b/ADM945_24_en-US_media/ADM945_24_en-US_images/Example_of_CDS_View_Results_in_Authorization_Trace.png "Screenshots showing the example of CDS View Results in Authorization Trace.")

Note

For further information see following SAP Notes:

- 2437978 - STAUTHTRACE: Access control for a CDS entity
    
- 2242714 - STAUTHTRACE: Display of access filtering
    
- 2437980 - STUSERTRACE: Access control for a CDS entity
    

## Practice System Exercise: Use the System Trace for Authorization Checks

Select Start Exercise to start the simulation.

#### Part 1

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_EB8DE4AA5186CAE:uebung)

#### Part 2

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_7F0BDF16CA3FA48C:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

### Business Example

After creating roles some authorizations for the OData services may be missing. You need to find the missing authorizations. Therefore you can evaluate the System Trace for Authorization Checks.

As a prerequisite the instructor has to start the System Trace for Authorization Checks transaction STAUTHTRACE on the front-end server (FES) for all adm945 users. This is done in the first task. The participants will complete the exercise in the second task.

### Task 1: Enable the System Trace for Authorization Checks on the SAP S/4HANA system. (Done by your instructor)

#### Steps

1. Log on to the SAP GUI of the system S4D.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        
2. Enable the System Trace for Authorization Checks (System-Wide).
    
    1. Start the System Trace for Authorization Checks, using transaction STAUTHTRACE.
        
    2. In the _Trace Options_ screen area, in the _Trace for User Only_ field, enter **adm945***.
        
    3. Choose _System-Wide Trace_.
        
    4. Choose _Select All_ in the server list.
        
    5. Choose _Activate Trace (F6)_.
        

### Task 2: Evaluate the System Trace for Authorization Checks on the on the SAP S/4HANA system

#### Steps

1. In Mozilla Firefox, start the SAP Fiori Launchpad.
    
    1. In the _Microsoft Windows_ start menu, choose _Mozilla Firefox_.
        
    2. In _Mozilla Firefox_, go to _Favorites_.
        
    3. In _Favorites_, choose _10 Development_ → _s4dhost_ → _10 S4D Fiori Launchpad_.
        
    4. Enter the following data:
        
        |Field|Value|
        |---|---|
        |_User_|**adm945-##**|
        |_Password_|Your password.|
        
    5. Choose _Log on_.
        
2. Start the _Manage Banks - Cash Management_ app.
    
    1. In the _SAP Fiori Launchpad_, select the _Financial Accounting Space ##_ and choose the _Bank Management Page ##_.
        
    2. Select the _Manage Banks - Cash Management_ app.
        
    3. Choose _Go_.
        
3. Go back to the SAP GUI as administrator and evaluate the System Trace for Authorization Checks (System-Wide) to find out what has been checked and what authorizations might miss.
    
    1. Start the System Trace for Authorization Checks transaction STAUTHTRACE.
        
    2. In the _Restrictions for the Evaluation_ screen area, in the _User_ field, enter **adm945-##**.
        
    3. Choose _System-Wide Trace_.
        
    4. Choose _Select All_ in the server list.
        
    5. Choose _Evaluate Trace (F8)_.
        
        #### Result
        
        The trace indicates that during execution of the application _UI_CASHBANK_MANAGE_ authorization for the CDS entity _C_CASHBANKTP_ is checked according to the authorization object **F_BNKA_MAO**.