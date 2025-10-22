Objective

After completing this lesson, you will be able to describe object ownership rules and effects.

## Describing Object Ownership

Before we can manage authorizations in SAP HANA, it is important to understand the basic ownership concept for database objects, such as, tables or schemas, and the implications of this concept.

The owner of an object is the user who creates the object. Generally speaking, only the object owner can initially access the object and grant object privileges to other users. However, all objects are located in a schema and the schema itself it is an object with an owner. The schema owner may be different to the owners of objects contained within the schema.

Object

An object refers to a database entity that can be created and managed within the database. Objects can include tables, views, procedures, functions, triggers, indexes, and other database components. Each object has its own set of properties and attributes that define its structure and behavior within the database. Objects in the SAP HANA database can be created, modified, deleted, and queried to store and retrieve data, as well as to perform various database operations.

Owner

An owner refers to the user or identity that has created a particular database object, such as a table, view, procedure, function, or other database component. The object owner has the rights and privileges to create, modify, and control access to the object, and is typically responsible for managing the object's properties and behavior within the database. Object owners can grant or revoke permissions and access rights to other users or roles, and are responsible for maintaining the integrity and security of the objects they own.

Schema

A schema is a collection of database objects, such as tables, views, procedures, functions, and other database components. It provides a way to organize and manage these objects within the database, allowing users to group related objects together based on their functionality or purpose. Every schema has an owner who has access to all objects inside the schema. Every user who has access to a schema can create objects in that schema. These objects are owned by the object creator.

### Database Object Ownership

In SAP HANA, the object ownership rules dictate who can access and manage objects within the database. The ownership of an object in SAP HANA is determined by the following criteria:

1. The owner of the object: The user who creates the object becomes its owner by default and has full control and access to the object.
2. The owner of the schema: The user who owns the schema in which the object is located also has control and access to the object. This means that the schema owner has the authority to manage and grant permissions on the objects within the schema.
3. Users to whom the owner of the object has granted privileges: The object owner can grant specific privileges to other users, allowing them to access and manipulate the object.
4. Users to whom the owner of the parent schema has granted privileges: If the parent schema owner grants certain privileges to other users, those users may also have access to the objects within that schema.

These ownership rules help to ensure proper access control and security within the SAP HANA database environment.

When you apply the object ownership rules to the previous video, the following can be concluded:

- User HAN owns the schema HAN and MF, and has full control and access to all object inside both schemas.
- User REY owns the schema REY, and has full control and access to all object inside schema REY.
- User REY can create objects in the schema HAN, because user REY was granted the privilege to create objects in schema HAN.
- User REY created the table ORDERS inside schema HAN. As owner of the schema HAN, user HAN has also access to the table ORDERS.
- User HAN created the table SALES inside schema MF. Only the owner, user HAN, has access to this table.

### The Impact of Dropping Database Users

Dropping a database user in SAP HANA is performed according to the following rules:

1. If a user owns no objects, except its own empty schema, then the user can simply be dropped.
2. If a user owns objects, neither the user nor any of the objects owned by that user will be deleted. To drop a user including the dependent objects, the drop operation needs to be executed with the "cascade" option.

Reviewing the previous video, let's analyze what happens if one of the users is dropped. The following rules apply:

- For both scenarios the cascade option needs to be used, as both users own other objects beside their own empty schema.
    
- In the scenario where only the user REY is dropped with the "cascade" option, the table HAN.ORDERS and the schema REY are dropped.
    
- In the scenario where only the user HAN is dropped with the "cascade" option, the schema MF and the table MF.SALES are dropped. Also, the table HAN.ORDERS (owned by REY) in the schema HAN is dropped.
    

The deletion of users also has an impact on the privileges that the user granted to others. When a user is dropped, all the privileges granted by that user to other users or roles are also revoked.

Let's look at the implications of the ownership concept in the case where one of the users needs to be dropped. The following rules apply:

- You can only drop a user if they own no objects (except their own schema). If dependent objects exist, neither the user nor any of the objects owned by that user will be deleted.
    
- If the user owns further objects, the only option is to drop the user with the "cascade" option. This means that all the objects owned by the user are dropped and all the privileges on these objects are revoked.
    
