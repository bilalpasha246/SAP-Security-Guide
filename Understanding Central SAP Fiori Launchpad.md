## Central Entry Point on SAP Business Technology Platform

SAP offers advanced UX integration capabilities on SAP Business Technology Platform (SAP BTP) to help organizations to establish a central entry point for applications and to provide users with an easy access to SAP, custom-built and third-party applications, services, and tasks – either from on-premise or cloud. Users also benefit from a harmonized user experience based on SAP Fiori design.

![Illustration showing SAP Business Technology Platform as the central entry point for applications.](https://learning.sap.com/service/media/topic/b92f39fe-ba2a-4926-b835-296efe07ca13/ADM945_24_en-US_media/ADM945_24_en-US_images/CentralEntryPointonSAPCloudPlatform.png "Illustration showing SAP Business Technology Platform as the central entry point for applications.")

SAP Business Technology Platform is being enhanced with capabilities to implement a common SAP Fiori launchpad experience in the cloud, based on SAP Launchpad service and related UX services for branding, notifications, tasks, enterprise search, Web Assistant, and secure single sign-on.

From operations perspective, connected solutions and systems remain self-contained entities regarding their software lifecycle management, authorizations and business content structure. While each system still has its local home page or launchpad as entry point, business users can preferably and conveniently access all their relevant apps through the central cloud-based SAP Fiori launchpad. The central SAP Fiori launchpad on SAP Business Technology Platform will also be able to integrate multiple SAP S/4HANA systems of different versions.

SAP Launchpad service on SAP Business Technology Platform can be used to implement a central entry point scenario to access business applications and services from different SAP systems in a single seamless experience. It provides a central point of access to SAP, but also custom-built, and third-party applications, and it offers an intuitive and harmonized user experience across a heterogeneous landscape based on SAP Fiori design. The access to apps and services is simplified and can be done from multiple devices, such as desktop or mobile devices. End users have access to a personalized home page with role-based content.

The enhanced integration capabilities of the SAP Launchpad service are typically desired from an end user perspective, for example, users need a seamless cross-products app-to-app navigation, one central inbox and notification channel, a central search, and digital assistance.

SAP is further evolving the capabilities of the SAP Launchpad service to integrate with other core services of SAP BTP.

Beside the central entry point scenario, there are also other use cases for the SAP Launchpad service:

#### Extensions

Provide an easy and mobile access to custom applications and extensions build on SAP BTP.

#### External-facing scenarios

Grant employees or business partners secure access to selected applications and services over the Internet on desktop and mobile devices outside the corporate network.

#### Cloud transition

Elevate the SAP Fiori experience to the cloud, especially for customers running an application-centric SAP Enterprise Portal.

### SAP Launchpad Service Content Model

![Screenshot on Launchpad Service Content.](https://learning.sap.com/service/media/topic/b92f39fe-ba2a-4926-b835-296efe07ca13/ADM945_24_en-US_media/ADM945_24_en-US_images/Launchpad_Service_Content.png "Screenshot on Launchpad Service Content.")

The SAP Launchpad Service is a service provided on SAP BTP. The SAP BTP administrator has to subscribe the service first. After this is done, the SAP Launchpad Service administration UI can be opened.

The SAP Launchpad service provides administration capabilities for integrating business applications and managing of related content such as apps, catalogs, spaces, and roles. The administrator of the SAP Launchpad service uses the Content Manager to build content structure and manage configuration for each application.

In the SAP Launchpad service administration UI, there is also a Provider Manager, where content providers can be configured.

### SAP Launchpad Service – Content Integration

![Illustration on Content Integration Remote Content Provider.](https://learning.sap.com/service/media/topic/b92f39fe-ba2a-4926-b835-296efe07ca13/ADM945_24_en-US_media/ADM945_24_en-US_images/07_02_Content_Exposure_001.png "Illustration on Content Integration Remote Content Provider.")

In hybrid landscape scenarios, administrators can integrate content into SAP BTP from content providers (remote or SAP BTP providers). For selected cloud and on-premise providers, such as SAP S/4HANA Cloud, SAP IBP, Cloud Foundry HTML5 Apps on SAP BTP or S/4HANA On-Premise, SAP Business Suite, SAP Enterprise Portal, the SAP Launchpad service offers content federation for an advanced integration of business content.

A content provider exposes content from a source to make it accessible from SAP Launchpad service .

If you have an on-premise SAP S/4HANA system as remote content provider, you do not want to manually replicate the content in the SAP Launchpad service. Instead, you want to synchronize, meaning expose the content to SAP BTP.

This makes the day-to-day operation and maintenance of the content administrator much more efficient:

1. The content administrator of the provider (for example SAP S/4HANA) manages application configuration and content structure using the native tools.
2. The content administrator of the provider exposes configuration and content structure based on the common data model (CDM) format.
    
    Note
    
    Content from remote content providers is exposed at the role level. All content items related to these roles, including apps, spaces, and catalogs, are also integrated and are all visible in the runtime. In the SAP Launchpad Service - Content Manager, however, it is possible to see only the roles and the list of apps assigned to each role. These roles can only be used as a whole. It is not possible to edit their content.
    
3. The SAP Launchpad service administrator assigns roles to launchpad sites and users. Thus, users get authorizations for the relevant content from the provider.

For more information about content integration, please refer to the official SAP Launchpad Service documentation on the SAP Help Portal: [https://help.sap.com/docs/Launchpad_Service/8c8e1958338140699bd4811b37b82ece/9db48fa44f7e4c62a01bc74c82e74e07.html](https://help.sap.com/docs/Launchpad_Service/8c8e1958338140699bd4811b37b82ece/9db48fa44f7e4c62a01bc74c82e74e07.html).

## Launchpad Roles

### SAP Launchpad Service - Options for Creation of Roles

- Manual creation of Launchpad Roles
- Synchronization of SAP S/4HANA Roles

The manual creation of launchpad roles is applicable for apps available in SAP S/4HANA as well as for native cloud developments.

However, roles in the on-premise SAP S/4HANA system that include SAP Fiori Apps can be also synchronized.

Central Launchpad is replicating catalogs and spaces of this role from the on-premise launchpad role to the corresponding central launchpad role. However, the replicated and exposed content cannot be changed. Just the role as a whole can be used.

Note

Exposed and manually created content can (currently) not be mixed up.

![Illustration showing the launchpad roles for SAP Launchpad Service.](https://learning.sap.com/service/media/topic/a0005707-afb4-4b54-b986-fe2397f98e69/ADM945_24_en-US_media/ADM945_24_en-US_images/Launchpad_Roles.png "Illustration showing the launchpad roles for SAP Launchpad Service.")

In the SAP Launchpad service, there are also roles to define which user sees which catalogs and spaces. The authorization model works, however, differently than the classic ABAP authorizations. Also how the roles are assigned to users is also different.

The app is the central element in the content model in SAP Launchpad service. It combines tile and target mapping for accessing an application.

Apps can be mapped to catalogs, spaces, but also directly roles. However, catalogs and groups are not added to roles. Only apps are added to roles.

- Mapping to a catalog enables the app to be available in the app finder of a launchpad site.
- Mapping to a space enables the app to be available on the home page of a launchpad site.
- Mapping to a role enables the app and all mapped catalogs and spaces to be assigned to a launchpad site by mapping the role to the site.

Note

If a user is authorized via a role for an app that is assigned to several catalogs, he or she will find all the catalogs in the central launchpad. However, the user will not be able to see other apps in the catalogs if he or she is not authorized for them.

Launchpad roles cannot be assigned to users directly. Defining a role in SAP Launchpad Service generates a role collection with the same name in the SAP BTP cockpit. This role collection can then be assigned to users allowing the users access to the site and all mapped apps, catalogs, and spaces.

![Screenshots on Role Collection SAP BTP.](https://learning.sap.com/service/media/topic/a0005707-afb4-4b54-b986-fe2397f98e69/ADM945_24_en-US_media/ADM945_24_en-US_images/Role_Collection_SAP_BTP.png "Screenshots on Role Collection SAP BTP.")