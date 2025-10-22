Objective

After completing this lesson, you will be able to use user groups.

## Using User Groups

### Understanding SAP HANA User Groups

![User groups can help managing large numbers of users when grouping them together on department level and assigning dedicated group admins to the groups.](https://learning.sap.com/service/media/topic/ac148cd3-1a60-4f50-8d44-1ab06826e142/HAHC94_2409_en-US_media/HAHC94_2409_en-US_images/UseGroups.png "User groups can help managing large numbers of users when grouping them together on department level and assigning dedicated group admins to the groups.")

User groups support a separation of user management tasks, allowing you to manage related users together. User groups are an efficient way to manage users. User groups can have:

- One or more dedicated group administrators
    
    Every user group has at least one dedicated group administrator. This makes it possible to delegate user management tasks to several users independently of each other. Only the designated group administrator(s) can manage the users in the group. This could be useful, for example, to protect highly privileged users or technical users from accidental deletion or manipulation.
    
- A group-specific configuration, such as password policy settings or client connect restrictions.
    

Caution

User groups don't control data access. A user's authorizations (roles and privileges) control data access.

You can create and manage users in user groups in the SAP HANA Cloud Central, SAP HANA cockpit, or using SQL.

### Demonstration: Creating a User Group Using SAP HANA Cockpit

Demo[](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?library=library.txt&show=project!PR_8AB0E36C2D0D9D8C:demo#2)

[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?library=library.txt&show=project!PR_8AB0E36C2D0D9D8C:demo#2)

### Creating User Groups Using SQL

The following is the SQL reference documentation for the CREATE USERGROUP statement.

Code Snippet

```
CREATE USERGROUP <usergroup_name>
 [ NO GRANT TO CREATOR ]
 [ SET PARAMETER <parameter_key_value_list> ]
 [ { ENABLE | DISABLE } PARAMETER SET <parameter_set_name> ]
 [ DISABLE CLIENT CONNECT ]
 [ CONNECT RESTRICTION <connect_restriction_list> ]
```

### Configuring User Groups

In addition to grouping users into meaningful categories, user groups also allow you to mass manage certain user settings and parameters. In this way, you can configure all users in a user group not only quickly but differently to users in other groups. Groups can be configured using the SAP HANA cockpit, or the CREATE | ALTER USERGROUP statement.

### Example 1: Create a User Group

This example creates a user group named **Cloud_Admins** and changes the minimal password length to 12, the maximum password lifetime to 90 days, and the maximum failed logon attempts to 3.

SQL

```
CREATE USERGROUP Cloud_Admins 
  SET PARAMETER 
    'minimal_password_length' = '12',
    'maximum_password_lifetime' = '90', 
    'maximum_invalid_connect_attempts' = '3'
  ENABLE PARAMETER SET 'password policy';
```

The users of different user groups may have different requirements when it comes to passwords. For example, you may want the passwords of technical users to be very complex. A group administrator can configure group-specific values for the individual parameters of the password policy.

Note

The password policy of a new user group is by default the password policy of the database.

There are two steps to configuring a group-specific password policy:

- Configuring the group-specific values of password policy parameters (SET PARAMETER)
- Enabling the parameter set ( ENABLE PARAMETER SET 'password policy')

If a group-specific value isn't explicitly set for a parameter, the value configured in the password policy of the database appears as the user group value in USERGROUP_PARAMETERS.

### Example 2: Assigning User Group Administrators

A user with the system privilege CREATE USERGROUP can create user groups. The database administrator DBADMIN initially has this privilege. By granting CREATE USERGROUP to a user, the database administrator can enable other users to create user groups.

These user group administrators can then designate one or more dedicated administrators for individual user groups by granting the object privilege USERGROUP OPERATOR on the user group, for example:

SQL

```
GRANT USERGROUP OPERATOR ON USERGROUP TechnicalUsers TO TechnicalUsersAdmin WITH GRANT OPTION;
```

### Group Setting: Client Connect Restrictions

Use the ENABLE | DISABLE CLIENT CONNECT option to control whether or not the users in a user group can connect to SAP HANA, for example, to temporarily stop users from connecting during updates or troubleshooting activities.

### Summary

In this lesson, you learned how to create and configure SAP HANA user groups using SAP HANA cockpit or using SQL.

### Further Reading

- [CREATE USERGROUP Statement (Access Control) | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-sql-reference-guide/create-usergroup-statement-access-control)
- [Password Policy Configuration Options | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/password-policy-configuration-options)