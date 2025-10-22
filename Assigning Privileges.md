Objective

After completing this lesson, you will be able to assign privileges to roles and users.

## Assigning Privileges to Roles and Users

### Describing the Basic Authorization Entities

Before we can start building our authorization and security concept in SAP HANA, it is important to understand the basic authorization entities and the relationships between them. The basic authorization entities are defined as follows:

The basic authorization entities are defined as follows:

User

Identifies the person accessing the system.

Role

Roles are a collection of privileges. They can be granted to a user or to another role (nesting).

Privilege

Privileges are used to impose restrictions on operations carried out on an object. They can be granted to a user or to a role.

Object

Any database object, for example, table, view, stored procedure, schema in the system.

### Describing Privileges Types

To perform operations in the SAP HANA database, a database user must have the necessary privileges. SAP HANA has system, object, analytical privileges, and privileges on users. The on-premises SAP HANA database has additional package and application privileges used in the deprecated SAP HANA extended services, classic model.

Privilege types are used in SAP HANA Cloud and SAP HANA on-premises:

- **System privileges** control general system activities. They're mainly used for administrative purposes, such as creating schemas, creating and changing users and roles, performing data backups, managing licenses, and so on.
- **Object privileges** are used to allow access to and modification of database objects, such as tables and views. Depending on the object type, different actions can be authorized (for example, SELECT, CREATE ANY, ALTER, DROP, and so on).
- **Analytic privileges** are used to control read access to data in SAP HANA information models pending on certain values or combinations of values.
- **Privileges on users** are SQL privileges that users can grant on their user. ATTACH DEBUGGER is the only privilege that can be granted on a user.
    
    For example, User A can grant User B the privilege ATTACH DEBUGGER to allow User B to debug SQLScript code in User A's session. User A is the only user who can grant this privilege. Note that User B also needs the object privilege DEBUG on the relevant SQLScript procedure.
    

Privilege types used exclusively for SAP HANA on-premises:

- **Package privileges** granted to developers using the SAP HANA extended application services, classic model (XSC) authorize application development tasks on individual packages in the classic SAP HANA repository.
    

Caution

