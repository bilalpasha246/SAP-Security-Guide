## Issues with Launchpad Content

#### Displaying Issues with Launchpad Content

The launchpad content manager displays issues with launchpad content.

- The catalog state is different on the configuration and the customizing scope.
- References to tiles and target mappings cannot be resolved.
- There are issues with the configuration of tile and target mapping.

### Scope-Related Catalog Issues

The launchpad content manager indicates if the state of a catalog differs on the configuration and the customizing scope.

The launchpad designer allows you to make client-specific changes to cross-client catalogs (for example, changing the catalog title or adding tiles). In this case, a copy of the cross-client catalog is created in the customizing scope. This copy has the same ID as the original catalog in the configuration scope. If the original catalog contains original tiles/target mappings, the copied catalog includes these objects as originals with the same ID. The copied catalog in customizing is now decoupled from the catalog in the configuration scope. Any changes made in the configuration scope (except changes of texts in tiles or target mappings) are no longer reflected in the customizing scope.

Note

To prevent these inconsistencies, cross-client catalogs cannot be changed in the client-specific launchpad content manager. We recommend you to change the cross-client catalog in the configuration scope (transaction /UI2/FLPM_CONF) or to copy the catalog in the customizing scope (transaction /UI2/FLPM_CUST) and make changes for the current client only

Note

To display the issue open the _Catalogs_ tab in the client-specific launchpad content manager (transaction /UI2/FLPM_CUST). Filter the _Scope_ columns for _Customization_ and check the value in _Status in Current Client_ column.

|Value|Description|
|---|---|
|Original|The catalog was created in the current client and does not exist in the configuration scope.|
|Changed|The catalog was created in the configuration scope and changed in the current client using the launchpad designer, which means that it is now decoupled from the original catalog on the configuration scope. If the original catalog is now changed in the configuration scope, these changes will not be reflected in the current client.|
|Outdated|The catalog was created in the configuration scope and changed in the current client using the launchpad designer, which means that it is now decoupled from the original catalog on the configuration scope. The original catalog was then changed in the configuration scope. The catalog on the current client is outdated because the changes in the configuration scope are no longer reflected. If the catalog is now changed in the customizing scope, its status will be set to "Changed" again.|

If a catalog is outdated, you have the following options:

- Update the catalog to the latest changes of the configuration scope. Changes made in the customizing scope will be lost.
- Continue working with the existing changes of the customization scope. In this case, you do not receive the latest changes provided in the configuration scope.

### Issues with Tiles and Target Mappings

The launchpad content manager indicates broken references and issues with the configuration of tiles and target mappings.

To display the issue open the _Tiles/Target Mappings_ tab in the launchpad content manager. Check the _Title / Subtitle / Information_ column to get a first hint about the issue:

### Issues with Tiles and Target Mappings

- Reference Lost to Backend Catalog
- Reference Lost
- Configuration Error

To get further information on the issue, open the context menu for a selected row and choose _Status Details_.

Description of the Issues:

Reference Lost to Backend Catalog

The selected tile/target mapping refers to an original tile/target mapping which was defined in the backend using the launchpad app manager.

The reference is broken because the original tile/target mapping or the catalog in which the originals were defined do not exist on the front-end server.

Reference Lost

The selected tile/target mapping refers to an original tile/target mapping which was defined in another catalog.

The reference is broken because the original tile/target mapping or the catalog in which the originals were defined do not exist in the system or client.

Configuration Error

There are several reasons for a tile/target mapping configuration issue.

Note

For details on how to solve these issues and the reasons for configuration errors see section Issues with Tiles and Target Mappings on help.sap.com

