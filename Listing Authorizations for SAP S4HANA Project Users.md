## Authorizations for SAP S/4HANA Project Users

![Illustration showing the authorizations for SAP Fiori users.](https://learning.sap.com/service/media/topic/a13e07ba-c2bd-4fcf-afb8-adc72c36170d/ADM945_24_en-US_media/ADM945_24_en-US_images/03_01__AuthorizationsForS4HANAProjectUser_001.png "Illustration showing the authorizations for SAP Fiori users.")

There are predefined roles for SAP Fiori end-users.

SAP_FLP_USER

This role includes authorization defaults of end-users of SAP Fiori launchpad.

SAP_FLP_EXP_USER

This role includes authorization defaults to access the /UI2/ file repository.This repository holds the exposed SAP Fiori launchpad content for externalconsumption, e.g. consumption in SAP Could Platform Launchpad.

During the execution of task list SAP Fiori Foundation the role development, these roles can be copied and used as a reference but they are not complete. It is necessary to also provide the IWSG entries for the SAP Fiori Launchpad OData services mentioned in the general Front-End Server role. In the predefined roles there are also some more authorization objects which are necessary for the execution of the SAP Fiori Launchpad.

In a hub deployment scenario the general PFCG role on the Back-End Server only needs the authorization for the Trusted-RFC connection.

In order to also use SAP Fiori applications within the SAP Fiori Launchpad, app specific roles are needed. SAP has also predefined roles for some of the SAP Fiori apps, which are documented in the SAP Fiori Apps Reference Library. Information about which SAP Fiori app belongs to which catalog and space and uses which OData service is also documented in the SAP Fiori Apps Reference Library.

![Illustration showing the authorizations for SAP Fiori admins.](https://learning.sap.com/service/media/topic/a13e07ba-c2bd-4fcf-afb8-adc72c36170d/ADM945_24_en-US_media/ADM945_24_en-US_images/03_01__AuthorizationsForS4HANAProjectUser_002.png "Illustration showing the authorizations for SAP Fiori admins.")

Just like the SAP Fiori user roles, there is also a predefined SAP Fiori administration role available.

SAP_FLP_ADMIN

This role includes authorization defaults of administration tools related to SAP Fiori launchpad. These tools are related to, for example, SAP Gateway, SAP Fiori content management, basis transactions, and so on.

These predefined roles can be copied to the user names during role development. They are created automatically in the user namespace by execution of task list SAP Fiori Foundation (SAP_FIORI_FOUNDATION_S4). The task GENERATE FIORI FOUNDATION ROLES copies the roles SAP_FLP_USER and SAP_FLP_ADMIN to the user namespace with a defined prefix. The copied roles will be enhanced with authorizations/menus for common Fiori functionalities (Fiori Launchpad, Easy Access, Smart Business Runtime Environment, Enterprise Search, Embedded Analytics). Then the copied roles will be used to create composite roles (default: Z_FIORI_FOUNDATION_ADMIN / Z_FIORI_FOUNDATION_USER)

The basic AS ABAP administration authorizations are also necessary for this user, but not mentioned above.

In case an administrator should also test specific SAP Fiori apps, the authorization object S_SERVICE can be maintained with an asterisk (*) for the PFCG role. With this authorization, the administrator can call and execute all OData services.

The transactions described above are just recommendations. It depends on the specific responsibilities the SAP Fiori administrator has within the company.

![Illustration showing the authorizations for SAP Fiori developer.](https://learning.sap.com/service/media/topic/a13e07ba-c2bd-4fcf-afb8-adc72c36170d/ADM945_24_en-US_media/ADM945_24_en-US_images/03_01__AuthorizationsForS4HANAProjectUser_003.png "Illustration showing the authorizations for SAP Fiori developer.")

For developing a SAP Fiori app an OData service at the Back-End server and a SAPUI5 application which is then deployed on the Front-End server need to be developed. It depends on the development setup if this is done by one developer or the tasks are split up between multiple developers.

![Illustration showing the authorizations for SAP Fiori administrator.](https://learning.sap.com/service/media/topic/a13e07ba-c2bd-4fcf-afb8-adc72c36170d/ADM945_24_en-US_media/ADM945_24_en-US_images/03_01__AuthorizationsForS4HANAProjectUser_004.png "Illustration showing the authorizations for SAP Fiori administrator.")

As a role developer you should get a clear understanding for the business need of a request to create or change a role. Adapt that request in role profiles with use of the underlying role authorization concept.

Primary sources how to implement a role change request are:

- SAP Fiori apps reference library
    
    What PFCG menu entries does an app need in front-end and back-end server?
    
- Simplification list
    
- Is the requested application outdated / obsolete?
    
    Note
    
    You can also check if the application is blacklisted by looking into the _ABLM_BLACKLIST_ table.
    

![Illustration showing the authorizations for SAP Fiori support.](https://learning.sap.com/service/media/topic/a13e07ba-c2bd-4fcf-afb8-adc72c36170d/ADM945_24_en-US_media/ADM945_24_en-US_images/03_01__AuthorizationsForS4HANAProjectUser_005.png "Illustration showing the authorizations for SAP Fiori support.")

The steps to solve incidents or defects should be:

- Get a clear description of the situation from the user including detailed steps until the problem stage.
- Check available logs (SLG1, SU53, and so on.
- Check consistency of appropriate data.
- Create an authorization trace (STAUTHTRACE).
- If required, debug the process in test environment.

#### Extended overview of the most important transactions in a support role.

- /UI2/FLP - SAP Fiori Launchpad
    
- /UI2/FLPCM_CUST - Launchpad Content Manager: Client-Specific (Customizing)
    
- /UI2/FLPCM_CONF - Launchpad Content Manager: Cross-Client (Configuration)
    
- /UI2/FLP_SYS_CONF - "FLP-Configuration": Overview
    
- /UI2/FLPD_CUST - Fiori Lpd. Designer (client-spec.)
    
- /UI2/FLPD_CONF - Fiori Lpd. Designer (cross-client)
    
- /UI2/CUST - Customizing of UI Technologies
    
- /UI2/SEMOBJ - Define Semantic Object - Customer
    
- /UI2/PERS_DEL - Cleanup Personalization Service
    
- /UI2/GW_MAINT_SRV - Gateway - Service Maintenance
    
- /UI2/GW_APPS_LOG - Gateway - Application Log
    
- /UI2/GW_ERR_LOG - Gateway - Error Log
    
- /UI2/GW_SYS_ALIAS - Gateway - Manage SAP System Alias
    
- /UI2/FLC - Fiori Launchpad Checks
    
- /UI2/FLIA - Fiori Launchpad Intent Analysis
    
- /UI2/FLT - Fiori Launchpad Texts
    
- /UI2/REFERENCE_LOST - Fiori Launchpad references
    
- /UI5/THEME_TOOL - UI Theme Tool
    
- /UI5/THEME_DESIGNER - UI Theme Designer
    
- /IWFND/ERROR_LOG - SAP Gateway Error Log
    
- /IWFND/TRACES - SAP Gateway Traces
    
- /IWFND/IWF_ACTIVATE - Activate / Deactivate SAP Gateway
    
- /IWFND/GW_CLIENT - SAP Gateway Client
    
- /IWFND/MED_ACTIVATE - Activate/Deactivate Metadata Cache
    
- /IWFND/CACHE_CLEANUP - Cleanup of GW Model Cache
    
- /IWBEP/CACHE_CLEANUP - Cleanup of GW Backend Model Cache
    
- ESH_COCKPIT - Connector Administration Cockpit
    
- ESH_TEST_SEARCH - Test Search
    
- SR13 - Area-Dependent Help
    
- STC01 - Task Manager for Tech. Configuration
    
- SEGW - SAP Gateway Service Builder
    
- SMICM - ICM Monitor
    
- SICF - HTTP Service Hierarchy Maintenance
    
- SM59 - RFC Destinations (Display/Maintain)