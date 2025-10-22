

Objective

After completing this lesson, you will be able to manage SAP Fiori Business Roles.

## Business Roles

### Definition of Business Roles

A business role is an abstract construct that represents a job that a person does. The business role includes everything they do that is related to their workplace responsibilities.

Note

A single business role does not necessarily equate to a person’s complete job, for example, in lean organizations or locations some people may have responsibility for multiple business roles.

Business roles are a fundamental concept of the user experience in SAP S/4HANA. With SAP Fiori the focus on business roles has increased dramatically. From the earliest days of SAP Fiori in 2013 the first and most important design principle of SAP Fiori is it is role-based, that is, business roles are designed for the user, the user's needs, and how the user works.

SAP delivers business roles as templates. You can use them as a starting point, copy them, and refine to meet your real needs. You will find the SAP-delivered business roles and their definitions in the SAP Fiori apps reference library.

Each SAP-delivered business role is matched by a security/authorizations role in your SAP S/4HANA system that can be assigned to the users who perform that business role.

Note

The reverse is not true, that is, there are many security roles in your SAP S/4HANA system that are not considered business roles. These are provided for other purposes such as administration.

### Creating Custom Business Roles

Custom business roles reflect how a real business role is applied within a specific organization. Customers can create their own business roles either by copying the SAP-delivered business role and refining it or creating a custom business role from scratch. Creating custom business roles is an essential skill for any team deploying SAP S/4HANA or just looking to drive more value from your existing SAP S/4HANA system.

To create a custom business role, a corresponding security/authorization role has to be created in the role maintenance (transaction PFCG). The role can then be filled with one or multiple SAP Fiori catalogs and spaces. The technical implementation of it is going to be explained in the following sections.

## SAP Fiori OData Authorization

### SAP Fiori Authorization Model on the Front-End Server