([https://help.sap.com/docs/ABAP_PLATFORM_NEW/a7b390faab1140c087b8926571e942b7/bff8d59f71384fcf84b61df55a6bfb66.html)](https://help.sap.com/docs/ABAP_PLATFORM_NEW/a7b390faab1140c087b8926571e942b7/bff8d59f71384fcf84b61df55a6bfb66.html)

.

## Adjust Launchpad Content after an Upgrade

After an upgrade from a lower on-premise version to a higher one, it might be necessary to adjust your launchpad content due to some changes. Applications can become obsolete or deprecated and you might need to add a successor.

Transactions and their status allow you to find out if an app is still in use or if it needs to be replaced. Transactions are assigned to launchpad app descriptor items belonging to a SAP Fiori app. SAP assigns the transaction in the launchpad app manager and maintains the status in _Maintain Authorization Default Values_ (transaction SU22) .

In the _Launchpad Content Manager_, you can check the transaction status and, if required, add new tiles and target mappings to your catalog using the associated successor transactions.

Note

This new feature is available as of SAP S/4HANA 2021.

Supported app types are:

- SAP GUI transactions
- SAPUI5 SAP Fiori applications

![Screenshot showing transaction status in Launchpad Content Manager.](https://learning.sap.com/service/media/topic/a505c391-77b7-4a56-8de6-052b4c5a2ee8/ADM945_24_en-US_media/ADM945_24_en-US_images/Transaction%20Status%20in%20CM.png "Screenshot showing transaction status in Launchpad Content Manager.")

### Checking the Status of Launchpad Content

On the _Tile/ Target Mappings_ tab, the fields **Transaction** and **Transaction Status** are displayed by default. They show the status of the relevant content. On the tabs _Catalogs_ and _Roles_, you see an aggregated status of the associated transactions.

#### Transaction Status in the Launchpad Content Manager

|Transaction Status|Description|Action|
|---|---|---|
|Deprecated|This status is a precursor of the status _Obsolete_. The app is not being developed anymore and is planned to be removed in the near future. The app can still be used.|When the status was set to _Deprecated_, this usually means that launchpad content with an associated successor transaction is in place. We encourage you to use the successor and avoid using the deprecated content, as it will be removed in an upcoming version.|
|Obsolete|The app does not meet important functional requirements and should therefore no longer be used.|Remove the launchpad content with the obsolete transaction and add launchpad content with the associated successor transaction instead.|
|Remote Content|The status of remote content (system alias is not mapped to local) cannot be determined.|You have to manually check in the back-end system if the app is up-to-date.|

If the status field is empty, the launchpad content is either up-to-date or no checks are needed, because, for example, the app type is not supported.

### Adjusting Launchpad Content with Associated Successor Transactions to your Business Catalog

![Screenshot on adjusting launchpad content.](https://learning.sap.com/service/media/topic/a505c391-77b7-4a56-8de6-052b4c5a2ee8/ADM945_24_en-US_media/ADM945_24_en-US_images/Adjusting%20Launchpad%20Content.png "Screenshot on adjusting launchpad content.")

You can view and directly update your launchpad content with the associated successor transactions in the _Launchpad Content Manager_. In order to do that, you need to perform following actions:

1. Open the_Launchpad Content Manager_ (transaction /UI2/FLPCM_CUST) and go to the _Catalogs_ tab.
2. In the upper table, select the relevant catalog in which the obsolete or deprecated launchpad content is assigned to.
3. In the lower table, you can see a list of tiles and target mappings and their transaction status. Click _Other Functions_  → _Show/ Add Successors_.
4. If new content with an associated successor transaction is available, a new window is opened. Select the relevant tiles and target mappings and click _Add Tile/ TM Reference_.
5. Remove the deprecated or obsolete tiles and target mappings from your catalog.

After you have adjusted your launchpad content in the launchpad content manager, you also need to:

1. Add your new tiles to your page and remove the obsolete or deprecated ones.
2. Activate the corresponding OData and ICF services of the newly added launchpad content.
3. Adjust the corresponding roles and authorizations using the transactions:
    - Profile Generator: Upgrade and First Installation (transaction SU25)
    - Role Maintenance (transaction PFCG)

## Practice System Exercise: Adjusting Launchpad Content with Associated Successor

Select Start Exercise to start the simulation.

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_A0C4658E36978DB4:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

### Business Example

After an upgrade you want to check if it might be necessary to adjust your launchpad content due to some changes.

### Task 1: Search for catalogs containing deprecated transactions and adjust the catalog content.

Use the _Launchpad Content Manager_ to search for catalogs containing deprecated transactions and to adjust the catalog content.

#### Steps

1. Log on to SAP Fiori Launchpad of system S4D with your **train-##** user. Use Google Chrome.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. In the _Microsoft Windows_ start menu, choose _Google Chrome_.
        
    2. In _Google Chrome_, go to _Bookmarks_.
        
    3. In _Bookmarks_, choose _10 Development_ → _s4dhost_ → _10 S4D SAP Fiori Launchpad_.
        
2. Start the _Launchpad Content Manager: Client-Specific_ app from the _Fiori Launchpad_ space.
    
    1. On the SAP Fiori Launchpad home screen, choose the _Fiori Launchpad_ space.
        
    2. Launch the _Launchpad Content Manager: Client-Specific_ app.
        
        #### Result
        
        The WebGui Transaction opens.
        
    3. Alternatively, you can start transaction **/UI2/FLPCM_CUST** from SAP GUI. To do so, enter **/n/ui2/flpcm_cust** in the OK field of the SAP GUI.
        
    4. Ensure that the _Catalogs_ tab is selected.
        
3. Search for catalogs containing deprecated transactions.
    
    1. On the _Catalogs_ tab of the _Launchpad Content Manager: Client-Specific (Customizing)_, select column _Transaction Status_.
        
    2. Choose _Set Filter_.
        
    3. In the _Transaction Status_ field of the screen _Determine Values for Filter Criteria_, enter **Contains deprecated transactions**.
        
    4. Choose _OK_.
        
    5. Choose _Execute (Enter)_.
        
        #### Result
        
        The result shows that your catalog _ADM945_##_BC_FIN_ACCOUNT_ contains deprecated transactions
        
4. Select your **Financial Accounting Catalog ##** catalog and adjust the Launchpad content.
    
    1. Select your catalog _ADM945_##_BC_FIN_ACCOUNT_.
        
    2. At the bottom (area _Content in Catalog..._), choose _Other Functions_ → _Show/Add Successors_.
        
        #### Result
        
        The result shows the successor tile/target mapping for Transaction F1574:
        
        Transaction: _F1574A_
        
        Title: _Manage Banks - Cash Management_
        
    3. Select the transaction _F1574A_ form the result list and choose _Add Tile/TM Reference_.
        
        #### Result
        
        The system will prompt for a customizing transport request since you are creating new customizing objects.
        
    4. Select the request you created in the previous exercise.
        
    5. Choose _Continue_.
        
    
    #### Result
    
    Now you have added the the app _Manage Banks - Cash Management_ to your _ADM945_##_BC_FIN_ACCOUNT_ catalog.
    
5. Select your **Financial Accounting Catalog ##** catalog and delete the deprecated transaction _F1574_
    
    1. Select your catalog _ADM945_##_BC_FIN_ACCOUNT_.
        
    2. At the bottom (area _Content in Catalog..._), select the transaction F1574 from the list of tiles/target mappings .
        
    3. Choose _Remove Tiles/Target Mappings_.
        
    4. Select _Tiles_ and _Target Mappings_ on the screen _Remove References from Catalog_.
        
    5. Choose _Continue_.
        
        The screen _Messages_indicates that the tile and the target mapping cannot be removed because they are assigned to a Launchpad space
        
    6. Choose _Close_.
        
6. Choose _SAP_ logo to get back to the FLP home screen.
    

### Task 2: Adjust the page content

After adjusting the catalog content you also have to adjust the page content.

#### Steps

1. In the _Manage Launchpad Pages_ app, remove the _Manage Banks_ app and add the _Manage Banks - Cash Management_app to the **Z_ADM945_##_BANK_MGMT** page.
    
    1. On the SAP Fiori Launchpad home screen, choose the _Fiori Launchpad_ space.
        
    2. Launch _Manage Launchpad Pages_ app.
        
    3. Select _Z_ADM945_##_PG_BANK_MGMT_.
        
    4. Choose _Edit_ (pencil icon).
        
    5. Choose _Remove_ on the tile _Manage Banks_ to remove the _Manage Banks_app.
        
    6. In the _Derived from Roles_ section on the right-hand side, choose _Add_ for the _Manage Banks - Cash Management_ app.
        
        #### Result
        
        The tile is added to the _Quick Access_ section.
        
    7. Choose _Save_ ind the lower right-hand corner.
        
    8. Choose _Back_.
        

### Task 3: Delete the deprecated app from the catalog

Finally you have to delete the deprecated app from the catalog.

#### Steps

1. Start the _Launchpad Content Manager: Client-Specific_ app from the _Fiori Launchpad_ space.
    
    1. On the SAP Fiori Launchpad home screen, choose the _Fiori Launchpad_ space.
        
    2. Launch the _Launchpad Content Manager: Client-Specific_ app.
        
        #### Result
        
        The WebGui Transaction opens.
        
    3. Alternatively, you can start transaction **/UI2/FLPCM_CUST** from SAP GUI. To do so, enter **/n/ui2/flpcm_cust** in the OK field of the SAP GUI.
        
    4. Ensure that the _Catalogs_ tab is selected.
        
    5. Search for your catalog _ADM945_##_BC_FIN_ACCOUNT_ by using the _Search Catalogs_ field.
        
2. Select your **Financial Accounting Catalog ##** catalog and delete the deprecated transaction _F1574_
    
    1. Select your catalog _ADM945_##_BC_FIN_ACCOUNT_.
        
    2. At the bottom (area _Content in Catalog..._), select the transaction F1574 from the list of tiles/target mappings .
        
    3. Choose _Remove Tiles/Target Mappings_.
        
    4. Select _Tiles_ and _Target Mappings_ on the screen _Remove References from Catalog_.
        
    5. Choose _Continue_.
        
    
    #### Result
    
    Now the tile and target mapping are deleted from the catalog.