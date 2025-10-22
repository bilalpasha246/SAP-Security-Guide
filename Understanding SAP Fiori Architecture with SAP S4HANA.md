
Objective

After completing this lesson, you will be able to understand SAP Fiori Architecture in SAP S/4HANA.

## SAP Fiori Architecture in SAP S/4HANA

![Illustration on SAP Fiori Architecture.](https://learning.sap.com/service/media/topic/e1186fe1-3d0b-4d57-b003-993731b3dbfe/ADM945_24_en-US_media/ADM945_24_en-US_images/01_02_UnderstandingSAPFioriArchitectureWithS4HANA_001.png "Illustration on SAP Fiori Architecture.")

The SAP Front-End Server is an ABAP Stack like any SAP ERP or SAP S/4HANA Back-End Server. However, no business add-ons are installed out of the box.

The recommended SAP Fiori system landscape splits up the UI part from the business logic on SAP Back-End Server.

- Lifecycle decoupling of UI apps from back-end.
- Especially for apps that must also run on any DB.
- Allow faster iterations for the UI apps.
- Allow changes to UI without the need for development privileges in the back-end.
- Add-on-based delivery enables fast release cycles.
- Single point of UI maintenance like browser support or UI5 provisioning.
- Central place for themes and brands.
- Single place for configuration, personalization and SAP Fiori shell services.
- Rule-based dispatching of requests in a multi-system landscape (for example for approvals including aggregation).
- Security considerations.
- Similar to an application-level gateway (ALG) with protocol switch and white-listing (excluding search).
- Admin for UI metadata does not need to have admin rights in the back end (data sensitivity).

Note that this picture does not describe the whole SAP Fiori architecture. It just shows the relevant components from an authorization point of view

![Diagram showing the big picture of SAP Fiori Architecture.](https://learning.sap.com/service/media/topic/e1186fe1-3d0b-4d57-b003-993731b3dbfe/ADM945_24_en-US_media/ADM945_24_en-US_images/01_02_UnderstandingSAPFioriArchitectureWithS4HANA_003.png "Diagram showing the big picture of SAP Fiori Architecture.")

This is the big picture of the SAP Fiori system landscape (simplified with important components for authorization)

![Diagram on SAP Fiori Search.](https://learning.sap.com/service/media/topic/e1186fe1-3d0b-4d57-b003-993731b3dbfe/ADM945_24_en-US_media/ADM945_24_en-US_images/01_02_UnderstandingSAPFioriArchitectureWithS4HANA_007.png "Diagram on SAP Fiori Search.")

SAP Fiori Launchpad Search works differently. The search user interface is called via HTTP / HTTPS from the central UI component on the Front-End Server, as it is part of the SAP Fiori Launchpad. But the data comes through thecl directly from the enterprise search engine on the SAP S/4HANA Back-End Server. (InA protocol is an internal protocol used by SAP products to retrieve data from (embedded)SAP BW systems or SAP HANA databases)

![Diagram on Legacy Apps.](https://learning.sap.com/service/media/topic/e1186fe1-3d0b-4d57-b003-993731b3dbfe/ADM945_24_en-US_media/ADM945_24_en-US_images/01_02_UnderstandingSAPFioriArchitectureWithS4HANA_008.png "Diagram on Legacy Apps.")

SAP legacy apps such as Web Dynpro or GUI for HTML apps need a HTTP or HTTPS connection that connects directly to the Back-End Server.

The pre-delivered Tiles, Spaces and Pages, Groups and Catalogs are shipped with the product UI and accessed via HTTP / HTTPS as well, or it is shipped via remote catalogs, spaces and pages, and groups on the SAP S/4HANA Back-End Server.

## Front-End Server Deployment Options Overview

When talking about SAP Fiori deployment options, we differentiate mainly between the deployment location of SAP Fiori UI components and the back-end components.

All the mentioned deployment options consume business data from an on-premise SAP back-end system. The SAP Fiori launchpad, the SAP-delivered or custom-built SAP Fiori UIs and the launchpad content can be deployed on the same server (embedded deployment), or on a separate server (hub deployment). SAP Cloud Platform offers various tools for developing of custom SAP Fiori / SAPUI5 applications and extensions.

The following graph shows the main SAP Fiori deployment options with an on-premise SAP back-end:

- SAP Fiori front-end server (FES) embedded deployment
    
    The tasks of the FES for providing SAP Fiori are embedded in the BES. There is only one system.
    
- SAP Fiori FES as a standalone server/hub deployment
    
    The FES and the BES are two separated systems splitting the tasks in providing SAP Fiori.
    

![Diagram on SAP Fiori Deployment Options.](https://learning.sap.com/service/media/topic/ea1c7fcb-32da-4a07-ac3e-d1fc7a9ff284/ADM945_24_en-US_media/ADM945_24_en-US_images/SAP_Fiori_Deployment_Options.png "Diagram on SAP Fiori Deployment Options.")

The recommendation for the SAP Fiori front-end server (FES) deployment is the following:

- For **SAP S/4HANA**, the **embedded SAP FES** deployment is recommended.
- For SAP Business Suite scenarios, SAP FES as a central hub is still the recommended deployment.

Hint

Furthermore, SAP is strategically evolving the SAP Business Technology Platform (SAP BTP) as an integration and extension platform and enhancing the capabilities to establish a central point of access. Organizations can implement an SAP Fiori launchpad in the cloud using the dedicated SAP Launchpad service, which acts as common UX integrator for SAP and non-SAP solutions (both on-premise and in the cloud). SAP Launchpad service enables customers building a common user experience on top of multiple SAP S/4HANA systems.

Note

This lesson gives a short overview of SAP Fiori deployment options.

A detailed description can be found in the SAP Fiori Deployment Options and System Landscape Recommendations document.

This document discusses the different SAP Fiori deployment options for SAP S/4HANA and SAP Business Suite systems and the recommended system landscape setup.

You will find a reference to this document in the SAP Note 2775163 - SAP Fiori Front-End Server 6.0 – General Information.

### Deployment Options - Pros and Cons

#### Pros and Cons - Embedded Deployment

- Pros
    - Administration is easier (only one common system)
        
    - No additional front-end system required, lower TCO
        
    - Easy initial activation of SAP Fiori Apps with the help of task lists
        
    - Optimized performance through direct access to back-end services (no RFC)
        
    - Roles and authorizations centrally in one system
        
- Cons
    - Central SAP Fiori Launchpad not possible
        
    - No integration of several back-end systems (for example, MyInbox)
        
    - Load on the system is higher (back-end and front-end processes)
        
    - Security: Front-end is physically connected to the back-end (especially relevant for internet scenarios)
        

#### Pros and Cons - Hub Deployment

- Pros
    - Central SAP Fiori Launchpad possible
        
    - Integration of several back-end systems (for example, MyInbox)
        
    - Load on the back-end system is not increased
        
    - Security: Front-end is physically decoupled from the back-end (especially relevant for Internet scenarios)
        
- Cons
    - Administration more complex (back-end and front-end system)
        
    - Additional front-end system required, higher TCO
        
    - Performance loss when accessing back-end services (RFC)
        
    - Roles and authorizations must be maintained in several systems
        

For more details, please refer to the FES Embedded OR Hub deployment – Pros and Cons section of the SAP Fiori Deployment Options and System Landscape Recommendations document.

Note

Further information can also be found in the following blogs:

- SAP Fiori Deployment Options – Updates with SAP FES 6.0.
    
    [https://blogs.sap.com/2019/10/25/sap-fiori-deployment-options-updates-with-sap-fes-6.0/](https://blogs.sap.com/2019/10/25/sap-fiori-deployment-options-updates-with-sap-fes-6.0/)
- SAP Fiori for SAP S/4HANA – Transition from Standalone to Embedded Deployment in SAP S/4HAN