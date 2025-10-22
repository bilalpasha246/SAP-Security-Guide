Objective

After completing this lesson, you will be able to create roles using SAP HANA Cockpit or the SQL console.

## Creating Authorization Roles

### Database Roles

A database role is a collection of privileges that can be assigned to either a database user or another role. You can create and assign roles in the SAP HANA cockpit, or use SQL.

A role typically contains the privileges required for a particular function or task, for example:

- Business users reading reports using client tools such as Microsoft Excel
- Modelers creating models and reports
- Database administrators operating and maintaining the database and its users

Privileges can be granted directly to users of the SAP HANA database. However, roles are the standard mechanism of granting privileges as they allow you to implement complex, reusable authorization concepts that can be modeled on business roles.

Roles in the SAP HANA database can exist as runtime objects (catalog roles), or as design-time objects (HDI roles). HDI roles are defined during application development using the SAP Business Application Studio. The HDI roles are not in scope for this learning journey.

### Catalog Roles

A role administrator needs the ROLE ADMIN privilege to create catalog roles in the runtime of the SAP HANA system. These catalog roles can be created and assigned using SQL or using SAP HANA cockpit.

Roles can be revoked by the granting role administrator database user or another role administrator database user who has the ROLE ADMIN privilege.

If the granting role administrator database user is dropped (not necessarily the role creator), all roles that were granted by this role administrator database user are revoked.

Note

A user with ROLE ADMIN can't revoke roles granted by technical users SYS and _SYS*.

The Runtime (Catalog) roles have the following properties:

- Roles cannot be transported between systems.
- There is no version management.
- Roles are owned by the database user who creates them.
- Roles are granted directly by the database user using the SQL GRANT and REVOKE statements.

### Demonstration - Create Catalog Roles Using SAP HANA Cockpit

Demo[](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?library=library.txt&show=project!PR_2705726F49191693:demo#2)

[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?library=library.txt&show=project!PR_2705726F49191693:demo#2)

### Using SQL to Create Roles

The following is the SQL reference documentation for the CREATE ROLE statement.

SQL

```
CREATE ROLE <role_name> [ SET ROLEGROUP <rolegroup_name> ]
   [ LDAP GROUP <ldap_group_list> ] [ NO GRANT TO CREATOR ]
```

The following example shows how to create the role **Admin_Resource**.

Code Snippet

```
CREATE ROLE Admin_Resource;
```

### Grouping Roles in Role Groups

![The image shows the use of role groups.](https://learning.sap.com/service/media/topic/e5ca749b-e85c-4791-8f13-93ce51472a42/HAHC94_2409_en-US_media/HAHC94_2409_en-US_images/RoleGroups.png "The image shows the use of role groups.")

In the SAP HANA cockpit role management application, it's also possible to group rules together in a _Role Group_ with a single name. This _Role Group_ name can later be used to search for roles in the SAP HANA cockpit role assignment application.

Note

You'll use the _Role Group_ name to find roles, but the separate roles will still be assigned to the user, the _Role Group_ will not be added.

Below the SQL reference documentation for the CREATE ROLEGROUP statement.

SQL

```
CREATE ROLEGROUP <rolegroup_name> [ NO GRANT TO CREATOR ] [ ENABLE ROLE ADMIN ]
```

The following example shows how to create a role group **Admin_Senior** and assign then new roles **Admin_Inifiles**, **Admin_Backup**, and existing role **Admin_Resource** to the role group.

SQL

```
CREATE ROLEGROUP Admin_Senior;
CREATE ROLE Admin_Inifiles SET ROLEGROUP Admin_Senior;
CREATE ROLE Admin_Backup SET ROLEGROUP Admin_Senior;
ALTER ROLE Admin_Resource SET ROLEGROUP Admin_Senior;
```

Use the role group in SAP HANA cockpit to find the included roles, and individually assign them to users.

### Summary

In this lesson you learned why using authorization roles is better than assigning privileges directly to a user account. You also learned how to create user roles and how you can group them in role groups for easier role management.

### Further Reading

For further reading about SAP HANA user management, see the following sites:

**SAP HANA Cloud:**

- [Roles | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/database-roles)
- [Role Groups | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/role-groups)
- [CREATE ROLE Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/create-role-statement-access-control)
- [CREATE ROLEGROUP Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/create-rolegroup-statement-access-control)
- [Catalog Roles and Design-Time Roles Compared | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/catalog-roles-and-design-time-roles-compared)

**SAP HANA database:**

- [Roles | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/e7f358b6e85b4610a2b62c5a25755fc0.html)
- [CREATE ROLE Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/4fe29514fd584807ac9f2a04f6754767/20d4a23b75191014a182b123906d5b16.html)
- [Catalog Roles and Design-Time Roles Compared | SAP](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/3360ac839b844171837dce4f7c5f1481.html)