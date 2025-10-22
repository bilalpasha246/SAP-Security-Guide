Objective

After completing this lesson, you will be able to analyze SAP Fiori Applications in Business Roles.

## Analysis Tools for SAP Fiori Applications

#### Overview

Developing and updating authorization concepts is part of the life cycle management of applications. The development steps which era needed to have finally available productive roles which considers all business requests regarding prevention of Segregation of Duty (SoD) conflicts and the amount of authorizations for each work place are the same as the steps for development of new applications. Even more importantly, the development of authorization roles are strongly linked with the development of programs and data structures.

![Table showing the analysis tools for SAP Fiori Applications.](https://learning.sap.com/service/media/topic/a9d65472-fd42-4711-8db5-660ef63e6b0a/ADM945_24_en-US_media/ADM945_24_en-US_images/Analysis_Tools_for_SAP_Fiori_Applications.png "Table showing the analysis tools for SAP Fiori Applications.")

With SAP Fiori, new entities like SAP Fiori Tile Catalogs and SAP Fiori Tile Spaces have been introduced so the tools which are available for role developer should consider those new software parts.

SAP will introduce new tools step-by-step or enhance available tools for role developers. The following sections describe tools that are currently available. The will help you to understand the scope and the functions of those tools.

### Search for Applications in Role Menu

The report Search for Applications in Role Menu (RSUSR_ROLE_MENU) is for searching for applications in the role menu. For the first time, the focus was set on searching for SAP Fiori catalogs and authorization default values of the IWSG and IWSV applications.

![Screenshots showing the search for applications in Role Menu.](https://learning.sap.com/service/media/topic/a9d65472-fd42-4711-8db5-660ef63e6b0a/ADM945_24_en-US_media/ADM945_24_en-US_images/05_01_AnalyzeSAPFioriApplicationsInRoles_002.png "Screenshots showing the search for applications in Role Menu.")

The report can be called via the menu node _Roles_ → _Search for Applications in Role Menu_ in transaction SUIM or directly via transaction RSUSR_ROLE_MENU.

This report is available in Front- and Back-End Systems.

Note

See also:

- SAP note 2341600 - SUIM | Search in role menu RSUSR_ROLE_MENU
- SAP note 2356418 - SUIM| RSUSR_ROLE_MENU and SUSR_SUIM_API_RSUSR_ROLE_MENU

![Screenshot showing the search result for applications in Role Menu.](https://learning.sap.com/service/media/topic/a9d65472-fd42-4711-8db5-660ef63e6b0a/ADM945_24_en-US_media/ADM945_24_en-US_images/05_01_AnalyzeSAPFioriApplicationsInRoles_003.png "Screenshot showing the search result for applications in Role Menu.")

The _Search for Applications in Role Menu_ report looks for entries in PFCG menu tab page and is able to list also items like SAP Fiori Tile Catalogs and SAP Fiori Tile Spaces. For example, you can use this report to get better insight if you are working on incidents or defects or if you want to get an overview about an implemented role concept.

### Search for Startable Applications in Roles

The _Search for Startable Applications in Roles_ report helps you to determine whether the applications contained in PFCG roles are startable.

Startable applications are all applications that meet the following criteria:

- The roles contain all of the start authorizations required for the application. This means that both the authorization for the authorization objects S_TCODE, S_SERVICE, S_RFC, and S_START and the authorization for the authorization object defined in transaction SE93 are grouped together.
    
- These required start authorizations are contained in the current profile of the role.
    
- There is no application start lock (transactions SM01_DEV and SM01_CUS).
    

The desired applications are sought in the role menu, the authorization data, and the current profile data of the selected roles.

Only if an application is contained in a generated profile with all of the aforementioned required start authorizations is this application flagged as a 'startable' application. Note that the currently generated profile is sought regardless of the profile status. In obsolete profiles, authorizations that are contained in the role might be missing. Furthermore, obsolete profiles can contain authorizations that have been removed from the role.

![Screenshots showing the search for startable applications in Roles.](https://learning.sap.com/service/media/topic/a9d65472-fd42-4711-8db5-660ef63e6b0a/ADM945_24_en-US_media/ADM945_24_en-US_images/05_01_AnalyzeSAPFioriApplicationsInRoles_004.png "Screenshots showing the search for startable applications in Roles.")

The report can be called via the menu node _Roles_ → _Search for Startable Applications in Roles_ in transaction SUIM or directly via transaction RSUSR_START_APPL.

This report is available in front- and back-end systems.

Note

See also:

- SAP note 2449011 - SUIM | Search for startable applications in roles - RSUSR_START_APPL
- SAP note 2521054 - SUIM| RSUSR_START_APPL: Various problems

## Practice System Exercise: Analyze Roles

Select Start Exercise to start the simulation.

#### Part 1

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_7E79067AD9904C83:uebung)

#### Part 2

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_E96A93935893F49B:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

### Business Example

You are a role developer and you are asked to adapt the role concept, and the appropriate PFCG roles, for use cases with SAP Fiori applications.

You want to check the current situation within the implemented PFCG roles. You try to focus on SAP Fiori related PFCG entities, such as SAP Fiori Tile Catalog, SAP Fiori Tile Spaces, and Authorization Objects related to SAP Fiori apps.

### Task 1: Search for SAP Fiori Applications in the Role Menu

Search for SAP Fiori applications in the role menu of business roles.

#### Steps

1. Log on to the SAP GUI of the system S4D.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        
2. Search for applications in the role menus.
    
    1. Start the User Information System transaction SUIM on the system S4D.
        
    2. Choose _User Information system_ → _Roles_.
        
    3. Start _Search for Applications in Role Menu_.
        
    4. In the _Selection of Roles_ screen area, in the _Role_ field, enter **ADM945_##***.
        
    5. In the _Type of Menu Entry_ field, choose different entry types like _Launchpad Catalog_, _Launchpad Space_ and others.
        
    6. Choose _Execute_ in the bottom right-hand corner.
        
    7. Analyze the result.
        
        The following types of menu entries can be shown:
        
        - Authorization Default Values for Services
        - SAP Fiori Tile Catalog
        - SAP Fiori Tile Group
        - SAP Fiori Tile Space
        
        Hint
        
        You can also start the _Search for Applications in Role Menu_ report via transaction RSUSR_ROLE_MENU or via transaction SA38.
        
    8. Choose _Back (F3)_ twice.
        
3. Search for role menus containing your SAP Fiori tile catalog **ADM945_##_BC_FIN_ACCOUNT**.
    
    1. Start the User Information System transaction SUIM on the system S4D.
        
    2. Choose _User Information system_ → _Roles_.
        
    3. Start _Search for Applications in Role Menu_.
        
    4. In the _Selection by Menu Entries_ screen area, in the _Type of Menu Entry_ field, choose **Launchpad Catalog**.
        
    5. In the _Selection by Menu Entries_ screen area, in the _Catalog_ field , enter **ADM945_##_BC_FIN_ACCOUNT**.
        
    6. Choose _Execute_ in the bottom right-hand corner.
        
    7. Analyze the result.
        
    8. Choose _Back (F3)_ twice.
        
4. Search for role menus containing your SAP Fiori space **Z_ADM945_##_SP_FIN_ACCOUNT**.
    
    1. Start the User Information System transaction SUIM on the system S4D.
        
    2. Choose _User Information system_ → _Roles_.
        
    3. Start _Search for Applications in Role Menu_.
        
    4. In the _Selection by Menu Entries_ screen area, in the _Type of Menu Entry_ field, choose **Launchpad Space**.
        
    5. In the _Selection by Menu Entries_ screen area, in the _Application_ field , enter **Z_ADM945_##_SP_FIN_ACCOUNT**.
        
    6. Choose _Execute_ in the bottom right-hand corner.
        
    7. Analyze the result.
        
    8. Choose _Back (F3)_ twice.
        

### Task 2: Search for SAP Fiori Applications that are Startable in Roles

Search for SAP Fiori applications that are startable in roles on the system S4D.

#### Steps

1. Log on to the SAP GUI of the system S4D.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        
2. Search for OData Service-based SAP Fiori applications that are startable in roles of the system S4D.
    
    1. Start the User Information System transaction SUIM on the system S4D.
        
    2. Choose _User information system_ → _Roles_.
        
    3. Start _Search for Startable Applications in Roles_.
        
    4. In the _Selection of Roles_ screen area, in the _Role_ field, enter **ADM945_##***.
        
    5. In the _Selection by Application Type_ screen area, in the _Application Type_ field, choose _SAP Gateway: Service Groups Metadata_.
        
    6. Choose _Execute_ in the bottom right-hand corner.
        
    7. Analyze the result.
        
        Note
        
        You are going to start the report on the system S4D. The result of the report, with the filter SAP Gateway: Service Groups Metadata, should show in the _Name of Application (TCode(Service/RFC Function)_ column , which shows the name of all applications implemented as the object type IWSG.
        
        This object type is related to software pieces, which act as an entry point to OData services often used in SAP Fiori applications. They are found in front-end systems for SAP Fiori landscapes. From the result list, you can navigate directly into the PFCG transaction, by double-clicking a line.
        
        Hint
        
        Keep in mind that the authorization to start a service is only available if the authorization is part of the role profile and is available in the user buffer.
        
        The report, with filter SAP Gateway: Service Groups Metadata, lists all IWSG entries available in a role independently, if that IWSG service is inserted via menu entry, or manually via the authorization object S_SERVICE on the _Authorization_ tab of PFCG.
        
        Hint
        
        Pay attention to the different meaning between the columns Executable Authorization and Executable (in profile contained). Only entries with a green check mark in the Executable (in profile contained) column are active for authorization checks.
        
    8. Choose _Back (F3)_ three times.
        
3. Change the Profile Status of Role **ADM945_##_BR_INVENTORY**.
    
    1. Start the Role Maintenance transaction PFCG on the system S4D.
        
    2. In the _Role_ field, enter **ADM945_##_BR_INVENTORY**.
        
    3. Choose _Change_.
        
    4. Go to the _Authorizations_ tab.
        
    5. Choose _Change Authorization Data_.
        
    6.  If an information window opens, choose _Continue (Enter)_.
        
    7. Choose _Organizational levels … (Ctrl+F8)_.
        
    8. Enter **1010** in the_'From'_ filed for organizational level _Plant_.
        
    9. Choose _Save_.
        
    10. Choose _Save_ without generation of the profile.
        
    11. Choose _Back_.
        
    12. In the _Exit Authorization Maintenance_ dialog box choose _Continue_.
        
        The profile status _Current version not generated_ is shown in the _Information About Authorization Profile_ screen area.
        
    13. Choose _Back_.
        
4. Repeat the search for OData Service-based SAP Fiori applications that are startable in roles of the system S4D.
    
    1. Start the User Information System transaction SUIM on the system S4D.
        
    2. Choose _User Information system_ → _Roles_.
        
    3. Start _Search for Startable Applications in Roles_.
        
    4. In the _Selection of Roles_ screen area, in the _Role_ field, enter **ADM945_##***.
        
    5. In the _Selection by Application Type_ screen area, in the _Application Type_ field, choose _SAP Gateway: Service Groups Metadata_.
        
    6. Choose _Execute_ in the bottom right-hand corner.
        
    7. Analyze the result.
        
        For the role **ADM945_##_BR_INVENTORY** the _Profile Status_ column shows: _Current version not generated_.