
Objective

After completing this lesson, you will be able to recall the environment and the infrastructure of SAP Identity Services and SAP BTP.

## Identity Provisioning

**Disclaimer:** The SAP Business Technology Platform (SAP BTP) is evolving permanently and frequently. Therefore, there might be some differences between the screenshots and simulations in this course and the actual environment. Some changes are due to the strategy of SAP, which is to harmonize the user experience across platforms while others bring new features.

The Identity Provisioning service automates identity lifecycle processes. It helps you to provision identities and their authorizations to various cloud and on-premise business applications.

### Environment

Identity Provisioning tenants run on the infrastructure SAP Business Technology Platform (SAP BTP).

### Features

- **User and Group Provisioning:**
    
    Provision users and groups between multiple supported cloud and on-premise systems (for both SAP and non-SAP).
    
- **User and Group Filtering:**
    
    Configure default transformations or filtering properties to control what data is going to be provisioned and what is going to be skipped.
    
- **Full and Delta Read Mode:**
    
    Run a provisioning job in full mode to read all entities from a source system, or in delta read mode - to read only the modified data.
    
- **Job Logging:**
    
    View and export job logs from the Identity Provisioning administration console; log display details about the job status and the provisioned entities.
    
- **Notifications:**
    
    Subscribe to a source system to receive notifications for the status of provisioning jobs.
    

![The diagram shows identity provisioning: The User Store is the source system to read entities, which are then transferred via Identity Provisioning Service to the SaaS Business Application. This application is the target system for populating entities.](https://learning.sap.com/service/media/topic/c41344da-1b66-429d-8373-204b909be6d6/SECCL1_24_en-US_media/SECCL1_24_en-US_images/OverviewGraphic_scr.png "The diagram shows identity provisioning: The User Store is the source system to read entities, which are then transferred via Identity Provisioning Service to the SaaS Business Application. This application is the target system for populating entities.")

## How to Navigate the Identity Provisioning Service

The administration console for Cloud Identity Services aggregates the functionality for Authentication services and Provisioning services. At this stage, we will focus on the main options available for the Provisioning service.

In this demonstration, you will learn where to locate the main functions on Identity Provisioning. From the available menu options, you will see where to create or configure a source, target, or intermediate (proxy) system. You will access the logs that report the success or failure of your provisioning operations, and finally access an administrative set of links that allow you to explore documentation, request support, or reset the existing tenant content, something that might be useful in the case of development/tenant/trial environments.

Note

To view this demonstration, and others in this course, the Chrome browser is recommended.

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_2C85A3D942236BB1:demo)

## How to Explore User Manual Definition

This demonstration shows how to manually create or review a user in the Identity Provisioning tenant. The user and authorizations options allows you to create or manage users, and can be useful to see if the user attributes are being populated correctly. Depending on the characteristics of source and target systems, not all details will be relevant for all possible systems. An e-mail might be relevant in most common scenarios, but a company relationship will not be needed so often. This functionality is common across Identity Authentication and Identity Provisioning.

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_E029721C04D83C81:demo)

## How to Explore Group Manual Definition

This demonstration shows how to manage groups in the Identity Provisioning Services tenant. Groups can appear as a result of a provisioning job execution, but can also be manually defined or imported by simple upload processes. Like for the user entity, a group and its management functions are a common point between Identity Authentication and Identity Provisioning services.

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_AB76949751B7A9B3:demo)

## How to Explore Mass Import/Export

This demonstration shows the available functions to manually import and export users into the Identity Services tenant. The export/import process or, if you prefer, the upload/download process uses CSV files. For the import step, carefully review if the file content matches the required attributes for the involved entities. As an example, in different systems, a first name, last name, or full name might be required or not.

Demo