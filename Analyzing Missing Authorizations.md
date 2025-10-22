Objective

After completing this lesson, you will be able to analyze Missing SAP Fiori Authorizations.

## Missing Proposals for OData Services

When entering a SAP Fiori catolog into the role menu the Odata Services assigned to the apps contained in the catalog are automatically entered in the role menu. In the case of problems with a SAPUI5 app, use the SAP Fiori Apps Library to determine which OData Services users require PFCG authorization for. Then check in the corresponding catalog in role maintenance for which OData Services an entry exists for. If problems occur, check if the correct proposals are made for the OData services.

![Screenshots on checking for OData Service proposed in Role Menu.](https://learning.sap.com/service/media/topic/da7db38b-82e8-454e-b97a-927a4d06fae0/ADM945_24_en-US_media/ADM945_24_en-US_images/CheckforODataServiceProposed.png "Screenshots on checking for OData Service proposed in Role Menu.")

### Authorization Maintenance for SAPUI5 Fiori Apps OData Authorization Object

When after entering a catalog in the role menu an entry for an OData service is missing you can enter the value for this OData service manually to the role menu. The OData authorization is maintained by the _Authorization Default_ entry from the PFCG Menu.

Therefore proceed the following steps:

1. Choose the _Insert Node_ button and select **Authorization Default**.
2. Choose **SAP Gateway: Services Groups Metadata** in the _Authorization Default_ field to select the IWSG Service on the FES and enter the name of the TADIR Service.
3. Choose **SAP Gateway Business Suite Enablement - Service** in the _Authorization Default_ field to select the IWSV Service on the BES and enter the name of the TADIR Service.

Note

- TADIR IWSG is the Front-End authorization object
- TADIR IWSV the Back-End object

![Screenshots on authorization maintenance for SAPUI5 Fiori Apps OData Authorization Object.](https://learning.sap.com/service/media/topic/da7db38b-82e8-454e-b97a-927a4d06fae0/ADM945_24_en-US_media/ADM945_24_en-US_images/02_02_SAPFioriODataAuthorization_002.png "Screenshots on authorization maintenance for SAPUI5 Fiori Apps OData Authorization Object.")

Both entries are generating the same S_SERVICE authorization object with different authorization values. The SRV_NAME value of the S_SERVICE authorization object is the hash value of an OData service, not the name. Therefore it is recommended to not maintain S_SERVICE manually.

Note

An IWSG object is only available when the OData service is completely configured.

## Practice System Exercise: Check for OData Service in Role Maintenance

Select Start Exercise to start the simulation.

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_7B709D6555F014B6:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

### Business Example

After creating roles some entries for the OData services might be missing. You need to find the missing authorizations. Therefore you can perform an authorization trace and cross check the information in the SAP Fiori Apps Library.

### Task 1: Check the OData Services in the SAP Fiori Reference Library

Open the SAP Fiori Reference Library and check which OData Services require PFCG authorization for the **Material Documents Overview** app.

#### Steps

1. Open the SAP Fiori Reference Library.
    
    1. In the _Microsoft Windows_ start menu, choose _Google Chrome_.
        
    2. In _Google Chrome_, go to _Bookmarks_.
        
    3. In _Bookmarks_, choose _SAP Fiori_ → _SAP Fiori Apps Reference Library_.
        
2. Explore the **Material Documents Overview** app.
    
    1. Choose _All apps for SAP S/4HANA_.
        
    2. Choose _All apps_.
        
    3. In the _Search_ field, enter **Material Documents Overview** or alternatively the app ID: **F1077**.
        
    4. Choose _Material Documents Overview_.
        
    5. Below the subtitle, make sure that the correct product and release version _SAP S/4HANA 2023_ with the latest FPS are selected.
        
    6. Select the _IMPLEMENTATION INFORMATION_ tab.
        
    7. Expand _Configuration_.
        
    
    #### Example
    
    The following OData Services require PFCG authorization:
    
    - MMIM_GR_CANCELLATION_SRV
    - MMIM_MATDOC_OV_SRV
    

### Task 2: Check the OData Services in the Role Menu

#### Steps

1. Log on to the SAP GUI of the system S4D.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        
2. Check the OData Services of the catalog **ADM945_##_BC_INVENTORY_MGMT** in the role menu.
    
    1. Start the Role Maintenance transaction PFCG on the system S4D.
        
    2. Enter the role name: **ADM945_##_BR_INVENTORY**.
        
    3. Choose _Change_.
        
    4. Go to the _Menu_ tab.
        
    5. Expand the catalog **Inventory Management Catalog ##** in the_Role Menu_.
        
        #### Result
        
        The following OData Services are included in the catalog:
        
        - R3TR IWSG ZMMIM_GR_CANCELLATION_SRV_0001
        - R3TR IWSG ZMMIM_MATDOC_OV_SRV_0001
        
        - R3TR IWSV MMIM_GR_CANCELLATION_SRV_0001
        - R3TR IWSV MMIM_MATDOC_OV_SRV_0001
        
    6. Choose _Back_.