![Illustration on SAP Fiori Authorization Model for SAPUI5 Fiori Apps - UI Access.](https://learning.sap.com/service/media/topic/f0461fe3-9dc2-424b-be54-e6d3041c6889/ADM945_24_en-US_media/ADM945_24_en-US_images/03_01_FioriAuthorizationModelSAPUI5AppsUIAccess.png "Illustration on SAP Fiori Authorization Model for SAPUI5 Fiori Apps - UI Access.")

On the front-end server (FES) users are provided with the UI access to apps and the start authorizations for the activated OData services (**IWSG**) used by the SAP Fiori apps.

The PFCG role needs the catalog for the start authorization of the activated OData services and the group or space for displaying the tiles on the SAP Fiori Launchpad home screen.

### SAP Fiori Authorization Model on the Back-End Server

![Illustration on SAP Fiori Authorization Model for SAPUI5 Fiori Apps - Data Access.](https://learning.sap.com/service/media/topic/f0461fe3-9dc2-424b-be54-e6d3041c6889/ADM945_24_en-US_media/ADM945_24_en-US_images/03_01_FioriAuthorizationModelSAPUI5AppsDataAccess.png "Illustration on SAP Fiori Authorization Model for SAPUI5 Fiori Apps - Data Access.")

To get business data from the implemented OData service on the back-end side, start authorizations to call the back-end server and data access authorizations to execute the app and display business data are necessary.

By assigning the catalog to the PFCG role menu, start authorization for the implemented OData service and the authorization proposals for the business authorizations. You can adjust these as required.

When using an embedded front-end server (FES), the FES and the BES functionality reside in one system, which means that UI access and data access authorizations can be maintained in one business role.

Hint

We recommend that you add a catalog to the role menu instead of adding individual OData services. The system determines the OData services for a catalog and automatically includes the start authorizations when adding the catalog to the role menu.

However, this is not always the case and adding single OData service authorizations provides additional security, especially if the FES is set up as a separate hub. By specifying the services explicitly in the role menu, you control which requests on behalf of a user can pass SAP Gateway.

You can create a new role or use an existing role that fits the scope of the catalog. If you add the services to an existing role, the authorization proposals have to be merged with the authorization values already defined in the role. You can consider using existing roles if the following applies:

- The users assigned to the role need access to all apps in the catalog.
- The business authorizations already defined in the role and those that you define for the apps in the catalog do not contradict.

Note

When a catalog is changed, for example, an app is added or removed, you must update the start and data access authorizations for the services in the PFCG role. You can determine the roles that must be adapted by using the PRGN_COMPARE_ROLE_MENU report.

Alternatively, in Role Maintenance (PFCG), you can compare and update the roles to reflect the authorizations changes as given in the current definition of the catalog.

However, the comparison (both using the report or comparing in PFCG) does not include applications or services that you added manually to the role menu.

![Illustration on Authorization Defaults for SAPUI5 Fiori Apps - UI and Data Access.](https://learning.sap.com/service/media/topic/f0461fe3-9dc2-424b-be54-e6d3041c6889/ADM945_24_en-US_media/ADM945_24_en-US_images/03_01_AuthorizationProposalsFioriAppsUIandDataAccess.png "Illustration on Authorization Defaults for SAPUI5 Fiori Apps - UI and Data Access.")

Both, the OData start authorization on the FES and the OData access authorization on the BES can include SU24 authorization defaults.

SU24 authorization defaults for IWSG objects only includes start authorizations. The default for IWSV objects mostly include business functional authorization objects which are used within the OData service execution.

## SAP Fiori Legacy Authorization

![Illustration on Authorization Defaults for SAP Fiori Legacy Apps.](https://learning.sap.com/service/media/topic/a7c427ec-84d3-4866-aea6-360633c535cf/ADM945_24_en-US_media/ADM945_24_en-US_images/03_01_SAPFioriLegacyAuthorization.png "Illustration on Authorization Defaults for SAP Fiori Legacy Apps.")

SAP Fiori legacy apps such as Web Dynpro or SAP GUI for HTML apps need an HTTP / HTTPS connection directly to the back-end server (BES).

However, legacy apps still need to be part of a business catalog, which is going to be assigned to the PFCG role. Also, based on the business catalog, an SAP Fiori space with pages can be created, which will display the tile of the legacy app.

In the PFCG role, start authorizations and the required execute and data access authorizations must be maintained.

The SAP Fiori Legacy Apps have the SU24 authorization proposals of the called transaction or Web Dynpro application.

## General Authorizations Required for SAP Fiori

In addition to app-specific authorizations, users also need general authorizations to run SAP Fiori launchpad. Besides that, administrators also need access to all the design-time tools, such as _SAP Fiori launchpad content manager_, _SAP Fiori launchpad designer_, tools for managing spaces and pages, as well as troubleshooting tools. SAP delivers roles templates for end users and administrators, that role administrators have to copy to their customer name space, adjust according to the customer's needs, and assign to users.

### General Authorizations Required for SAP Fiori

- SAP-Delivered Role for End users: SAP_FLP_USER
- SAP-Delivered Role for Administrators: SAP_FLP_ADMIN

These authorization roles include the authorizations for the UI2 OData services. For these OData services, both the model provider of the activated OData services and the data provider reside on the FES.

## Practice System Exercise: Create Business Roles and Assign Catalogs to Roles

Select Start Exercise to start the simulation.

#### Part 1

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_F91F7E31A279CCBA:uebung)

#### Part 2

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_83C9AC0900A4EEA2:uebung)

#### Part 3

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_6437704F4CACA80:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

### Business Example

In SAP S/4HANA system, authorizations are necessary to display the tiles in the SAP Fiori Launchpad and to start the SAP Fiori apps.

In this exercise, you will create a business role for a financial accounting manager and for an inventory manager:

- ADM945_##_BR_FINANCIALS with authorizations for the following catalog:
    
    ADM945_##_BC_FIN_ACCOUNT
    
- ADM945_##_BR_INVENTORY with authorizations for the following catalog:
    
    ADM945_##_BC_INVENTORY_MGMT
    

Note

In this exercise, when an object name or value contains ##, replace ## by the number your trainer assigned to you.

![Illustration on ADM945: Roles Overview.](https://learning.sap.com/service/media/topic/b7b6cd90-491b-40d1-81c7-3ea06d63a299/ADM945_24_en-US_media/ADM945_24_en-US_images/ADM945_Roles_Overview.png "Illustration on ADM945: Roles Overview.")

### Task 1: Create a Test User

You want to create test user **ADM945-##** in your SAP S/4HANA system S4D.

#### Steps

1. Log on to the SAP GUI of the system S4D.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        
2. Create a user master record for dialog user **ADM945-##**.
    
    1. Start the User Maintenance (transaction SU01).
        
    2. Enter **ADM945-##**.
        
    3. Choose _User_ (_Create User F8_) to create a dialog user.
        
    4. On the _Address_ tab, enter any name of your choice.
        
        Note
        
        _Last name_ is mandatory.
        
    5. On the _Logon Data_ tab, enter an initial password of your choice.
        
        Initial password:____________________
        
        Note
        
        The password must be minimum 10 characters long, contain at least 1 digit, and at least 1 capital letter.
        
3. Assign the role **Z_FLP_USER** to your new user master record.
    
    Hint
    
    This role is copied form SAP-standard role **SAP_FLP_USER** and includes basic authorizations for end-users of the SAP Fiori Launchpad. As of SAP S/4HANA 2020, the **SAP_FLP_USER** role replaces the **SAP_UI2_USER_700** role.
    
    1. Switch to the _Roles_ tab.
        
    2. In the _Role_ field, enter **Z_FLP_USER**.
        
    3. Choose _Save_ in the lower right-hand corner.
        

### Task 2: Create Role and Assign Catalog for Financial Accounting Manager

You want to create the _ADM945_##_BR_FINANCIALS_ business role for the financial accounting manager.

#### Steps

1. Create the _ADM945_##_BR_FINANCIALS_ business role.
    
    1. In system S4D, start the role maintenance (transaction PFCG).
        
    2. Enter the role name **ADM945_##_BR_FINANCIALS**.
        
    3. Choose _Create Single Role_.
        
    4. Enter any description of your choice.
        
    5. Choose _Save_ in the lower right-hand corner.
        
2. Assign the _ADM945_##_BC_FIN_ACCOUNT_ catalog to the _ADM945_##_BR_FINANCIALS_ role.
    
    1. Go to the _Menu_ tab.
        
    2. In the context menu of the _Transaction_ button, choose _SAP Fiori Launchpad_ → _Launchpad Catalog_.
        
        Note
        
        Do not change the location option of the Front-End Server. Since the FES is embedded in the SAP S/4HANA system, its location is considered local.
        
    3. In the _Catalog ID_ field, use the value help (F4) and search for the **ADM945_##_BC_FIN_ACCOUNT** catalog.
        
    4. Select the catalog and choose _Copy_.
        
    5. Choose _Continue_.
        
    6. Expand the catalog and review the entries that have been added with it.
        
    7. Choose _Save_ in the lower right-hand corner.
        
        #### Result
        
        When you expand the catalog in the role menu, you will see the _IWSG_ and _IWSV_ entries for the SAP Fiori SAPUI5 apps as well as the FAGLB03 transaction as legacy app _Display Balances_.
        
3. Change the authorization data and generate a profile.
    
    1. Go to the _Authorizations_ tab.
        
    2. Choose _Change Authorization Data_.
        
    3. In the _Define Organizational Levels_ dialog box, choose _Full authorization_.
        
    4. Choose _Save_.
        
    5. View the authorization objects and the filled authorization fields.
        
    6. Choose _Status_ to fill in the missing values and assign full authorization.
        
    7. In the _Assign Full Authorization for Subtree_ dialog box, choose _Execute_ to fill the empty authorization fields.
        
    8. Choose _Generate (Shift + F5)_.
        
    9. In the _Assign Profile Name for Generated Authorization Profile_, choose _Execute_.
        
    10. Choose _Back (F3)_.
        
4. Assign the_ADM945_##_BR_FINANCIALS_ business role to the **ADM945-##** user.
    
    1. Go to the _User_ tab.
        
    2. In the _User ID_ field, enter **ADM945-##**.
        
    3. Choose _Save_ in the lower right-hand corner.
        
    4. Execute _User Comparison_.
        
    5. Choose _Full Comparison_.
        
    6. Choose _Cancel_.
        
    7. Choose _Back (F3)_.
        

### Task 3: Create Role and Assign Catalog for Inventory Manager

You want to create the _ADM945_##_BR_INVENTORY_ business role for the inventory manager.

#### Steps

1. Create the _ADM945_##_BR_INVENTORY_ business role.
    
    1. In system S4D, start the role maintenance (transaction PFCG).
        
    2. Enter the role name **ADM945_##_BR_INVENTORY**.
        
    3. Choose _Create Single Role_.
        
    4. Enter any description of your choice.
        
    5. Choose _Save_ in the lower right-hand corner.
        
2. Assign the _ADM945_##_BC_INVENTORY_MGMT_ catalog to the _ADM945_##_BR_INVENTORY_ role.
    
    1. Go to the _Menu_ tab.
        
    2. In the context menu of the _Transaction_ button, choose _SAP Fiori Launchpad_ → _Launchpad Catalog_.
        
        Note
        
        Do not change the location option of the Front-End Server. Since the FES is embedded in the SAP S/4HANA system, its location is considered local.
        
    3. In the _Catalog ID_ field, use the value help (F4) and search for the **ADM945_##_BC_INVENTORY_MGMT** catalog.
        
    4. Select the catalog and choose _Copy_.
        
    5. Choose _Continue_.
        
    6. Choose _Save_ in the lower right-hand corner.
        
        #### Result
        
        When you expand the catalog in the role menu, you will see the _IWSG_ and _IWSV_ entries for the SAP Fiori SAPUI5 apps as well as the _WDYA_ entry for the legacy app _Physical Inventory Analysis_, which is a Web Dynpro application.
        
3. Change authorization data and generate a profile.
    
    1. Go to the _Authorizations_ tab.
        
    2. Choose _Change Authorization Data_.
        
    3. In the _Define Organizational Levels_ dialog box, choose _Full authorization_.
        
    4. Choose _Save_.
        
    5. View the authorization objects and the filled authorization fields.
        
    6. Choose _Status_.
        
    7. In the _Assign Full Authorization for Subtree_ dialog box, choose _Execute_ to fill the empty authorization fields.
        
    8. Choose _Generate (Shift + F5)_.
        
    9. In the _Assign Profile Name for Generated Authorization Profile_, choose _Execute_.
        
    10. Choose _Back (F3)_.
        
4. Assign the _ADM945_##_BR_INVENTORY_ business role to the **ADM945-##** user.
    
    1. Go to the _User_ tab.
        
    2. In the _User ID_ field, enter **ADM945-##**.
        
    3. Choose _Save_ in the lower right-hand corner.
        
    4. Execute _User Comparison_.
        
    5. Choose _Full Comparison_.
        
    6. Choose _Cancel_.
        
    7. Choose _Back (F3)_.
        

### Task 4: Log on to the SAP Fiori Launchpad and Examine the Apps

You want to log on to the SAP Fiori Launchpad with**ADM945-##** test user you created in the task before. You also want to check if the test user can find the assigned catalogs in the App Finder of his SAP Fiori Launchpad.

#### Steps

1. Start the SAP Fiori Launchpad in Mozilla Firefox.
    
    Hint
    
    We do not recommend that user _Google Chrome_ since you have already logged in to the SAP Fiori Launchpad with your **train-##** user. To avoid the log off, you can use any other browser in the training landscape to start the SAP Fiori Launchpad if you know the URL. Mozilla Firefox is only a suggestion. However, there you will find all necessary bookmarks.
    
    1. In the _Microsoft Windows_ start menu, choose _Mozilla Firefox_.
        
    2. In _Bookmarks_, choose _10 Development_ → _s4dhost_ → _10 S4D SAP Fiori Launchpad_.
        
    3. Enter the following data:
        
        |Field|Value|
        |---|---|
        |_User_|**ADM945-##**|
        |_Password_|**initial password**|
        
    4. Choose _Log On_.
        
    5. Enter the current password and create a new password.
        
        Note
        
        The password must be minimum 10 characters long, contain at least 1 digit, and at least 1 capital letter.
        
    6. Choose _Change_.
        
    7. Choose _Continue_.
        
    8. Examine the SAP Fiori Launchpad _Home_ screen.
        
    
    #### Result
    
    No tiles appear on the _Home_ screen.
    
2. Test the catalog entries in the App Finder of SAP Fiori Launchpad.
    
    1. In the top right-hand corner, select your user.
        
    2. Go to the _App Finder_.
        
        #### Result
        
        You should see the catalogs _Financial Accounting Catalog ##_ and _Inventory Management Catalog ##_.
        
    3. Select _Financial Accounting Catalog ##_ and find the apps that are contained in this catalog.
        
    4. Select _Inventory Management Catalog ##_ and find the apps that are contained in this catalog.
        
3. Start the _Manage Banks_ app from the _ADM945_##_BC_FIN_ACCOUNT_ catalog and display some data.
    
    1. In the App Finder, select _Financial Accounting Catalog ##_ once again and choose _Manage Banks_.
        
        #### Result
        
        You can start the app. No error occurs. The _IWSG_ service is started on front-end server (FES). The _IWSV_ service enables the user to start the app on the back-end server (BES) and access the business data.
        
    2. Choose _GO_.
        
        #### Result
        
        The list of banks is displayed.
        
    3. Choose any bank, e.g. _50070010 (Bank 1 - SAMPLE BANK)_ to drill down for details. To do so, in the line of the bank, select the arrow on right-hand side.
        
    4. Examine the data.
        
    5. Choose _SAP_ logo to return to the FLP home screen.
        
4. Start the _Material Documents Overview_ app from the _Inventory Management Catalog ##_ catalog.
    
    1. In the top right-hand corner, select your user.
        
    2. Go to the _App Finder_.
        
    3. Select the _Material Documents Overview_ app.
        
        #### Result
        
        You can start the app. No error occurs. The _IWSG_ service is started on front-end server (FES). The _IWSV_ service enables the user to start the app on the back-end server (BES) and access the business data.
        
    4. Choose _SAP_ logo to return to the FLP home screen.