- If one of the objects of the user that is going to be dropped is a schema, all the objects located in that schema are also dropped (even if they are owned by a different user).
    

### SAP HANA Cockpit: Dropping a Database User

When a user is dropped using SAP HANA Cockpit, all the related database objects to be dropped are shown. This makes it easy to analyze the impact of the DROP USER action.

![The list of affected objects from the DROP USER <user_name> CASCADE is shown.](https://learning.sap.com/service/media/topic/a35dca97-782e-47d9-a222-c076d71a1d26/HAHC94_2409_en-US_media/HAHC94_2409_en-US_images/DropUserCascade01.png "The list of affected objects from the DROP USER <user_name> CASCADE is shown.")

### SQL: Dropping a Database User

Dropping a user using the SQL command DROP USER <user_name> CASCADE is riskier as the SQL statement will drop the user without displaying objects to be dropped.

As a best practice, first check the ownership and the related database objects before dropping a user using SQL.

Depending on the type of object you would like to analyze, the ownership of the objects in your SAP HANA database system can be analyzed using the system views named "OWNERSHIP," "SCHEMAS," or "ROLES."

### Reviewing Objects Owned by a User

Use the following SQL statement on the OWNERSHIP view to find all objects owned by user HAN:

SQL

```
SELECT OWNER_NAME,OBJECT_TYPE,SCHEMA_NAME,OBJECT_NAME FROM PUBLIC.OWNERSHIP WHERE OWNER_NAME = 'HAN';
```

### Reviewing Schemas Owned by a User

Use the following SQL statement on the SCHEMAS view to find all schemas owned by user HAN:

SQL

```
SELECT SCHEMA_NAME,SCHEMA_OWNER FROM PUBLIC.SCHEMAS WHERE SCHEMA_OWNER = 'HAN';
```

### Reviewing Roles Created by a User

For roles there is no ownership, but there is the role creator. Having a clear overview of who created which role is beneficial before dropping a user.

Note

Dropping the creator of a role does **NOT** drop the role.

Use the following SQL statement on the ROLES view to find which roles were created by user SYSTEM:

SQL

```
SELECT * FROM ROLES WHERE CREATOR = 'SYSTEM';
```

### Revoking Privileges

Similar to dropping a user, revoking a privilege from a user can also provoke a "recursive" revoking situation in cases where the privilege was extended further to other users or roles.

To understand this, you should know that the following options for granting privileges exist:

Granting a privilege to a user or role

This option allows user HAN to grant a privilege to user REY. User REY is not allowed to further extend this privilege to others.

Granting a privilege to a user or role with GRANT/ADMIN option

This option allows user HAN to grant a privilege to user REY. User REY is allowed to extend this privilege to others. For example, user REY can extend the same privilege to user MAZ.

Note

To grant a privilege, the user granting the privilege should be the "owner" of the privilege (owner of the object related to the privilege) or should have the privilege assigned to them with the GRANT/ADMIN option.

In the example, user HAN granted a privilege to user REY with the GRANT/ADMIN option. Afterwards, user REY granted the same privilege to user MAZ.

If user HAN revokes the privilege from user REY, the privilege is also revoked indirectly from user MAZ as user REY no longer has the privilege. This also happens if user HAN is dropped from the database, this revokes the privilege from user REY and user MAZ.

### Summary

In this lesson, you learned about the meaning of the terms object, owner, and schema and how object ownership works in the context of the SAP HANA database. You learned how to use the OWNERSHIP, SCHEMAS, and ROLES views to identify the owner of an object. You also learned the implications of granting and revoking privileges.

### Further Reading

**SAP HANA Cloud:**

- [GRANT Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/grant-statement-access-control)
- [REVOKE Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/revoke-statement-access-control)
- [Granting and Revoking Privileges and Roles | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/granting-and-revoking-privileges-and-roles)

**SAP HANA database:**

- [GRANT Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/4fe29514fd584807ac9f2a04f6754767/20f674e1751910148a8b990d33efbdc5.html)
- [REVOKE Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/4fe29514fd584807ac9f2a04f6754767/20fc91cb75191014ac15eb4d6f2d7dde.html)
- [Prerequisites for Granting and Revoking Privileges and Roles | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/c719b2e7d9761014b9d798770c3d0958.html)