SAP HANA extended application services, classic model (XSC) has been announced as deprecated. See [SAP Note 2465027 - Deprecation of SAP HANA extended application services, classic model and SAP HANA Repository](https://me.sap.com/notes/2465027)

Privileges granted on a classic repository package are implicitly assigned to the design-time objects in that package, as well as to all sub-packages. Users are only allowed to maintain objects in a repository package if they have the necessary privileges for the package in which they want to perform an operation, for example, to read or write to an object in that package.

- Note
    
    With SAP HANA extended application services, advanced model (XSA), versioning source code, and web content is not stored in the SAP HANA database. This means that package privileges are not used in XSA.
    
- **Application Privileges** define the authorization level required for access to an XSC application, for example, to start the application or view particular functions and screens.
    
    Application privileges can be assigned to an individual user or to a group of users, for example, in a role. The role can also be used to assign system, object, package, and analytic privileges. You can use application privileges to provide different levels of access to the same application, for example, to provide advanced maintenance functions for administrators and view-only capabilities to normal users.
    

- Note
    
    With SAP HANA extended application services, advanced model (XSA), application privileges are not used. Application-level authorization is implemented using OAuth and authorization scopes and attributes.
    

### Assigning Privileges

Privileges can be granted to database users either directly, or indirectly through roles that they've been granted. In this case, the privileges are inherited. Roles are the standard mechanism of granting privileges to users.

Users must have both the privileges to perform the operation and to access the resources (such as schemas and tables) to which the operation applies.

### Demonstration - Assigning Privileges Using SAP HANA Cockpit

Demo[](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?library=library.txt&show=project!PR_ECBE3090AEDEE287:demo#2)

[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?library=library.txt&show=project!PR_ECBE3090AEDEE287:demo#2)

### Assigning Privileges Using SQL

The following is the SQL reference documentation for the GRANT statement.

Code Snippet

```
{ GRANT <system_privilege>[{, <system_privilege>}...] TO <grantee> [ WITH ADMIN OPTION ]
   | GRANT <source_privilege>[,...] ON REMOTE SOURCE <source_name> TO <grantee> [ WITH GRANT OPTION ]
   | GRANT <schema_privilege>[,...] ON SCHEMA <schema_name> TO <grantee> [ WITH GRANT OPTION ]
   | GRANT <object_privilege>[,...] ON <object_name> TO <grantee> [ WITH GRANT OPTION ]
   | GRANT <role_name>[,...] TO <grantee> [ WITH ADMIN OPTION ]
   | GRANT <role_in_a_rolegroup>[{, <role_in_a_rolegroup>}...] TO <grantee> [ WITH ADMIN OPTION ] [ USING GROUP ]
   | GRANT { ALTER | DROP | REFERENCES } ON { JWT | SAML | X509 } PROVIDER <provider_name> TO <grantee> [ WITH GRANT OPTION ]
   | GRANT { ALTER | DROP | REFERENCES } ON PSE <pse_name> TO <grantee> [ WITH GRANT OPTION ]
   | GRANT <user_role_group_privilege>[,...] ON { USERGROUP <usergroup_name>   | ROLEGROUP <rolegroup_name> } TO <grantee> [ WITH GRANT OPTION ] [ USING GROUP ]
   | GRANT { ALTER | DROP | REFERENCES } ON ADAPTER <adapter_name> TO <grantee> [ WITH GRANT OPTION ]
   | GRANT <object_privilege>[,...] ON PSE <pse_name> TO <grantee> [ WITH GRANT OPTION ]
   | GRANT STRUCTURED PRIVILEGE <structured_privilege> TO <grantee> [ WITH GRANT OPTION ]}
```

**Example 1:** This example shows how to grant the **INIFILE ADMIN** and **TRACE ADMIN** privileges to the user **CLOUDADMIN01**, and allow the user CLOUDADMIN01 to grant these privileges to others.

SQL

```
GRANT INIFILE ADMIN, TRACE ADMIN TO CLOUDADMIN01 WITH ADMIN OPTION;
```

The **WITH ADMIN OPTION** allows a user to grant these privileges to other users.

**Example 2:** This example shows how to grant the **SELECT** privilege on schema **CLOUDDMIN01** to the role **Cloud_DBAdmin_Role**.

Code Snippet

```
GRANT SELECT ON SCHEMA cloudadmin01 to Cloud_DBAdmin_Role;
```

**Example 3:** This example shows how to grant the role **Cloud_DBAdmin_Role** to the user **CLOUDADMIN01**.

Code Snippet

```
GRANT Cloud_DBAdmin_Role TO CLOUDADMIN01 WITH ADMIN OPTION;
```

### Summary

In this lesson you learned how to assign privileges to users and roles in SAP HANA using the SAP HANA cockpit or SQL console. It emphasizes the importance of assigning privileges to roles rather than directly to users.

### Further Reading

For further reading about SAP HANA privileges see the following sites:

**SAP HANA Cloud:**

- [System Privileges (Reference) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/system-privileges-reference)
- [Object Privileges (Reference) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/object-privileges-reference)
- [Analytic Privileges | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/analytic-privileges)
- [GRANT Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/grant-statement-access-control)
- [REVOKE Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/revoke-statement-access-control)

**SAP HANA database:**

- [System Privileges (Reference) | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/4c6d4c4167ed42bcbbb2a0ed87790607.html)
- [Object Privileges (Reference) | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/8978bfdfcf3b45f9acf3fdb0964d3d9c.html)
- [Analytic Privileges | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/db08ea0cbb571014a386f851122958b2.html)
- [Package Privileges | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/5bb08abc86014e08aad64648cdb95ef9.html)
- [Application Privileges | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/7569092e89c244bd9404ccbfe5d3a2b7.html)
- [GRANT Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/4fe29514fd584807ac9f2a04f6754767/20f674e1751910148a8b990d33efbdc5.html)
- [REVOKE Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/4fe29514fd584807ac9f2a04f6754767/20fc91cb75191014ac15eb4d6f2d7dde.html)