
It is often necessary to specify different security policies for different types of database users. In the SAP HANA database, a distinction is made between database users that correspond to technical database users and real people.

Hint

Technically speaking, database users that correspond to real people and technical database users are the same; the only difference between them is conceptual.

### Technical Database Users

Technical database users do not correspond to real people and will not be deleted if a person leaves the organization. This means that technical database users should be used for administrative tasks such as creating objects and granting privileges for a particular application.

Some technical users are available by default, for example, the user SYS.

Other technical database users are created for application-specific purposes. For example, an application server may log on to the SAP HANA database using a dedicated technical database user.

Technical users are standard users created with the CREATE USER statement.

Note

For technical users, it is recommended to use the authentication mechanisms X.509, SAML, or JWT when possible. If password-based authentication is used, this will require any potential password changes to be performed for both the SAP HANA database and the client to avoid failed logon attempts or locking of the technical user due to such failed logon attempts.

### Real People Database Users

Every person who needs to work with SAP HANA must have a database user. Depending on your system configuration and scenario, database users can be created by:

- User administrators
- User group administrators
- Identity providers (LDAP, SAML, or JWT) used for user authentication and enabled for automatic user creation.

Standard or restricted database users are created manually with either SAP HANA cockpit or the SQL Console.

### Standard Users

Standard users are used for people who interact directly with the data and objects in the SAP HANA database.

### Restricted Users

Restricted users are used for people who interact via client applications with the data and objects in the SAP HANA database.

### SAP-Owned Users

Note

SAP-owned users are only used in SAP HANA Cloud.

In an SAP HANA Cloud environment, SAP is responsible for monitoring and configuring certain aspects of customer systems, for example, configuring TLS/SSL for the system and establishing trust to internal systems. Therefore, a number of SAP-owned technical users exist in the SAP HANA database. These users are managed by SAP and the authorizations in SAP HANA database ensure that they cannot be manipulated by customers. SAP-owned users in turn cannot influence users created by customers and do not have access to any data, tables, or objects created by customers – unless explicitly granted by the customer, for example, for support purposes.

To enforce the separation between SAP- and customer-owned database users and to facilitate basic operation and maintenance operations managed by SAP, the administration user for customers, DBADMIN, is not granted all system privileges available in the SAP HANA database in an SAP HANA Cloud environment. One example of such a system privilege is USER ADMIN. Users created by the customer side must be managed using user groups.

### Summary

In this lesson, you learned about the difference between technical user accounts and real people user accounts. For user accounts that represent real people, you learned that when a person directly interacts with the SAP HANA database, a standard user is required, but when a real person connects via an application to SAP HANA, a restricted user will be sufficient. In the context of SAP HANA Cloud, you learned that there are also SAP-owned user accounts used by SAP for monitoring and configuration purposes.

### Further Reading

For further reading about the different user types in SAP HANA, see the following sites:

**SAP HANA Cloud:**

- [User Types | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/user-types)
- [SAP Owned users | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/user-management)
- [Predefined users | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/predefined-users)

**SAP HANA database:**

- [User Types | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/dec8d273bb571014b4c2b771d3e0f166.html)
- [Predefined Database users | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/de4ee8bbbb5710148a04f023da147c8d.html)