# Using Additional Features for Role Maintenance

Objective

After completing this lesson, you will be able to utilize Additional Reports for Role Maintenance.

## New Features for Role Maintenance

#### Overview

![Table showing new features for Role Maintenance.](https://learning.sap.com/service/media/topic/e9f8a208-5422-410e-99db-26a36cccdb54/ADM945_24_en-US_media/ADM945_24_en-US_images/New_Features_for_Role_Maintenance.png "Table showing new features for Role Maintenance.")

### Update of Application Groups in Role Menu

You have inserted application groups (for example, SAP Fiori tile catalogs) into the menu of roles. The applications contained in the application groups were also included in the role menu as sub nodes of the groups. If you add applications to a group or delete applications from a group, you must update the role menu.

![Screenshots showing update of application groups in role menu for PFCG.](https://learning.sap.com/service/media/topic/e9f8a208-5422-410e-99db-26a36cccdb54/ADM945_24_en-US_media/ADM945_24_en-US_images/05_01_AnalyzeSAPFioriApplicationsInRoles_006.png "Screenshots showing update of application groups in role menu for PFCG.")

For updating of an SAP Fiori catalog within PFCG mark the appropriate entry of an SAP Fiori catalog in the _Menu_ PFCG role tab page and push the _Details_ button. If you do that in a SAP Fiori front-end server, you can directly choose the SAP Fiori catalog which holds the definitions of the Fiori configurations. If you are in a back-end server, you have to choose an appropriate RFC connection to be able to connect to the SAP Fiori front-end server where the SAP Fiori catalogs are defined. Look for the right catalog and check the status of the applications which are available in that catalog.

The update of application groups in role menu is available in front- and back-end systems.

The _PRGN_COMPARE_ROLE_MENU_ report offers navigation options to transactions PFCG and SUPC as well as the mass menu change function. For detailed information, see the program documentation on the initial screen of the report.

Note

See also SAP note 2465999 - Update of application groups in role menu.

![Screenshots showing mass update of Application Groups in Role Menu.](https://learning.sap.com/service/media/topic/e9f8a208-5422-410e-99db-26a36cccdb54/ADM945_24_en-US_media/ADM945_24_en-US_images/05_01_AnalyzeSAPFioriApplicationsInRoles_008.png "Screenshots showing mass update of Application Groups in Role Menu.")

The output of the _PRGN_COMPARE_ROLE_MENU_ report shows application groups and the applications they contain which are inserted in the _Menu_ PFCG tab page of the selected PFCG roles. The status shows whether the application group needs to be compared. The _Comparison_ column informs you whether an application needs to be deleted from the menu or added to it. If errors or warnings occur during the evaluation of the application groups, you can display the messages by choosing the icon in the _Messages for Application Group_ column.

The authorization status corresponds to the specification on the _Authorizations_ tab in transaction PFCG.

The report can also be started from transaction SU25 (_Upgrade Tool for Profile Generator_) with the _Update of Application Groups in Role Menu_ menu entry.

### Creation of Roles

The PRGN_CREATE_FIORI_FRONTENDROLE program allows to maintain roles with menu options from selected SAP Fiori tile catalogs.

You can use the PRGN_CREATE_FIORI_FRONTENDROLE program to perform the mass maintenance of menu options from selected SAP Fiori tile catalogs. The assignment of the SAP Fiori tile catalogs to roles takes place by means of a table that you either create or upload manually or generate automatically by means of catalog selection.

Note

Depending on the scenario you can use it to create front-end roles in a hub deployment or to create roles in an embedded scenario.

![Screenshots on creating SAP Fiori Front-End Roles.](https://learning.sap.com/service/media/topic/e9f8a208-5422-410e-99db-26a36cccdb54/ADM945_24_en-US_media/ADM945_24_en-US_images/Create%20_SAP_Fiori_Frontend_Roles.png "Screenshots on creating SAP Fiori Front-End Roles.")

Note

See also SAP note 2648554 - Creation of front-end roles for SAP Fiori launchpad.

Note

The following tools for role creation are available in hub deployment scenarios.

In hub deployment scenarios you can transfer the menu of an SAP Fiori front-end role to the role menu of an existing or new back-end role.

- Transaction PFCG: Transfer of menus from front-end server:
    
    You are on the _Menu_ tab in role menu processing. The function for copying a menu from another role from the front-end server is for appending the menu of the front-end role to the existing menu. When you do this, you can adjust the menu options for SAP Fiori tile catalogs.
    
- Program PRGN_CREATE_FIORI_BACKENDROLES:
    
    You can use this program to create a back-end role for selected SAP Fiori front-end roles and to copy the relevant front-end role menu. If the back-end role already exists, the role menu of the back-end role is deleted and replaced by the role menu of the front-end role.
    

![Screenshots showing the transferring of the menu of Front-End Roles in PFCG.](https://learning.sap.com/service/media/topic/e9f8a208-5422-410e-99db-26a36cccdb54/ADM945_24_en-US_media/ADM945_24_en-US_images/Transfer_Menu_FES_PFCG.png "Screenshots showing the transferring of the menu of Front-End Roles in PFCG.")

Description of the PRGN_CREATE_FIORI_BACKENDROLES report.

Enter the RFC destination of the front-end server from which the role menus should be copied. Then select one or more roles (asterisk possible only at end of search string) from the front-end server.

The name of the back-end role can be identical to the name of the front-end role or can be changed by means of a naming conversion:

- The function for deleting a prefix allows you to delete a name component at the start of a role. If the prefix is not part of the name, an error message is output.
- You can use the function for adding a prefix to insert a name component at the start of a role. Note that the role name is restricted to 30 characters.

The following options are available for the execution:

- During the transfer of the role menu, you can adjust the menu options for SAP Fiori tile catalogs:
    - The RFC destination of the front-end server that you entered in the selection is entered as the new location for the remote front-end server in the SAP Fiori tile catalogs.
    - Applications that are assigned to the SAP Fiori tile catalogs on the front-end server and are started on the back-end server are included in the role menu as subnodes of the SAP Fiori tile catalog.
- The profile and the authorizations of the back-end roles can be deleted and created anew. During the recreation process, authorizations are generated from the authorization default values of the applications in the menu and empty fields are defined with full authorization. The profiles of the roles are then generated. If you have not selected this option, you must adjust the authorizations in PFCG.

Menu options for invalid applications are deleted during the import.

![Screenshots on creating Back-End Roles from Front-End Roles.](https://learning.sap.com/service/media/topic/e9f8a208-5422-410e-99db-26a36cccdb54/ADM945_24_en-US_media/ADM945_24_en-US_images/Create_BES__Role_from_FES_Role.png "Screenshots on creating Back-End Roles from Front-End Roles.")

## Practice System Exercise: Maintain Roles

Select Start Exercise to start the simulation.

#### Part 1

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_208936966E4B81AF:uebung)

#### Part 2

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_1B63459067967F85:uebung)

#### Part 3

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_5FAA8C03CA56DDAB:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

### Business Example

As a role developer you are asked to adapt the role concept and the appropriate PFCG roles which contain SAP Fiori applications.

### Task 1: Update of Application Groups in Role Menu

In a previous exercise you have modified the SAP Fiori catalog named **ADM945_##_BC_FIN_ACCOUNT**. The SAP Fiori App _Manage Banks_ was replaced by the SAP Fiori App_Manage Banks - Cash Management_. In addition the change was also adopted to the **Z_ADM945_##_BANK_MGMT** page.

The role still contains the _Manage Banks_ app in the **ADM945_##_BC_FIN_ACCOUNT**catalog. Therefore it is necessary to update the application groups in role menu and to maintain the authorizations.

#### Steps

1. Log on to the SAP GUI of the system S4D.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        
2. Update the application groups in role menu of role **ADM945_##_BR_FINANCIALS**.
    
    1. Start the Role Maintenance transaction PFCG.
        
    2. In the _Role_ field, enter **ADM945_##_BR_FINANCIALS**.
        
    3. Choose _Change_.
        
    4. Go to the _Menu_ tab.
        
    5. Select your catalog **Financial Accounting Catalog ##** in the role menu.
        
    6. Choose _Details_.
        
        #### Result
        
        The pop displays that several IWSG and IWSV services which were proposed due to the _Manage Banks_ app will be removed. The IWSG and IWSV services which were proposed due to the _Manage Banks - Cash Management_ app will be added. This is because you removed an SAPUI5 application in the catalog and added another one.
        
    7. In the _Change SAP Fiori Launchpad Catalog_ dialog box choose _Continue_ to update the catalog in the role menu.
        
    8. Choose _Save_.
        
3. Change the authorization data and generate a profile.
    
    1. Go to the _Authorizations_ tab.
        
    2. Choose _Change Authorization Data_.
        
    3. Check which authorization objects were deleted and which were added.
        
    4. Choose _Status_ to fill in the missing values and assign full authorization.
        
    5. In the _Assign Full Authorization for Subtree_ dialog box, choose _Execute_ to fill the empty authorization fields.
        
    6. Choose _Generate (Shift + F5)_.
        
    7. Choose _Back (F3)_.
        
    8. Choose _Save_.
        

### Task 2: Mass Update of Application Groups in Role Menu

Modify the SAP Fiori catalog named **ADM945_##_BC_FIN_ACCOUNT** and perform a mass update the application groups in role menu.

#### Steps

1. Log on to SAP Fiori Launchpad of system S4D with your **train-##** user. Use Google Chrome.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. In the _Microsoft Windows_ start menu, choose _Google Chrome_.
        
    2. In _Google Chrome_, go to _Bookmarks_.
        
    3. In _Bookmarks_, choose _10 Development_ → _s4dhost_ → _10 S4D SAP Fiori Launchpad_.
        
        Note
        
        Since SAP S/4HANA 2020 tools for setting up launchpad content can be accessed fro SAP Fiori launchpad. To access these tools, you as an administrator need to have the relevant authorizations that are provided by SAP-delivered role **SAP_FLP_ADMIN**.
        
2. From the group _Fiori Launchpad_, start _FLP Content Manager: Client-Specific_ from the SAP Launchpad home screen.
    
    1. On the SAP Fiori Launchpad home screen, choose _Fiori Launchpad_ group.
        
    2. Launch _FLP Content Manager: Client-Specific_ app.
        
        #### Result
        
        The WebGui Transaction opens.
        
    3. Alternatively, you can start transaction **/UI2/FLPCM_CUST** from SAP GUI. To do so, enter **/n/ui2/flpcm_cust** in the OK field of the SAP GUI.
        
    4. Ensure that the _Catalogs_ tab is selected.
        
3. Modify the SAP Fiori catalog named **ADM945_##_BC_FIN_ACCOUNT**. Add _Manage G/L Account Master Data_ app (app ID: F0731A).
    
    1. Search for your catalog _ADM945_##_BC_FIN_ACCOUNT_, for example, using the _Search Catalogs_ field.
        
    2. At the bottom (area _Content in Catalog..._), choose _Add Tiles/Target Mappings_ → _Add Tiles/TMs to Selected Catalog_.
        
    3. In the _Add Tiles/Target Mappings as References to Catalog..._ screen, search for App ID **F0731A**, for example using the _Search Tiles/Target Mappings_ field.
        
    4. Select the line for semantic object _GLAccount_ and action _manage_.
        
    5. Choose _Add Tile/TM Reference_.
        
4. Log on to the SAP GUI of the system S4D.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        
5. Update the application groups in role menus.
    
    1. Start the Profile Generator: Upgrade and First Installation transaction SU25.
        
    2. Execute _Update of Application Groups in Role Menus_.
        
    3. In the _Role_ field, enter **ADM945_##***.
        
    4. Choose _Execute_.
        
        #### Result
        
        The resulting list indicates in the _Comparison_ column that the IWSG service _ZFAC_MANAGE_GLACCOUNT_SRV_0002_ and the IWSV service _FAC_MANAGE_GLACCOUNT_SRV_0002_ are added to the catalog _ADM945_##_BC_FIN_ACCOUNT_ of the role _ADM945_##_BR_FINANCIALS_.
        
    5. Select the role _ADM945_##_BR_FINANCIALS_ and choose _Adopt Menu_.
        
    6. Choose _Yes_as answer for question _Do you want to execute the changes_.
        
    7. Choose _Change role_.
        
6. Change the authorization data and generate a profile.
    
    1. Go to the _Authorizations_ tab.
        
    2. Choose _Change Authorization Data_.
        
    3. Check which authorization objects were added.
        
    4. Choose _Status_ to fill in the missing values and assign full authorization.
        
    5. In the _Assign Full Authorization for Subtree_ dialog box, choose _Execute_ to fill the empty authorization fields.
        
    6. Choose _Generate (Shift + F5)_.
        
    7. Choose _Back (F3)_.
        
    8. Choose _Save_.
        
    9. Choose _Back (F3)_ to go back to the resulting list of roles .
        

### Task 3: Mass Maintenance of Roles from selected SAP Fiori Tile Catalogs

Create new front-end roles for your SAP Fiori tile catalogs.

|Catalog|Role|
|---|---|
|ADM945_##_BC_FIN_ACCOUNT|ADM945_##_BR_GE_FIN_ACCOUNT|
|ADM945_##_BC_INVENTORY_MGMT|ADM945_##_BR_GE_INVENTORY_MGMT|

#### Steps

1. Log on to the SAP GUI of the system S4D.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        
2. Create new front-end roles for your SAP Fiori tile catalogs.
    
    1. Start the ABAP Program Execution transaction **SA38**.
        
    2. In the _Program_ field, enter **PRGN_CREATE_FIORI_FRONTENDROLE**.
        
    3. Choose _Execute_.
        
    4. In the _Assigment of Fiori Tile Catalogs_ screen area, select _Generation from Fiori Launchpad Catalogs_.
        
    5. In the _Fiori Launchpad Catalog_ field, enter **ADM945_##***.
        
    6. In the _Namespace for Role: Delete Prefix_, enter **ADM945_##_BC**.
        
    7. In the _Namespace for Role: Add Prefix_, enter **ADM945_##_BR_GE**.
        
    8. Choose _Execute_.
        
    9. Check the name of the roles listed and choose _Execute_.
        
    10. In the _Messages_ dialog box, choose _Continue_.
        
    11. Choose _Back_.