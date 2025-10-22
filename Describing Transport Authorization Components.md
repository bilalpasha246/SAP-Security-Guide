## Authorization Components Transport

#### Transport Landscape

![Illustration on transport concepts.](https://learning.sap.com/service/media/topic/b1a11360-0613-4f25-8742-4c717f128700/ADM945_24_en-US_media/ADM945_24_en-US_images/Transport_Concepts_001.png "Illustration on transport concepts.")

The figure shows a typical three-tier transport landscape with three back-end server systems. If you have a standalone front-end server, you have an additional three-tier transport landscape.

While most objects are being transported with traditional transport requests (workbench or customizing), the following figures introduce some objects with dedicated transport attachment or technologies.

![Bullets points listing the authorization components that can be transported.](https://learning.sap.com/service/media/topic/b1a11360-0613-4f25-8742-4c717f128700/ADM945_24_en-US_media/ADM945_24_en-US_images/04_01_TransportingAuthorizationComponents_001.png "Bullets points listing the authorization components that can be transported.")

Options for Transporting Authorization Components:

User data and authorization data must be exchanged in system landscapes with multiple SAP systems. The data is either exchanged between different clients of an SAP system or between clients of different SAP systems.

Authorization profiles can be transported together with their roles. Working with authorization profiles without an assigned role should remain the exception.

### Transport of Catalogs using SAP Fiori Launchpad Content Manager

The SAP Fiori launchpad content manager allows you to make system-wide or client-specific changes.

- Transaction /UI2/FLPCM_CONF allows you to make system-wide changes (configuration scope).
- Transaction /UI2/FLPCM_CUST allows you to make changes for the current client (customizing scope). These changes supersede configuration settings.

![Screenshots showing the transport of catalogs using SAP Fiori Launchpad Content Manager.](https://learning.sap.com/service/media/topic/b1a11360-0613-4f25-8742-4c717f128700/ADM945_24_en-US_media/ADM945_24_en-US_images/TransportCatalogsusingFLPCM.png "Screenshots showing the transport of catalogs using SAP Fiori Launchpad Content Manager.")

When you trigger a change in the client-independent SAP Fiori launchpad content manager (transaction /UI2/FLPCM_CONF), a dialog box is displayed in which you define whether you want to save your changes locally or transport them to other systems. To transport your changes, select a package and a workbench request.

The client-specific SAP Fiori launchpad content manager (transaction /UI2/FLPCM_CUST) takes the settings in transaction SCC4 into account. These settings control whether objects can be changed and whether the changes can be transported. In case changes are recorded (automatic or manually triggered), a customizing request is required.

You can manually trigger the transport of changes when the option Changes without automatic recording is set for the client. This feature also allows you to transport catalogs independent of a change, for example, to make catalogs that were created locally in the launchpad designer available in other clients or systems. To trigger the transport choose a catalog in the _Catalogs_ tab of SAP Fiori Launchpad Content Manager and choose _Transport_ in the toolbar.

### Transporting Catalogs and Groups using SAP Fiori Launchpad Designer

For customizing and configuration of SAP Fiori catalogs and groups, the tool SAP Fiori Launchpad Designer (FLPD) offers an environment for both layers.

- Transaction /UI2/FLPD_CONF starts the FLPD Configuration
- Transaction /UI2/FLPD_CUST starts the FLPD Customizing

To transport catalogs and/or groups, choose _Settings_ in the upper-right corner of the browser window. The system will prompt you for a workbench request (in case of configuration) respective a customizing request (in case of customizing).

![Screenshots showing the transporting catalogs and groups using SAP Fiori Launchpad Designer.](https://learning.sap.com/service/media/topic/b1a11360-0613-4f25-8742-4c717f128700/ADM945_24_en-US_media/ADM945_24_en-US_images/04_01_TransportingAuthorizationComponents_002.png "Screenshots showing the transporting catalogs and groups using SAP Fiori Launchpad Designer.")

Hint

Make sure you have assigned appropriate transport request before you change or add entities in the SAP Fiori Launchpad Designer. If you missed that step you can add changes as it is described in following blog entry at [https://wiki.scn.sap.com/wiki/display/SAPMOB/How+To%3A+Add+existing+catalogs+and+groups+in+CUST+scope+to+transport+requests](https://wiki.scn.sap.com/wiki/display/SAPMOB/How+To%3A+Add+existing+catalogs+and+groups+in+CUST+scope+to+transport+requests)

### Transporting Spaces and Pages

![Screenshots showing the transporting spaces and pages.](https://learning.sap.com/service/media/topic/b1a11360-0613-4f25-8742-4c717f128700/ADM945_24_en-US_media/ADM945_24_en-US_images/04_01_TransportingAuthorizationComponents_003.png "Screenshots showing the transporting spaces and pages.")

When you create a new space in the _Manage Launchpad Spaces_ app or a new page in the _Manage Launchpad Pages_ app, you have to assign a customizing transport request to it.

Note

It is crucial that you are either the owner or you have been entered as the user for the transport request, otherwise you will not see the request in the drop-down list.

You can see the existing transport assignments also in the details view of the _Manage Launchpad Spaces_ and _Manage Launchpad Pages_ apps.

Note that the space or page is not locked after it was assigned to a transport. A space or page can be assigned to several transports. In addition, spaces, pages, and roles that are connected can be assigned to different transports. When you select different transports, it is necessary that all transports are done, so that all three objects are available in the target system. Otherwise the pages and spaces might not be shown correctly.