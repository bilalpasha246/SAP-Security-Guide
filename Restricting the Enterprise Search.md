
Objective

After completing this lesson, you will be able to manage Restrictions for Enterprise Search.

## Restricting the Enterprise Search

### Overview

When users want to search for data in the SAP Fiori launchpad, the SAP Fiori search accesses the SAP HANA enterprise search, SAP Enterprise search helps you find apps and central business objects from the search bar. This is a search solution providing unified, comprehensive, and secure real-time access to enterprise data and information from within and outside of a company. The search returns both structured data (business objects) and unstructured data (HTML files, presentations, documents) from SAP systems and other search providers and allows direct access to the associated applications and actions.

![Illustration on SAP Fiori System Architecture – Enterprise Search.](https://learning.sap.com/service/media/topic/db75adf2-f272-42f0-aaab-49e76b20ca7b/ADM945_24_en-US_media/ADM945_24_en-US_images/U5L2_EnterpriseSearch_01.png "Illustration on SAP Fiori System Architecture – Enterprise Search.")

Every application that uses SAP AS ABAP as its underlying technology platform can use Enterprise Search as the technology for basic searches. Enterprise Search allows you to search all structured data in an application in a unified way. Enterprise Search contains tools for creating and changing search models.

SAP HANA is the database used for Enterprise Search. Enterprise Search enables direct search access to your business data stored in the tables in SAP HANA.

### Activation of the Enterprise Search – Fundamentals

The Enterprise Search is activated for each client individually. Mainly it should be executed on clients with SAP Fiori usage and extended need for search capabilities.

![Illustration on activation of the Enterprise Search.](https://learning.sap.com/service/media/topic/db75adf2-f272-42f0-aaab-49e76b20ca7b/ADM945_24_en-US_media/ADM945_24_en-US_images/U5L2_EnterpriseSearch_02.png "Illustration on activation of the Enterprise Search.")

The necessary steps to enable the SAP Fiori search in the SAP Fiori launchpad are part of the task list for activating SAP Enterprise Search. The task list, _SAP_ESH_INITIAL_SETUP_WRK_CLIENT_, provides the automatic initial setup of Enterprise Search in the work client.

Note

The user who executes the enterprise search setup tasks owns the administrator role _SAP_ESH_LOCAL_ADMIN_ or a role which has at least all authority objects of the role _SAP_ESH_LOCAL_ADMIN_.

The search for business objects is enabled through corresponding search models.

Since the search connectors are searching with a specific scope only relevant models are beneficial for the user. Based on the used applications the relevant search connectors can be found in different places:

- SAP Fiori Apps Reference Library
- SAP Notes
- SAP Standard Business Roles
- ESH Modeler

A collection made from all of these different sources should be used to get all the relevant search models.

As an example the selection of search models using the SAP Fiori Apps Reference Library is shown on the figure below. Based on the used applications the relevant search connectors can be found in the SAP Fiori Apps Reference Library. Therefore select all relevant apps for the role you want to limit the cope of the search and aggregate them.

![Screenshots on selecting models for the Enterprise Search – SAP Fiori Apps.](https://learning.sap.com/service/media/topic/db75adf2-f272-42f0-aaab-49e76b20ca7b/ADM945_24_en-US_media/ADM945_24_en-US_images/U5L2_EnterpriseSearch_03.png "Screenshots on selecting models for the Enterprise Search – SAP Fiori Apps.")

### Restriction of the Enterprise Search

![Illustration on restricting the Search Object Access in the SAP Fiori Launchpad.](https://learning.sap.com/service/media/topic/db75adf2-f272-42f0-aaab-49e76b20ca7b/ADM945_24_en-US_media/ADM945_24_en-US_images/U5L2_EnterpriseSearch_04.png "Illustration on restricting the Search Object Access in the SAP Fiori Launchpad.")

Enabling access to all search connectors might have a bad influence on the performance of the system. Not every user needs access to all search connectors. Restricting the Enterprise Search restricts access to the necessary search connectors.

This can be achieved by restricting the authorizations for the authorization objects _S_ESH_CONN_ and _SDDLVIEW_.

As an example we look at the enterprise search models used in the SAP Fiori app Material Documents Overview

Each classical search model has a corresponding CDS based search model. The following table provides an overview of the search models:

#### Example for Search Model

|Model Name|Classical Model|CDS Based Model|
|---|---|---|
|Material Document|MATERIAL_DOCUMENT_H|ESH_S_MATDOC|
|Physical Inventory|MATERIAL_INVENTORY_H|ESH_S_PHYSINVTRY|

The required authorizations for the search models are part of the authorization defaults:

R3TR IWSV MMIM_MATDOC_OV_SRV 0001

When creating roles, depending on what search model will be used, the following authorizations shall be taken over into the role:

#### Authorizations for Search Model

|Search Model|Authorization Object|Field Name and Value|
|---|---|---|
|MATERIAL_DOCUMENT_H|S_ESH_CONN|TEMPL_NAME =<br><br>MATERIAL_DOCUMENT_H|
|MATERIAL_INVENTORY_H|S_ESH_CONN|TEMPL_NAME =<br><br>MATERIAL_INVENTORY_H|
|ESH_S_MATDOC|SDDLVIEW|DDLSCRNAME =<br><br>ESH_S_MATDOC|
|ESH_S_PHYSINVTRY|SDDLVIEW|DDLSCRNAME =<br><br>PHYSINVTRY|

![Screenshots on default authorization values for Search Model.](https://learning.sap.com/service/media/topic/db75adf2-f272-42f0-aaab-49e76b20ca7b/ADM945_24_en-US_media/ADM945_24_en-US_images/U5L2_EnterpriseSearch_05.png "Screenshots on default authorization values for Search Model.")

![Screenshots on limiting authorizations in profile.](https://learning.sap.com/service/media/topic/db75adf2-f272-42f0-aaab-49e76b20ca7b/ADM945_24_en-US_media/ADM945_24_en-US_images/U5L2_EnterpriseSearch_06.png "Screenshots on limiting authorizations in profile.")

Another Example for enterprise search models in Bank Relationship Management is shown in SAP Note 2847374 - Enterprise Search Models in Bank Relationship Management: Availability of CDS based search models in SAP S/4HANA 1909.

![Illustration on Enterprise Search Setup Approach.](https://learning.sap.com/service/media/topic/db75adf2-f272-42f0-aaab-49e76b20ca7b/ADM945_24_en-US_media/ADM945_24_en-US_images/U5L2_EnterpriseSearch_07.png "Illustration on Enterprise Search Setup Approach.")

​To ensure a proper restriction of the Enterprise Search please make sure:

- All manifestations of the S_ESH_CONN and SDDLVIEW authorization objects are restricted
- The user has no SAP_ALL authorization profile
- The authorizations in standard SAP Business Roles are set accordingly

## Practice System Exercise: Check Restrictions for Enterprise Search

Select Start Exercise to start the simulation.

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_3DAA5B3826848CAF:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

### Business Example

You want to check the restrictions for SAP Enterprise Search.

### Steps

1. In _Google Chrome_, open the SAP Fiori Reference Library.
    
    1. In the _Microsoft Windows_ start menu, choose _Google Chrome_.
        
    2. In _Google Chrome_, go to _Bookmarks_.
        
    3. In _Bookmarks_, choose _SAP Fiori_ → _SAP Fiori Apps Reference Library_.
        
2. Search for the app _Display G/L Account Balances_ and check for which OData service the user will require PFCG authorization.
    
    1. In the _SAP Fiori Apps Reference Library_, choose _SAP Fiori Apps for SAP S/4HANA_.
        
    2. Choose _All Apps_.
        
    3. In the _Search_ field, enter **Material Documents Overview**.
        
    4. Choose _Material Documents Overview_.
        
    5. Below the subtitle, select the release version _SAP S/4HANA 2023_ latest FPS.
        
    6. Select the _IMPLEMENTATION INFORMATION_ tab.
        
    7. Expand _Configuration_.
        
    8. Check for which OData service the user requires the PFCG authorization .
        
        #### Result
        
        The user requires PFCG authorization for the the OData services _MMIM_MATDOC_OV_SRV_ and _MMIM_GR_CANCELLATION_SRV_.
        

### Task 1: Check the proposals for authorization objects S_ESH_CONN and SDDLVIEW

You want to check the authorization default values for authorization objects **S_ESH_CONN** and **SDDLVIEW** in back-end system S4D.

#### Steps

1. Log on to the SAP GUI of the system S4D.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        
2. Check the authorization proposals for implemented OData service **MMIM_MATDOC_OV_SRV**.
    
    1. Start the transaction SU24.
        
    2. In the _Type of Application_ field, choose **SAP Gateway Business Suite Enablement - Service**.
        
    3. In the _Object Name_ field, choose the input help (F4).
        
    4. Expand the _Restrictions_ area and enter **MMIM_MATDOC_OV_SRV*** in the _Object Name_ field.
        
    5. Choose _Start Search_.
        
    6. Select the search result _R3TR IWSV MMIM_MATDOC_OV_SRV 0001_.
        
    7. Choose _Copy_.
        
    8. Choose _Execute (F8)_.
        
        #### Result
        
        The result list shows the list of data access objects on the back-end server S4D for the service _R3TR IWSV MMIM_MATDOC_OV_SRV__0001_. Among others it also displays the authorization default values for authorization objects _S_ESH_CONN_ and _SDDLVIEW_ .
        

### Task 2: Check the authorization proposals in profile

You want to check the authorization proposals for authorization objects **S_ESH_CONN** and **SDDLVIEW** in the role **ADM945_##_BR_INVENTORY**.

#### Steps

1. Check the authorization proposals in the profile of role **ADM945_##_BR_INVENTORY**.
    
    1. Start the Role Maintenance transaction PFCG.
        
    2. In the _Role_ field, enter **ADM945_##_BR_INVENTORY**.
        
    3. Choose _Change_.
        
    4. Go to the _Authorizations_ tab.
        
    5. Choose _Change Authorization Data_.
        
        #### Result
        
        The pop displays that several IWSG and IWSV services which were proposed due to the _Manage Banks_ app will be removed. The IWSG and IWSV services which were proposed due to the _Manage Banks - Cash Management_ app will be added. This is because you removed an SAPUI5 application in the catalog and added another one.
        
    6. Expand the following nodes: _Object class AAAB_, _Authorization Object SDDLVIEW_ and _Authorizat. 00_.
        
    7. Check the values for the authorization fields.
        
    8. Expand the following nodes: _Object class BC_A_, _Authorization Object S_ESH_CONN_ and _Authorizat. 00_.
        
    9. Check the values for the authorization fields.
        
    10. Choose _Back (F3)_.