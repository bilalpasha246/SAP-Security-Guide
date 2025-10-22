
Objective

After completing this lesson, you will be able to create and configure user accounts in SAP HANA Cloud using SAP HANA Cockpit or the SQL console.

## Creating User Accounts

Every person who wants to work with the SAP HANA database needs to have a personal database user account. Using SAP HANA cockpit or the SQL Console, you can create and manage standard and restricted database users.

Standard Users

Correspond to users created with the CREATE USER statement. By default they can create objects in their own schema and read data in system views. Read access to system views is granted by the PUBLIC role, which is granted to every standard user.

Restricted Users

Are created with the CREATE RESTRICTED USER statement, initially have no privileges. Restricted users are intended for provisioning users who access SAP HANA through client applications and who aren't intended to have full SQL access via an SQL console. If the privileges required to use the application are encapsulated within an application-specific role, then it's necessary to grant the user only this role. In this way, it can be ensured that users have only those privileges that are essential to their work. By default, restricted users can only connect to the database using HTTP or HTTPS protocols.

Compared to standard database users, restricted users are initially limited in the following ways:

- They cannot create objects in the database as they are not authorized to create objects in their own database schema.
- They cannot view any data in the database as they are not granted the standard PUBLIC role.
- They are only able to connect to the database using HTTP/HTTPS.

Note

For restricted users to connect via ODBC or JDBC, access for client connections must be enabled by executing the SQL statement ALTER USER <user_name> ENABLE CLIENT CONNECT or enabling the corresponding option for the user in the SAP HANA cockpit.

### Authorization Mode

The authorization mode indicates whether the user's authorization is based on LDAP group membership or local SAP HANA mechanisms.

The default user authorization mode is Local. This means that the user must be granted roles and privileges directly.

A user with authorization mode LDAP is granted roles exclusively based on their LDAP group membership. It is not possible to grant such a user other roles or privileges directly.

### Authentication Mechanism

When creating a user in SAP HANA, you need to specify how the user can be authenticated. The following authentication methods are available:

- User name and password (Local or LDAP)
    
    The user can be authenticated by a password stored locally in the SAP HANA database or remotely in a directory server.
    
- SAML
    
    The SAML identity provider must already exist and you must be authorized to assign it.
    
- X.509
    
    X.509 certificate uses a Public Key Infrastructure (PKI) to securely authenticate users. After users receive their X.509 certificates from a certificate issuing Certification Authority (CA), they can use them to securely access SAP HANA.
    
- JWT (JSON Web Token)
    
    The JWT identity provider must already exist and you must be authorized to assign it.
    

To create the user, select the _Save_ button. The user is created and appears in the list of users on the left. A new schema is created for the user in the catalog. It has the same name as the user.

### Custom User Properties

In the section custom user properties you can add the following parameters to the user account:

- Client - Specifies the session client to be used to filter the data according to the client specified in table fields such as MANDT or CLIENT.
- Locale - Specifies the locale (language, country/region) for the user.
- Priority - Specifies the priority with which the thread scheduler handles statements executed by the user. Priority values of 0 (lowest priority) to 9 (highest) are available; the default priority is 5.
- Statement Memory Limit - Specifies the maximum memory (in GB) that can be used by a statement executed by the user.
- Statement Thread Limit - Specifies the maximum number of threads that can be used by a statement executed by the user.
- Time Zone - Specifies the user's timezone. The standard database formats for locale and timezone are supported.

### Demonstration - Create SAP HANA Database User

Demo[](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?library=library.txt&show=project!PR_8D61768C1239A680:demo#2)

[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?library=library.txt&show=project!PR_8D61768C1239A680:demo#2)

### Creating an SAP HANA Database User Using SQL

SQL stands for Structured Query Language. It is a standardized language for communicating with a relational database. SQL is used to retrieve, store, or manipulate information in the database. To execute SQL queries, you need to use the SQL console or the SAP HANA HDBSQL tool.

The SQL Console is available in:

- SAP HANA Cloud Central - includes a SQL Console
- SAP HANA database explorer - cloud and on-premises include the SQL Console
- SAP HANA cockpit - cloud and on-premises have a SQL Console link to the SAP HANA database explorer

The following is the SQL reference documentation for the CREATE USER statement.

Code Snippet

```
CREATE [ RESTRICTED ] USER <user_name>
   [ <authentication_options> ]
   [ <validity_specification> ] 
   [ <set_user_parameters> ] 
   [ <ldap_group_authorization> ] 
   [ SET USERGROUP <usergroup_name> ]
```

If the user administrator creating the new user has the OPERATOR privilege on only one user group, the SET USERGROUP option is optional. If in such a scenario the SET USERGROUP is omitted, the user is assigned to the user group of the user administrator who executed the CREATE USER statement.

Note

In SAP HANA Cloud it is mandatory that a user is assigned to a user group. In SAP HANA on-premises, the user group assignment is optional.

The following example shows how to create a user **CLOUDADMIN01** with a password **Welcome1** and a validity from **now** until **01.01.2030**, having **cloud.admin01@example.com** as e-mail address, and is part of the **AdminGroup** .

SQL

```
CREATE USER CLOUDADMIN01 PASSWORD Welcome1 VALID FROM NOW UNTIL '2030-01-01' 
 SET PARAMETER "EMAIL ADDRESS" = 'cloud.admin01@example.com'
 SET USERGROUP "AdminGroup"
```

### Predefined Database Users

In the SAP HANA Cloud database, there are several predefined (or internal) database users, such as SYSTEM, SYS, _SYS_STATISTICS, and so on.

The most powerful database user, called SYSTEM, is reserved for use by SAP. The corresponding customer administration user is called DBADMIN. This user isn't intended for routine use and after using it to create other administration users, we recommend disabling it.

Note

In the on-premises SAP HANA database, the customer owns the SYSTEM user account. This user isn't intended for routine use and after using it to create other administration users, we recommend disabling it.

### Deleting a Database User

When database users that correspond to real people leave the organization, a user administrator must intervene to delete or deactivate these user accounts from the database. When a database user is deleted, any database objects that were owned by that user are automatically dropped, and any privileges granted by that user are automatically revoked.

Hint

If you want to keep the objects and granted privileges, it is better to deactivate the user account instead of deleting the account.

Database users created by an identity provider must be dropped manually by a user administrator. If the user is dropped on the LDAP server, the corresponding database user in SAP HANA is not automatically dropped.

### Summary

In this lesson, you learned what information is needed when creating an SAP HANA database user account. You also learned about the differences between a standard and a restricted user, what happens when you delete a database user, and gained insight in which predefined database users are available in SAP HANA.

### Further Reading

For further reading about SAP HANA user accounts, see the following sites:

**Using SAP HANA Cockpit**

- [Create a Database User | SAP Help Portal](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-database-administration-with-sap-hana-cockpit/create-database-user)
- [Create a Restricted Database User | SAP Help Portal](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-database-administration-with-sap-hana-cockpit/create-restricted-database-user)
- [Delete a Database User | SAP Help Portal](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-database-administration-with-sap-hana-cockpit/delete-database-user)
- [Deactivate a Database User | SAP Help Portal](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-database-administration-with-sap-hana-cockpit/deactivate-database-user)
- [Database User Details | SAP Help Portal](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-database-administration-with-sap-hana-cockpit/database-user-details)

**Using SQL Console**

- [CREATE USER Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/create-user-statement-access-control)
- [DROP USER Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/drop-user-statement-access-control)
- [ALTER USER Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/alter-user-statement-access-control)
- [USERS System View | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/users-system-view)
- [USER_PARAMETERS System View | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/user-parameters-system-view)