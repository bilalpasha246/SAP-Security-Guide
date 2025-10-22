# Explaining SAP BTP Accounts

Objective

After completing this lesson, you will be able to explore Global Accounts.

## SAP Business Technology Platform

**Disclaimer:** The SAP Business Technology Platform (SAP BTP) is evolving permanently and frequently. Therefore, there might be some differences between the screenshots and simulations in this course and the actual environment.

### What is SAP Business Technology Platform?

Your organization aims to develop custom code and modify SAP solutions. However, unlike on-premise systems, such modifications are not possible in the cloud, so you need alternative ways to meet your specific requirements. You also want to integrate SAP Software-as-a-Service (SaaS) solutions, such as SAP Concur, SAP SuccessFactors, and others, with SAP S/4HANA Cloud to create a fully connected ecosystem of applications and business processes. Additionally, you plan to integrate various third-party applications.

Given that your organization generates and collects vast amounts of data, effective data management and analysis are essential to derive meaningful insights. The SAP Business Technology Platform (BTP) serves this need by providing an open platform-as-a-service (PaaS) environment with in-memory processing, core platform services, and specialized microservices. It enables you to build and extend intelligent, mobile-ready cloud applications quickly, easily, and cost-effectively, without the need for on-premise infrastructure.

The SAP BTP is the technological base of the intelligent, sustainable enterprise. Based on open standards, SAP BTP offers complete flexibility and control over your choice of clouds, frameworks, and applications. It is used for three main scenarios in the scope of an intelligent and sustainable enterprise:

- **Integration**
    
    Modern enterprises operate within complex IT landscapes that combine on-premise systems and cloud platforms along with SaaS applications and hyperscaler technologies from SAP and third-party providers.
    
    Integration plays a critical role in connecting these diverse systems and business processes across the entire value chain. Seamless integration enhances operational efficiency, data consistency, and business agility—making it a cornerstone of an effective IT landscape in the digital era.
    
- **Data to Value**
    
    It is essential for organizations to maintain a consolidated view of their data assets to generate insights and enable real-time decision-making, especially in periods of rapid change. As data continues to grow exponentially and becomes the currency of the future, ensuring high data quality and adopting robust data management technologies are critical. To truly unlock the value of data, organizations must go beyond collection—analyzing, interpreting, and applying insights to drive agility, scalability, and sustainable growth.
    
- **Extensibility**
    
    To remain competitive, organizations must stay agile and adapt quickly to evolving business conditions and customer expectations. Extensibility empowers organizations to enhance and expand their existing application investments, ensuring they continue to meet dynamic business needs and deliver ongoing value.
    
    With SAP BTP as the foundation, enterprises can develop and deliver new features rapidly and efficiently, supporting continuous innovation. You can leverage services such as feature flags, continuous delivery, and cloud transport management to enable agile and controlled innovation. With the flexibility to choose your preferred runtime environment, SAP BTP allows you to extend applications efficiently and securely. As the number of cloud solutions in IT landscapes continues to grow, organizations must embrace extensibility rather than traditional system modifications—marking a fundamental shift from the on-premise approach to modern cloud development.
    

