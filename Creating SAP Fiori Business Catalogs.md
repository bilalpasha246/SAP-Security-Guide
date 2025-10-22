Objective

After completing this lesson, you will be able to manage SAP Fiori Business Catalogs.

## Tools for Setting Up Business Catalogs

Business catalogs contain a collection of tiles and target mappings relevant for a business role. The content of the business catalog is a subset of the content of the technical catalog. This subset reflects the requirements of a specific business user. To set up SAP Fiori business catalogs, _SAP Fiori launchpad content manager_ and _SAP Fiori launchpad designer_ can be used.

![Screnshot showing the tools for setting up Business Catalogs.](https://learning.sap.com/service/media/topic/b90e70e6-47a4-4e77-afa4-0ddaf8decd1a/ADM945_24_en-US_media/ADM945_24_en-US_images/02_01_FLP_Content_Manager_Designer_001.png "Screnshot showing the tools for setting up Business Catalogs.")

#### SAP Fiori Launchpad Content Manager

Administrators use the _SAP Fiori launchpad content manager_ to browse launchpad content and to set up business catalogs according to their needs.

Hint

To access _SAP Fiori launchpad content manager_ from the launchpad, authorization role **SAP_FLP_ADMIN** needs to be assigned to you.

#### Transactions for SAP Fiori Launchpad Content Manager

The _SAP Fiori launchpad content manager_ allows you to make system-wide or client-specific changes.

System-wide changes are stored in the configuration scope and client-specific changes are stored in customizing scope. Depending on the scope of your changes, use the SAP Fiori app in the launchpad or one of the following transactions in SAP GUI:

### Transactions for the Launchpad Content Manager

- System-wide changes: /UI2/FLPCM_CONF
- Client-specific changes: /UI2/FLPCM_CUST

Note

Form the launchpad, you can only start the _SAP Fiori launchpad content manager_ in the client-specific scope.

- /UI2/FLPCM_CONF
    - Allows you to make system-wide changes (configuration scope).
    - SAP delivers predefined catalogs in the configuration scope.
- /UI2/FLPCM_CUST
    - Allows you to make changes for the current client (customizing scope). These changes supersede configuration settings.
    - Displays content available in the current client. In addition, cross-client content is displayed but cannot be edited here. You can filter the _Scope_ column for _Customizing_ to display only client-specific content.

End users can adjust content defined by the administrator and save their preferences in the personalization scope. These settings supersede customizing and configuration settings.

The _SAP Fiori launchpad content manager_ offers the following features:

### SAP Fiori Launchpad Content Manager

- Exploring launchpad content
- Creating and maintaining catalogs
- Maintaining role assignment
- Displaying the service activation status for apps
- Displaying issues with launchpad content

## Creating Business Catalogs using SAP Fiori Launchpad Content Manager

![Screenshot showing the SAP Fiori Launchpad Content Manager.](https://learning.sap.com/service/media/topic/b1710316-66c1-435c-b1d6-e71c56dbc983/ADM945_24_en-US_media/ADM945_24_en-US_images/02_01_SAPFioriLaunchpadContentManager.png "Screenshot showing the SAP Fiori Launchpad Content Manager.")

Note

The launchpad content manager only loads persisted content when the session is started. During a running session, there is no further check whether the displayed entities are still up to date. This can lead to data inconsistencies when changes are made in another session of the launchpad content manager or in the launchpad designer.

### Creating Catalogs

You can set up your content from scratch by creating a new catalog and adding content to it. You can add or remove reference tiles and reference target mappings to catalogs.

![Screenshot showing the steps to create SAP Fiori Catalog.](https://learning.sap.com/service/media/topic/b1710316-66c1-435c-b1d6-e71c56dbc983/ADM945_24_en-US_media/ADM945_24_en-US_images/02_01_CreateSAPFioriCatalog.png "Screenshot showing the steps to create SAP Fiori Catalog.")

## Practice System Exercise: Create Business Catalogs

Select Start Exercise to start the simulation.

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_54B47DCEC70E2382:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

### Business Example

You want to create authorizations for end users to work with SAP Fiori apps.

As an example we have chosen the following SAP Fiori apps that represent the different application types:

- Display G/L Account Balances (New), (SAPUI5 Analytical) - App ID: **F0707A**
    
- Manage Banks, (SAPUI5 Transactional) - App ID: **F1574**
    
- Display G/L Account Balances For Ledger, (SAP GUI Transaction) - App ID: **FAGLB03**
    
- Material Documents Overview, (SAPUI5 Analytical) - App ID: **F1077**
    
- Physical Inventory Analysis, (Web Dynpro) - App ID: **F2913**
    

These example apps should be used in two different job profiles: accounting manager and inventory manager. Therefore, two different business catalogs and afterward, two roles are created in the following exercises to segregate the authorizations for these two job profiles.

- #### ADM945_##_BC_FIN_ACCOUNT
    
    - Display G/L Account Balances (New)
        
    - Manage Banks
        
    - Display G/L Account Balances For Ledger
        
- #### ADM945_##_BC_INVENTORY_MGMT
    
    - Material Documents Overview
        
    - Physical Inventory Analysis
        

Note

In this exercise, when an object name or value contains ##, replace ## by the number your trainer assigned to you.

![Screenshot showing the ADM945 App Overview.](https://learning.sap.com/service/media/topic/b5b2f7db-1597-46bd-9c66-e42fbfb846e1/ADM945_24_en-US_media/ADM945_24_en-US_images/ADM945_App_Overview.png "Screenshot showing the ADM945 App Overview.")

![Illustration showing the ADM945 Catalogs Overview.](https://learning.sap.com/service/media/topic/b5b2f7db-1597-46bd-9c66-e42fbfb846e1/ADM945_24_en-US_media/ADM945_24_en-US_images/ADM945_Catalogs_Overview.png "Illustration showing the ADM945 Catalogs Overview.")

### Task 1: Create SAP Fiori Catalogs

Since SAP-delivered business catalogs are not sufficient for your business purposes, you want to create your custom business catalogs for an accounting manager and inventory manager and fill the catalogs with the required SAP Fiori apps.

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
        
2. Start the _Launchpad Content Manager: Client-Specific_ app from the _Fiori Launchpad_ space.
    
    1. On the SAP Fiori Launchpad home screen, choose the _Fiori Launchpad_ space.
        
    2. Launch the _Launchpad Content Manager: Client-Specific_ app.
        
        #### Result
        
        The WebGui Transaction opens.
        
    3. Alternatively, you can start transaction **/UI2/FLPCM_CUST** from SAP GUI. To do so, enter **/n/ui2/flpcm_cust** in the OK field of the SAP GUI.
        
    4. Ensure that the _Catalogs_ tab is selected.
        
3. First, create a business catalog for the accounting manager. Enter **ADM945_##_BC_FIN_ACCOUNT** as catalog ID, and **Financial Accounting Catalog ##** as catalog title.
    
    Hint
    
    Be sure to enter the ID using capital letters.
    
    1. On the _Catalogs_ tab of the _Launchpad Content Manager: Client-Specific (Customizing)_, choose _Create_.
        
    2. In the _New ID_ field, enter **ADM945_##_BC_FIN_ACCOUNT**.
        
    3. In the _New Title_ field, enter **Financial Accounting Catalog ##**.
        
    4. Choose _Continue_.
        
        #### Result
        
        The system will prompt for a customizing transport request since you are creating a new customizing object.
        
    5. Create a new customizing request or select a request if there is one.
        
    6. Choose _Continue_.
        
4. Add tile and target mapping references to the **Financial Accounting Catalog ##** catalog for the following SAP Fiori apps:
    
    - Display G/L Account Balances - App ID: **F0707A**
        
    - Manage Banks - App ID: **F1574**
        
    - Display G/L Account Balances For Ledger - App ID: **FAGLB03**
        
    
    From the SAP Fiori apps reference library, you also know the following:
    
    - The relevant semantic object
    - The relevant action
    
    1. In the _Launchpad Content Manager: Client-Specific (Customizing)_, ensure that the tab _Catalogs_ is selected.
        
    2. Search for your catalog _ADM945_##_BC_FIN_ACCOUNT_ by using the _Search Catalogs_ field.
        
    3. Select your catalog _ADM945_##_BC_FIN_ACCOUNT_.
        
    4. At the bottom (area _Content in Catalog..._), choose _Add Tiles/Target Mappings_ → _Add Tiles/TMs to Selected Catalog_.
        
        Note
        
        You will have to repeat this step **three** times since you are adding three SAP Fiori apps to the catalog.
        
    5. On the _Add Tiles/Target Mappings as References to Catalog..._ screen, search for either app title, app ID, semantic object, or action.
        
    6. Select the right app form the result list and choose _Add Tile/TM Reference_.
        
        Note
        
        Several results might be displayed. Make sure you choose the app with both tile and target mapping. Also double-check that you have chosen the right application type (column _App Type_).
        
    
    #### Result
    
    Back on the _Launchpad Content Manager: Client-Specific (Customizing)_ screen, ensure that _Catalogs_ tab is selected. There are three SAP Fiori apps in the _ADM945_##_BC_FIN_ACCOUNT_ catalog.
    
5. Create another business catalog for the inventory manager. Enter **ADM945_##_BC_INVENTORY_MGMT** as catalog ID and **Inventory Management Catalog ##** as catalog title.
    
    Hint
    
    Be sure to enter the ID using capital letters.
    
    1. In the _Launchpad Content Manager: Client-Specific (Customizing)_, ensure that the _Catalogs_ tab is selected.
        
    2. Choose _Create_.
        
    3. In the _New ID_ field, enter **ADM945_##_BC_INVENTORY_MGMT**.
        
    4. In the _New Title_ field, enter **Inventory Management Catalog ##**.
        
    5. Choose _Continue_.
        
        #### Result
        
        The system will prompt for a customizing transport request since you are creating new customizing objects.
        
    6. Select the request you created in the previous step.
        
    7. Choose _Continue_.
        
6. Add tile and target mapping references to the **Inventory Management Catalog ##** catalog for the following SAP Fiori Apps:
    
    - Material Documents Overview - App ID: **F1077**
        
    - Physical Inventory Analysis - App ID: **W0058**
        
    
    From the SAP Fiori apps reference library, you also know the following:
    
    - The relevant semantic object
    - The relevant action
    
    1. In the _Launchpad Content Manager: Client-Specific (Customizing)_, ensure that the _Catalogs_ tab is selected.
        
    2. Search for your catalog _ADM945_##_BC_INVENTORY_MGMT_ by using the _Search Catalogs_ field.
        
    3. Select your catalog _ADM945_##_BC_INVENTORY_MGMT_.
        
    4. At the bottom (area _Content in Catalog..._), choose _Add Tiles/Target Mappings_ → _Add Tiles/TMs to Selected Catalog_.
        
        Note
        
        You will have to repeat this step **two** times since you are adding two SAP Fiori apps to the catalog.
        
    5. On the _Add Tiles/Target Mappings as References to Catalog..._ screen, search for either app title, app ID, semantic object, or action.
        
    6. Select the right app form the result list and choose _Add Tile/TM Reference_.
        
        Note
        
        Several results might be displayed. Make sure you choose the app with both tile and target mapping. Also double-check that you have chosen the right application type (column _App Type_).
        
        For the _Physical Inventory Analysis_, the app ID is not maintained in the content manager. Search for the title or semantic object/action instead.
        
    
    #### Result
    
    Back on the _Launchpad Content Manager: Client-Specific (Customizing)_ screen, ensure that _Catalogs_ tab is selected. There are two SAP Fiori apps in the _ADM945_##_BC_INVENTORY_MGMT_ catalog.
    

## Creating Business Catalogs using SAP Fiori Launchpad Designer

![Screenshot showing the SAP Fiori Launchpad Designer.](https://learning.sap.com/service/media/topic/e0736b5d-ed6d-4297-9ac2-efb95a826680/ADM945_24_en-US_media/ADM945_24_en-US_images/FLP_Designer.png "Screenshot showing the SAP Fiori Launchpad Designer.")

The _SAP Fiori Launchpad Designer_ is a web-based tool for creating, configuring and customizing catalogs, groups and tiles.

Note

To access _SAP Fiori launchpad designer_ from the SAP Fiori launchpad, the authorization role **SAP_FLP_ADMIN** needs to be assigned to you.

You can also open _SAP Fiori launchpad designer_ using transactions in SAP GUI.

The customizing layer is accessed in the transaction /UI2/FLPD_CUST or via a tile in the SAP Fiori launchpad. It is client-specific.

The configuration layer is cross-client and is accessed in the transaction /UI2/FLPD_CONF or via a tile in the SAP Fiori launchpad. It is client-independent .

### Transactions for SAP Fiori Launchpad Designer

- System-wide changes: /UI2/FLPD_CONF
- Client-specific changes: /UI2/FLPD_CUST

![Screenshot showing the catalog view of SAP Fiori Launchpad Designer.](https://learning.sap.com/service/media/topic/e0736b5d-ed6d-4297-9ac2-efb95a826680/ADM945_24_en-US_media/ADM945_24_en-US_images/02_01_SAPFioriUIAuthorization_003.png "Screenshot showing the catalog view of SAP Fiori Launchpad Designer.")

Hint

Creating catalogs, tiles and target mappings with the launchpad designer is no longer recommended. For creating tiles and target mappings, use the _launchpad app manager_ instead. For creating business catalogs, use _SAP Fiori launchpad content manager_.

![On the left, screenshot showing the plus icon to create a new SAP Fiori catalog. On the right, screenshot showing the Create Catalog dialox box.](https://learning.sap.com/service/media/topic/e0736b5d-ed6d-4297-9ac2-efb95a826680/ADM945_24_en-US_media/ADM945_24_en-US_images/02_01_SAPFioriUIAuthorization_004.png "On the left, screenshot showing the plus icon to create a new SAP Fiori catalog. On the right, screenshot showing the Create Catalog dialox box.")

To create a new SAP Fiori catalog, use the plus icon (+) on the button of the SAP Fiori Launchpad Designer and provide a title and ID.

![Screenshots on creating apps reference to own catalog.](https://learning.sap.com/service/media/topic/e0736b5d-ed6d-4297-9ac2-efb95a826680/ADM945_24_en-US_media/ADM945_24_en-US_images/02_01_SAPFioriUIAuthorization_005.png "Screenshots on creating apps reference to own catalog.")

SAP delivers predefined catalogs. The tile and target mapping is defined in the technical catalog which is marked with the ID *_TC_". SAP also delivers sample and ready to use business catalogs as recommendation. They are marked with the ID *_BC_*.

In case you want to define your own catalog, you can reference the tiles and target mappings from one of the SAP-delivered catalogs.

The tiles from the tile view can be referenced via drag and drop, the tiles and target mappings from the table view using the _Create Reference_ footer button from the original catalog. A dialog displays where you can choose the catalog that you want to copy the information to.

Hint

Do not modify the SAP-delivered catalogs or their tiles and target mappings. Always use the technical catalog as a reference.