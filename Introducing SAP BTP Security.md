SAP Business Technology Platform is an open platform-as-a-service (PaaS) that delivers in-memory capabilities, core platform services, and unique microservices for building and extending intelligent, mobile-enabled cloud applications. SAP BTP is an integrated offering comprised of four technology portfolios:

1. Database and data management
2. Application development and integration
3. Analytics
4. Intelligent technologies

![[Pasted image 20251007111947.png]]

Application Development
This aspect of SAP BTP empowers developers to create, deploy, and manage applications efficiently. It offers various development tools and services supporting different programming languages and approaches. It provides developers with a collaborative and cloud-based environment with preconfigured tools and services for application development, enabling faster and more efficient development cycles. Also, SAP BTP supports low-code/no-code development, enabling business users to create applications without extensive coding knowledge. For more information, see: https://www.sap.com/products/business-technology-platform/low-code.html.

Automation
Automation within SAP BTP enables organizations to streamline repetitive tasks, improve efficiency, and reduce manual intervention in business processes. This could include SAP Build Process Automation for automating routine tasks such as data entry or invoice processing. SAP BTP also offers workflow automation capabilities, allowing organizations to easily design, execute, and monitor complex business workflows. Organizations can free up resources, minimize errors, and focus on higher-value activities that drive business growth by automating mundane tasks and workflows. For more information, see: https://www.sap.com/products/technology-platform/process-automation.html.

Integration
Integration is critical to SAP BTP, enabling seamless communication and data exchange between systems, applications, and data sources. SAP BTP offers the SAP Integration Suite to facilitate connectivity across On-Premise and cloud environments and with external partners and customers. There are also resources for API management and prebuilt business content for out-of-the-box solutions. For more information, see: https://www.sap.com/products/integration.html.

Data and Analytics
Data and analytics capabilities on SAP BTP empower organizations to derive insights from their data, make informed decisions, and drive business outcomes. This includes services for data warehousing, data modeling, and advanced analytics. For more information, see: https://www.sap.com/products/analytics.html.

Artificial Intelligence (AI)
SAP BTP offers comprehensive AI technologies and services like SAP AI Business Services and Generative AI Hub. They enable organizations to harness the power of artificial intelligence to foster innovation, enhance efficiency, and provide added value to customers. By applying these AI capabilities, organizations can stay ahead of the competition and thrive in today's digital economy. For more information, see: https://www.sap.com/products/artificial-intelligence.html.

Hyperscaler
Hyperscalers such as Google Cloud, Microsoft Azure, and Amazon Web Services offer a wide range of services and resources that can enhance the performance and capabilities of SAP BTP. Hyperscalers provide an extensive, scalable, and flexible infrastructure that can support the various services and applications offered by SAP BTP. Hyperscalers have big resilient data centers in several regions that offer high availability through cluster technology. Also, a hyperscaler can provide other benefits, such as security and cost-effectiveness. Ultimately, the decision to use a hyperscaler for SAP BTP depends on each organization's specific requirements and preferences.
![[Pasted image 20251007112250.png]]

SAP BTP includes global accounts, directories, and subaccounts as layers for managing and operating SaaS solutions and custom applications and services. This involves setting up a trust with SAP Cloud Identity Services for business users and platform users such as administrators, developers, and operators who work with SAP BTP.

SAP BTP distinguishes between the following:
- **Platform users** are usually administrators or operators (DevOps) who work with cloud management tools and deploy, administer, and troubleshoot services on SAP BTP. These users typically log on to the SAP BTP cockpit and work there. They can also be developers who use Cloud Foundry Spaces’ services.
- **Business users** use the business applications that are deployed on SAP BTP. For example, the end users of a deployed custom application or users of subscribed apps or services, such as SAP Business Application Studio, are business users.
![[Pasted image 20251007112518.png]]

The SAP BTP is organized in global accounts on the highest level, which multiple cloud infrastructure providers in different regions host. A global account reflects a contract with SAP and can consist of several directories and/or subaccounts that provide users with various applications and services. Furthermore, subaccounts can have multiple environments. Environments constitute the actual platform-as-a-service offering of SAP BTP that allows the development and administration of business applications. These environments are called spaces.
![[Pasted image 20251007112626.png]]

![[Pasted image 20251007112714.png]]![[Pasted image 20251007112750.png]]

Role collections consist of individual roles that combine authorizations for resources and services on SAP BTP. A role collection can comprise one or multiple roles. You only assign role collections to users, not individual roles. Roles and their authorizations are provided automatically to users via role collection assignments.