Learn more about SAP BTP here: [https://www.sap.com/products/business-technology-platform.html](https://www.sap.com/products/business-technology-platform.html).

### Architecture of SAP Business Technology Platform

The figure shows a global account divided into regions.

![The diagram shows a global account divided into regions X, Y, Z, each with subaccounts A, B, C. Each subaccount has applications, services, and subscriptions.](https://learning.sap.com/service/media/topic/bda5cf06-7d23-4993-99b8-15098dbe54c2/SECCL1_24_en-US_media/SECCL1_24_en-US_images/SAP_BTP_Arch_scr.png "The diagram shows a global account divided into regions X, Y, Z, each with subaccounts A, B, C. Each subaccount has applications, services, and subscriptions.")

SAP BTP offers global accounts and subaccounts.

- **Global Accounts**
    
    A global account is the realization of a contract that you made with SAP. It is used to manage subaccounts, members, entitlements, and quotas. You receive entitlements and quotas to use platform resources as per the global account which can then be distributed to the subaccounts for actual consumption.
    
- **Subaccounts**
    
    Subaccounts allow you to structure a global account based on your organization’s and project’s specific needs for members, authorizations, and entitlements. A global account can contain one or more subaccounts, where you can deploy applications, consume services, and manage subscriptions. Each subaccount within a global account operates independently, which is an important consideration for security, member management, data management, data migration, and integration when planning your overall landscape and architecture.
    

### Regions and Environments

![The diagram shows a sample region with subsections: applications, services, data, environments, and infrastructure. Beside it, a sample environment has run time, tools, and services that connect to applications.](https://learning.sap.com/service/media/topic/bda5cf06-7d23-4993-99b8-15098dbe54c2/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Regions_and_Envir_scr.png "The diagram shows a sample region with subsections: applications, services, data, environments, and infrastructure. Beside it, a sample environment has run time, tools, and services that connect to applications.")

You can deploy applications in different regions. Each region represents a geographical location (for example, Europe, U.S. East) where applications, data, or services are hosted.

- **Infrastructure**
    
    The infrastructure layer of a region is either provided by SAP or by one of its Infrastructure-as-a-Service (IaaS) partners, such as Amazon Web Services (AWS) or Microsoft Azure.
    
- **Environments**
    
    Environments represent the Platform-as-a-Service (PaaS) layer of SAP BTP, enabling the development, deployment, and administration of business applications. Each environment provides the necessary tools, technologies, and runtime required to build applications efficiently. The availability of multiple environments offers flexibility and choice, allowing organizations to tailor their development processes based on their specific technical and business needs.
    
- **Services**
    
    Services enable, facilitate, or accelerate the development of business applications and other platform services on SAP BTP.
    
- **Data**
    
    Your business and application data are managed through services like the SAP Data Warehouse Cloud service.
    
- **Applications**
    
    These are the business applications that you deploy in a region, building on top of and using the layers underneath.
    

## Global Accounts and Subaccounts

### Overview - SAP BTP Offering

SAP BTP offers users the ability to turn data into business value, compose end-to-end business processes, and build and extend SAP applications quickly.

The services and solutions of SAP BTP are available on multiple cloud infrastructure providers. The multi-cloud foundation supports different environments, such as Cloud Foundry, ABAP, and Kyma, as well as multiple different regions, and a broad choice of programming languages.

The central point of entry to the cloud platform is the SAP BTP cockpit, where you can access your accounts and applications and manage all activities associated with them.

The hierarchical element, '**directory** is essentially a grouping of subaccounts. Furthermore, subaccounts can have multiple environments.

The figure depicts the relationship between a global account, its directories, subaccounts, environments, regions, entitlements, and quotas.

![The diagram shows different workflows: The global account links to entitlements, billing info, directory, regions, admins, and license type. The directory connects to entitlements, admins, .... The subaccount links to quotas, environment, admins, region, and business user IdP.](https://learning.sap.com/service/media/topic/c02dc827-fcb6-4620-84a5-c95c39ae08fd/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Ac_Dir_and_Subac_FeatureB_scr.png "The diagram shows different workflows: The global account links to entitlements, billing info, directory, regions, admins, and license type. The directory connects to entitlements, admins, .... The subaccount links to quotas, environment, admins, region, and business user IdP.")

## Users and Authentication

### User and Authorization Management on SAP BTP

As IT landscapes become more and more complex, the topic of security becomes more important. Your company must manage application users (business users) and platform users (admins, operators, and so on). You want to assign roles and authorizations and build a central identity provisioning with the SAP Cloud Identity Services. All APIs and interfaces that are used or integrated must be secured as well.

The figure shows the SAP BTP users.

![There are platform users, such as administrators and operators, as well as business users, such as application users.](https://learning.sap.com/service/media/topic/c440250b-3b5b-4aa3-8cb0-f4337e878518/SECCL1_24_en-US_media/SECCL1_24_en-US_images/SAP_BTP_Users_scr.png "There are platform users, such as administrators and operators, as well as business users, such as application users.")

SAP BTP distinguishes between the following:

- Platform users are usually administrators or operators who work with cloud management tools and deploy, administer, and troubleshoot services on SAP BTP. These are usually users who directly log on to SAP BTP cockpit and work there.
- Business users use the business applications that are deployed on SAP BTP. For example, the end users of a deployed custom application or users of subscribed apps or services, such as SAP Business Application Studio, are business users.

The figure shows the SAP accounts and memberships.

![There are different types of membership for each of the different accounts, that is, the global account, directory, subaccount, org, and space account. Each level has a corresponding role: global account administrator, directory member, subaccount administrator, org member, and space member.](https://learning.sap.com/service/media/topic/c440250b-3b5b-4aa3-8cb0-f4337e878518/SECCL1_24_en-US_media/SECCL1_24_en-US_images/SAP_Accounts_Memb_scr.png "There are different types of membership for each of the different accounts, that is, the global account, directory, subaccount, org, and space account. Each level has a corresponding role: global account administrator, directory member, subaccount administrator, org member, and space member.")

The SAP BTP is organized in global accounts on the highest level. These are hosted by multiple cloud infrastructure providers in different regions. A global account reflects a contract with SAP. It can consist of several directories and/or several subaccounts that provide different applications and services to users. Furthermore, subaccounts can have multiple environments. Environments constitute the actual platform-as-a-service offering of SAP BTP that allows the development and administration of business applications. These environments are called spaces.

In Cloud Foundry, further levels are in place for a better structuring and organization of work. For example, if you have too many subaccounts in a global account, you can create directories to structure them. And if you enable the Cloud Foundry environment, you automatically create a Cloud Foundry org., in which you create one or more spaces.

Anyone who wants to use SAP BTP must be assigned as a user to it. User management happens at all levels, from global accounts to spaces. On each level, you require an administrator, who administers resources and the users on those levels.

The figure shows the SAP BTP subaccounts.

![A sample global account includes three subaccounts, A, B, and C. Subaccount A includes SAP BAS, mobile services, and a business application.There are three users: a global account administrator, a subaccount administrator, and a business user.](https://learning.sap.com/service/media/topic/c440250b-3b5b-4aa3-8cb0-f4337e878518/SECCL1_24_en-US_media/SECCL1_24_en-US_images/SAP_BTP_Subaccounts_scr.png "A sample global account includes three subaccounts, A, B, and C. Subaccount A includes SAP BAS, mobile services, and a business application.There are three users: a global account administrator, a subaccount administrator, and a business user.")

When a customer signs a contract with SAP, one user is created at the global account level. On this level, entitlements are defined, assigning entities and services, including billing information. The global account administrator can initially log on to SAP BTP to manage these entitlements and create directories and subaccounts. To ensure that more than one employee can administer the global account, the administrator must create other users at the global account level and assign them administrator permissions.

Typically, a global account consists of various subaccounts. When a global account administrator creates a subaccount, they automatically become the administrator of the subaccount. The subaccount administrator can manage entitlements, service subscription, create other users on the subaccount level, and assign roles to the users. Subaccount administrators get administration authorizations for the subaccount only, not for the global account.

Subaccount administrators also create business users, who are consumers of applications and services that are provided on SAP BTP. For example, SAP Business Application Studio, or business applications (SaaS) that were created with the help of the tools and services provided by SAP BTP and deployed in a subaccount. These users can have access to SAP BTP, but they are not able to do any administrative tasks. If a business user only uses a single application on SAP BTP, they do not necessarily require access to the SAP BTP cockpit (meaning the subaccount) but to the application only. In this case, the subaccount administrator creates the user on a subaccount level and only assigns application authorizations to the user.

### Users, Roles, and Role Collections

To use different functions of SAP BTP, you must be authorized for it. In the Cloud Foundry environment, you can configure authorizations using roles and role collections.

Role collections consist of individual roles that combine authorizations for resources and services on SAP BTP. A role collection can comprise one or multiple roles. You only assign role collections to users, but not individual roles. Roles and their authorizations are provided automatically to users using role collection assignment.

Role collections are managed on each SAP BTP level separately. Role collections that exist in the global account do not exist in the subaccounts. Likewise, role collections in subaccounts are not available in the global account.

SAP BTP already delivers a predefined set of role collections for platform users and for application users. To set up administrator access for platform users in the global account, directories, subaccounts, and so on, an existing administrator of a certain level on SAP BTP assigns predefined role collections to other platform users.

For users of applications that can be subscribed on SAP BTP, there are also predefined role collections that become available after application subscription. It is also possible to create custom role collections with roles inside that give permissions for custom applications deployed on SAP BTP.

The figure shows a role collection workflow.

![The shows a role collection workflow. A role collection is assigned to a user (via static or federated assignment) or a role (via static assignment). Roles include the administrator and the developer.](https://learning.sap.com/service/media/topic/c440250b-3b5b-4aa3-8cb0-f4337e878518/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Role_Collections_scr.png "The shows a role collection workflow. A role collection is assigned to a user (via static or federated assignment) or a role (via static assignment). Roles include the administrator and the developer.")

### SAP Solutions for Identity Management and Governance

The figure shows the SAP solutions for identity management and governance.

![The image is a diagram titled Cloud Identity Services with three sections: Identity Authentication Service, Identity Provisioning Service, and Identity Access Governance Service.](https://learning.sap.com/service/media/topic/c440250b-3b5b-4aa3-8cb0-f4337e878518/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Security_SAP_Cloud_scr.png "The image is a diagram titled Cloud Identity Services with three sections: Identity Authentication Service, Identity Provisioning Service, and Identity Access Governance Service.")

The SAP Identity Management and Access Governance solutions portfolio spreads along multiple cloud and on-premise applications:

- **SAP Single Sign-On** provides simple, secure access to IT applications for business users. It offers advanced security capabilities to protect your company data and business applications.
- **SAP Cloud Identity Authentication Service** provides simple and secure access to Web-based applications with a variety of authentication methods at anytime and from anywhere. The service was previously known as SAP Cloud Identity service.
- **SAP Identity Management** keeps the user's data secure and consistent and supports customers by implementing integrated identity lifecycle scenarios with SAP's cloud or on-premise HR solutions: SAP SuccessFactors solutions (cloud) and SAP ERP Human Capital Management (on-premise). Be aware of the EOL timeline for this product.
- **SAP Cloud Identity Provisioning** offers a comprehensive, low-cost approach to identity lifecycle management in the cloud. Identity Provisioning covers a broad range of source and target systems, both in the cloud and on-premise.
- **SAP Cloud Identity Access Governance** is a cloud solution that integrates out-of-the-box with SAP S/4HANA, and it can run similar SOD scenarios as SAP GRC Access Control. Additionally, it has functionalities to build business roles in the cloud, provision those to various target systems through SAP Cloud Identity Services, Identity Provisioning, and integrate in complex workflows thanks to SAP BTP Workflow service.
- **The SAP GRC Access Control** application helps streamline the process of managing and validating user access to applications. SAP Identity Management and SAP Access Control function as an integrated solution for identity and access governance.

### SAP Cloud Identity Services

The figure shows the SAP Cloud Identity Services.

![The diagram shows the process where the end user uses SAP cloud identity services to access SAP cloud business applications.](https://learning.sap.com/service/media/topic/c440250b-3b5b-4aa3-8cb0-f4337e878518/SECCL1_24_en-US_media/SECCL1_24_en-US_images/SAP_Cloud_Id_Ser_scr.png "The diagram shows the process where the end user uses SAP cloud identity services to access SAP cloud business applications.")

The Identity Authentication service is mainly responsible for the Authentication and Single Sign-On, while the Identity Provisioning service takes care of the Identity Lifecycle Management, which includes both users and groups.

The figure shows the SAP identity provisioning.

![With identity provisioning, you can perform various tasks for cloud-based and on-premise systems.](https://learning.sap.com/service/media/topic/c440250b-3b5b-4aa3-8cb0-f4337e878518/SECCL1_24_en-US_media/SECCL1_24_en-US_images/SAP_Id_Prov_scr.png "With identity provisioning, you can perform various tasks for cloud-based and on-premise systems.")

The Identity Provisioning service allows you to do the following:

- Manage user accounts and authorizations across cloud and on-premise systems
- Provision identities from user stores in the cloud and on-premise
- Enable business applications to quickly support single sign-on with identity authentication

As a key value proposition, the Identity Provisioning service provides:

- Fast and efficient administration of user on-boarding
- Centralized end-to-end lifecycle management of corporate identities in the cloud
- Automated provisioning of existing on-premise identities to cloud applications

### Open Security Standards – Interoperable

The figure shows the open security standards like SAML and OIDC.

![The diagram illustrates how users authenticate through identity providers using open security standards like SAML or OIDC to access cloud applications, including SAP. It shows two flows: direct identity authentication and using a corporate identity provider.](https://learning.sap.com/service/media/topic/c440250b-3b5b-4aa3-8cb0-f4337e878518/SECCL1_24_en-US_media/SECCL1_24_en-US_images/SAML_OpenID_scr.png "The diagram illustrates how users authenticate through identity providers using open security standards like SAML or OIDC to access cloud applications, including SAP. It shows two flows: direct identity authentication and using a corporate identity provider.")

Identity Authentication provides simple and secure access to Web-based applications with various authentication methods at any time and from anywhere.

Identity Authentication provides secure and simple access based on the following factors:

- Identity federation based on SAML 2.0
- Web Single Sign-On SSO and desktop SSO
- Secure on-premise integration to reuse existing authentication systems
- Social login and two-factor authentication
- Risk-based authentication

Identity Authentication provides user and access management based on the following factors:

- User administration and integration with on-premise user stores
- User groups and application access management
- User self-service, for example, password reset, registration, and user profile maintenance
- System for cross-domain Identity Management (SCIM) API

Identity Authentication provides the following enterprise features:

- Branding of end user UIs
- Password and privacy policies
- Identity Authentication is interoperable with all application supporting SAML 2.0 standard or OpenID Connect (OIDC)

Identity Authentication has the following IdP proxy features:

- Authentication that is delegated to corporate IdP login
- Reuse of existing SSO infrastructure
- Easy and secure authentication for employee scenarios
- Federation based on the SAML 2.0 standard

Identity Authentication can connect to an on-premise user store. There is no user replication required to the cloud and no internal network ports must be exposed to the internet. Other Identity Authentication service product features can be used, including UI configuration policies and two-factor authentication.

## Accounts, User, and Member Management

### Best Practices for Managing Cloud Accounts

The following table outlines the best practices for managing cloud accounts.

#### Best Practices

|**Object**|**Recommendation**|
|---|---|
|Global Account|- For each commercial model (license type), you get a separate global account.<br>- Appoint at least one person as administrator. The administrator is responsible for adding new subaccounts, adding members to a global account, and managing the entitlements. We recommend that you also appoint at least one substitute administrator. If the main administrator leaves the company or is unavailable, it is important that you have someone who is available to take over these tasks.<br>- You purchase entitlements for each global account (according to your commercial model). The administrator of the global account distributes quotas to the individual subaccounts.|
|Directory|Appoint at least one person as administrator. The administrator is responsible for adding new subaccounts, managing members, and managing entitlements. We recommend that you also appoint at least one substitute administrator. If the main administrator leaves the company or is unavailable, it is important that you have someone who is available to take over these tasks.|
|Subaccount|- Each subaccount runs in exactly one region (data center) and one environment.<br>- Appoint at least one person as an administrator. The administrator is responsible for adding new members to the subaccount and assigning their business roles. We recommend that you also appoint at least one substitute administrator. If the main administrator leaves the company or is unavailable, it is important that you have someone who is available to take over these tasks.|

### User and Member Management

On the SAP BTP, member management happens at all levels from global account to space, while user management is done for deployed applications.

User accounts enable users to log on to SAP BTP and access subaccounts and use services according to the permissions given to them. We distinguish between two types of users.

The figure shows the user management for subaccounts.

![A diagram show how two different types of users, platform users and business users, use the subaccount. The text that follows includes more detail.](https://learning.sap.com/service/media/topic/e7c3d81c-9998-4d0f-a699-bacfb0b9e824/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Two_Types_Of_User_scr.png "A diagram show how two different types of users, platform users and business users, use the subaccount. The text that follows includes more detail.")

- Platform users are usually developers, administrators, or operators who deploy, administer, and troubleshoot applications and services on SAP BTP.
- Business users use the applications that are deployed to SAP BTP. For example, the end users of your deployed application or users of subscribed apps or services, such as SAP Business Application Studio, are business users.

Member management refers to managing permissions for platform users. A member is a user who is assigned to an SAP BTP global account or subaccount. Administrators can add users to global accounts and subaccounts and assign roles to them as needed. You can use predefined roles - for example, the administrator role for managing subaccount members.

User management refers to managing authentication and authorization for your business users. This is only done for your deployed applications.

### Account Model

The SAP BTP is structured according to global accounts, directories (optional), and subaccounts.

### Global Accounts

A global account is the realization of a contract you or your company has made with SAP.

A global account is used to manage subaccounts, members, entitlements, and quotas. You receive entitlements and quotas to use platform resources per global account and then distribute the entitlements and quotas to the subaccount for actual consumption. There are two types of commercial models for global accounts: the consumption-based model and the subscription-based model.

The figure shows the global account organization.

![A diagram shows a global account with three subaccounts, where each subaccount is attached to a region. Subaccount A is connected to Region X, Subaccount B to Region Y, and Subaccount C to Region Z.](https://learning.sap.com/service/media/topic/e7c3d81c-9998-4d0f-a699-bacfb0b9e824/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Global_Acc_Org_scr.png "A diagram shows a global account with three subaccounts, where each subaccount is attached to a region. Subaccount A is connected to Region X, Subaccount B to Region Y, and Subaccount C to Region Z.")

### Directories

Directories allow you to organize and manage your subaccounts according to your technical and business needs.

A directory can contain directories and subaccounts to create a hierarchy. Using directories to group other directories and subaccounts is optional - you can still create subaccounts directly under your global account.

You can create a hierarchical structure that is seven levels deep. The highest level of a given path is always the global account and the lowest is a subaccount, which means that you can have up to five levels of directories.

The figure shows the organizing subaccounts with directories.

![A hierarchical tree diagram shows the global account at the top, branching into a subaccount and directory, further expanding into additional subaccounts and directories at multiple levels.](https://learning.sap.com/service/media/topic/e7c3d81c-9998-4d0f-a699-bacfb0b9e824/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Org_Subacc_Dir_scr.png "A hierarchical tree diagram shows the global account at the top, branching into a subaccount and directory, further expanding into additional subaccounts and directories at multiple levels.")

Directories allow you to monitor usage and costs for contracts that use the consumption-based commercial model. In addition, you can also add the following features to your directories (optional):

- **Manage Entitlements:** This enables the assignment of a quota for services and applications to the directory from the global account quota for distribution to the directory's subaccounts. When you assign entitlements to a directory, you express the entitlements and maximum quota that can be distributed across its child subaccounts. You also have the option to choose the auto-assignment of a set amount of quota to all subaccounts created or moved to that directory. Subaccounts that are already in the directory when you select that option will not be auto-assigned quota.
- **Manage Authorizations:** This enables authorization management for the directory. For example, it allows certain users to manage directory entitlements. You can only use this feature in combination with the Manage Entitlements feature.

## Subaccount

Subaccounts let you structure a global account according to your organization's and project's requirements regarding members, authorizations, and entitlements.

A global account can contain one or more subaccounts in which you deploy applications, use services, and manage your subscriptions. The deployed applications are grouped into Space. Subaccounts in a global account are independent from each other. This is important to consider with respect to security, member management, data management, data migration, integration, and so on, when you plan your landscape and overall architecture.

The figure shows the subaccount structure.

![A diagram shows a global account with Subaccount A and Subaccount B. Each subaccount contains applications, services, and subscriptions.](https://learning.sap.com/service/media/topic/bc7973b7-c050-4a28-8508-a5fb3429440d/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Subaccount_Structure_scr.png "A diagram shows a global account with Subaccount A and Subaccount B. Each subaccount contains applications, services, and subscriptions.")

Each subaccount is associated with a region, which is the physical location where applications, data, or services are hosted. The specific region is relevant when you deploy applications and access the SAP BTP cockpit using the corresponding cockpit URL. The region assigned to your subaccount does not have to be directly related to your location. You could be in the United States, for example, but operate your subaccount in Europe.

The entitlements and quotas that have been purchased for a global account have to be assigned to the individual subaccounts.

## Technical Users

### Platform Users

Platform users are usually developers, administrators, or operators who deploy, administer, and troubleshoot applications and services on SAP BTP. They’re the users that you give certain permissions, for instance, at the global account or subaccount level.

Platform users who were added as members and who have administrative permissions can view or manage the list of global accounts, subaccounts, and environments, such as Cloud Foundry orgs and spaces. Members access them using the SAP BTP Cockpit, or the SAP BTP command line interface (CLI), or environment-specific CLI, such as the Cloud Foundry (CF) CLI.

For platform users, there's a default identity provider. We expect that you have your own identity provider. We recommend that you configure your custom tenant of Identity Authentication as the identity provider and connect Identity Authentication to your own corporate identity provider.

### Business Users

**Business users** use the applications that are deployed to SAP BTP. For example, these are the end users of SaaS apps or services, such as SAP Workflow service or SAP Cloud Integration, and the end users of your custom applications are business users.

Application developers (platform users) create and deploy application-specific security artifacts for business users, such as scopes. Administrators use these artifacts to assign roles, build role collections, and assign these role collections to business users or user groups. In this way, they control the users' permissions in the application.

For business users, there's a default identity provider. We expect that you have your own identity provider. We recommend that you configure your custom tenant of Identity Authentication as the identity provider and connect Identity Authentication to your own corporate identity provider.

### Member Management and User Management

**Member management** refers to managing permissions for platform users. You can think about it as managing the members of your team.

Member management happens at global account, directory, subaccount, and environment level. Members' permissions apply to all operations that are associated with the global account, the organization, or the space, irrespective of the tool used. Depending on the scope and the cloud management tools feature set you're using, you can manage members in different ways:

#### Managing Members

|Global Accounts|Directories|Subaccounts|
|---|---|---|
|You manage global account members by assigning role collections to platform users. Use the following predefined role collections:<br><br>- Global Account Administrator<br>- Global Account Viewer<br><br>Assign these role collections from the cockpit or the CLI.|You manage directory members by assigning role collections to platform users. Use the following predefined role collections:<br><br>- Directory Administrator<br>- Directory Viewer<br><br>Assign these role collections from the SAP BTP cockpit or the CLI.|You manage subaccount members by assigning role collections to platform users.<br><br>Note<br><br>Neo subaccounts don’t use role collections.<br><br>Use the predefined role collections, such as:<br><br>- Subaccount Administrator<br>- Subaccount Viewer<br><br>Assign these role collections from the SAP BTP cockpit (now Cloud Identity Services UI) or the CLI.|

#### Member Management in the Cloud Foundry Environment

|||
|---|---|
|Manage organization members on the _Members_ page at environment level in the cockpit or with the Cloud Foundry CLI.<br><br>A platform user added as an org. member can be either an **Org. Manager** or an **Org. Auditor**.|Manage space members on the _Members_ page at space level in the cockpit or with the Cloud Foundry CLI.<br><br>A platform user added as a space member can be either a **Space Manager**, **Space Developer**, **Space Auditor**, or **Space Supporter**.|

**User management** refers to managing authentication and authorization for your business users.

## How to Explore BTP Security

This demonstration guides you through the first steps to understand the SAP BTP security approach. You start with a global account from where you can drill down into the subaccount level. Your organization might have multiple global accounts, but most likely you will find multiple subaccounts.

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_DBFE6642A84B0A99:demo)

## How to Explore Accounts

This demo introduces the security-relevant structures that you will find in SAP BTP. When you sign a contract, you will get a global account from where you can build subaccounts and group them in directories. Depending on the level, you will find different security-relevant options from users and resources that you can access to external Identity Providers.

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_89566A85E712A7AC:demo)

## How to Explore Directories

This demonstration introduces you to the concept of directories. A directory allows you to group subaccounts and, if needed, the directory can also provide user management facilities (optional).

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_65ABC98A1BCD97B5:demo)

## How to Explore Users

This demo allows you to explore the user management functions and see at which levels users can be created, from global account, to directory, and to subaccount. Typically, technical users appear at the upper levels, while business users appear at the subaccount level.

Demo[  
](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_569AD0189A450985:demo)