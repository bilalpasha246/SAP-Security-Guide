A user store is a system or database that stores information about users, such as their login credentials, personal information, and permissions. It is commonly used in software applications and websites to manage user accounts and access control. The user store allows the application to authenticate and authorize users and store and retrieve user-related data.![[Pasted image 20251007144133.png]]

SAP Identity Directory is a central SAP Cloud Identity Services component that stores and manages users and groups. It's the source of truth for users who have or will have access to SAP Cloud applications.

The Identity Directory in SAP Cloud Identity Services is the persistency layer inside the services. It is a user store used to manage the identities and access rights of users within an organization. This component facilitates identity lifecycle flows and unlocks critical new features, such as a user store for newer SAP BTP applications.![[Pasted image 20251007144326.png]]

Identity Directory can be used in the following use cases:

- Classic use case - the Local Identity Directory can be configured as a target and source system. See: [Configuring Local Identity Directory in Target-Source Scenario](https://help.sap.com/docs/identity-provisioning/identity-provisioning/configuring-local-identity-directory-in-target-source-scenario)
- Proxy mode - the Local Identity Directory as a proxy connector. See: [Configuring Local Identity Directory in Proxy Scenario](https://help.sap.com/docs/identity-provisioning/identity-provisioning/configuring-local-identity-directory-in-proxy-scenario)
- Merging attributes - read attributes of a single user in multiple source systems and merge the attributes in the directory. See: [Patched and Merged Attributes](https://help.sap.com/docs/identity-provisioning/identity-provisioning/patched-and-merged-attributes)

SAP recommends SAP Identity Management (IDM) for compliant identity management of a customer’s On-Premise systems for a hybrid landscape. SAP Identity Management is optimized for On-Premise systems. The SAP Cloud IPS is the recommended solution for identity lifecycle processes and cloud system provision. SAP customers with existing SAP IDM solutions can easily integrate with SAP Cloud IPS.![[Pasted image 20251007144517.png]]

Benefits of integrating SAP IDM and the SAP Cloud IPS include:
- An existing SAP Identity Management installation is unaffected when enabling hybrid identity management.
- Cloud-based business applications become available as supported systems in SAP IDM.
- SAP IDM capabilities, such as self-service workflow, are available.
- SAP IDM capabilities for reporting and auditing capabilities are available to cover cloud applications.
- SAP IDM and SAP Cloud IPS both support SCIM standards and interfaces for SCIM-based systems.