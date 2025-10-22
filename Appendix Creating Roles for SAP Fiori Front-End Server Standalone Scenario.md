Objective

After completing this lesson, you will be able to manage Authorizations for SAP Fiori Front-End Server Standalone Scenario.

## Front-End Server and Back-End Server Roles in SAP Fiori Front-End Server Standalone Scenario

#### Front-End Server Roles

![Illustration on Front-End Role.](https://learning.sap.com/service/media/topic/e1fa3714-81c1-4b17-a251-6d0f08937715/ADM945_24_en-US_media/ADM945_24_en-US_images/03_05_Roles_FES_Hub_Deploy_000.png "Illustration on Front-End Role.")

If front-end server hub (standalone) deployment is used, PFCG roles providing UI access and start authorizations for activated OData services must be created on the front-end server system.

The PFCG role on the FES needs the catalog for the start authorization and the space for displaying it on the SAP Fiori Launchpad home screen.

Hint

We recommend that you add a catalog to the role menu instead of adding individual OData services. The system determines the OData services for a catalog and automatically includes the start authorizations when adding the catalog to the role menu.

However, this is not always the case and adding single OData service authorizations provides additional security, especially if the FES is set up as a separate hub. By specifying the services explicitly in the role menu, you control which requests on behalf of a user can pass SAP Gateway.

#### Back-End Server Roles

![Illustration on Back-End Role.](https://learning.sap.com/service/media/topic/e1fa3714-81c1-4b17-a251-6d0f08937715/ADM945_24_en-US_media/ADM945_24_en-US_images/03_05_Roles_FES_Hub_Deploy_001.png "Illustration on Back-End Role.")

To view the tile, start the SAP Fiori app, and to get business data from the OData service, a specific OData authorization is necessary.

Therefore the PFCG front-end role with the catalog and space also needs the OData start authorization to call the back-end server.

In addition, a specific PFCG back-end role with the required execute and data access authorizations is needed.

Note

We recommend that you organize the roles on the BES according to the roles on the FES for the sake of consistency of the catalog content.

The authorizations required for a particular application are provided by the OData service of the SAP Fiori apps. This includes the start authorizations for the service or the application in the back-end system and the business authorizations for accessing the business data that is displayed in the app. By adding the catalog to the menu of back-end PFCG roles, the OData services, the start authorization, and the authorization proposals for the business authorizations will be included automatically. You can adjust these as required.

![Illustration on authorizations proposals for Front-End and Back-End Roles.](https://learning.sap.com/service/media/topic/e1fa3714-81c1-4b17-a251-6d0f08937715/ADM945_24_en-US_media/ADM945_24_en-US_images/03_05_Roles_FES_Hub_Deploy_002.png "Illustration on authorizations proposals for Front-End and Back-End Roles.")

Both, the OData start authorization on the FES and the OData access authorization on the BES can include SU24 authorization defaults.

SU24 authorization defaults for IWSG objects only includes start authorizations. The default for IWSV objects mostly include business functional authorization objects which are used within the OData service execution.

![Illustration on authorization proposals for Legacy Apps.](https://learning.sap.com/service/media/topic/e1fa3714-81c1-4b17-a251-6d0f08937715/ADM945_24_en-US_media/ADM945_24_en-US_images/03_05_Roles_FES_Hub_Deploy_003.png "Illustration on authorization proposals for Legacy Apps.")

SAP Fiori legacy apps such as Web Dynpro or SAP GUI for HTML apps need an HTTP / HTTPS connection directly to the back-end server (BES).

However, legacy apps still need to be part of a business catalog, which is going to be assigned to the PFCG role. Also, based on the business catalog, SAP Fiori spaces and pages can be created, which will display the tile of the legacy app.

In the PFCG role, start authorizations and the required execute and data access authorizations must be maintained.

SAP Fiori legacy apps have the SU24 authorization proposals of the called transaction or WebDynpro application only on the BES system.

![Screenshot showing FES and BES Roles.](https://learning.sap.com/service/media/topic/e1fa3714-81c1-4b17-a251-6d0f08937715/ADM945_24_en-US_media/ADM945_24_en-US_images/03_05_FES_and_BES_Roles.png "Screenshot showing FES and BES Roles.")

## Users and Authorizations on Front-End and Back-End Systems

To use SAP Fiori apps in a SAP Fiori Front-End Server hub deployment scenario, users are required on both front-end (FES) and the back-end server (BES) systems.

The users on the BES require the authorizations to use SAP Fiori apps and the authorization to access the business data. These authorizations are required to run SAP Fiori launchpad, to trigger the OData services required for SAP Fiori, and to get business data from the OData service.

On the FES, assign the role containing the catalogs, spaces, and OData start authorizations to a user. Thus, the user gets access to the apps in the catalogs and the start authorizations for the respective OData services on the FES.

The users on the BES require the authorizations to use SAP Fiori apps and the authorization to access the business data. These authorizations are required to run SAP Fiori launchpad, to trigger the OData services required for SAP Fiori, and to get business data from the OData service.

#### General Authorizations Needed on the Front-End System:

- End users: Authorizations to run the SAP Fiori launchpad
- Administrators:
    - Authorizations to run the SAP Fiori launchpad
    - Authorizations to run the SAP Fiori launchpad designer
    - authorizations to run the SAP Fiori launchpad content manager
    - Authorizations to run trouble shooting tools.

SAP delivers roles templates for end users and administrators, that role administrators have to copy to their customer name space, adjust according to the customer's needs, and assign to users.

### General Authorizations Needed on the Front-End System

- SAP-Delivered Role for End users: SAP_FLP_USER
- SAP-Delivered Role for Administrators: SAP_FLP_ADMIN

These authorizations include the authorizations for the UI2 OData services. For these OData services, both the model provider of the activated OData services and the data provider reside on the front-end server.

#### General Authorizations needed on the Back-End System:

The ABAP back-end system implements the business logic and provides the data for the SAP Fiori apps. For apps launched by users from the SAP Fiori launchpad on the front-end server, users with the same user names are required on the ABAP back-end system.

Users in the ABAP back-end system require PFCG roles with certain general authorizations as well as authorizations for specific OData services.

### Assigning RFC Authorization to Users

If the OData back-end service is located on a remote back-end, users need permission to perform the RFC call on the back-end system. Therefore, users in the back-end system need a role including the RFC authorization objects S_RFC and S_RFCACL.

![Tables showing the fields and their values for S_RFC and S_RFCACL authorization objects.](https://learning.sap.com/service/media/topic/f4a0dfc4-e0ec-4ee3-ae80-1263f47cb8c2/ADM945_24_en-US_media/ADM945_24_en-US_images/RFCAuthorizationsfor%20the%20back-enduser.png "Tables showing the fields and their values for S_RFC and S_RFCACL authorization objects.")

For the _S_RFC_ authorization object, you can alternatively assign authorizations for all the function modules in this function group, then using the **FUNC** RFC_TYPE.

To assign authorizations for the trusted RFC connection, in the _S_RFCACL_ authorization object, assign the values to every user using this connection. Thus, the system checks that the users on the front-end server (FES) and on the back-end server (BES) are the same.