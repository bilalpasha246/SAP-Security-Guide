Assigning Users to a User Groups

Objective
After completing this lesson, you will be able to assign users to a user group.
Assigning Users to User Groups

To use all benefits from user groups, you must assign all database users to a user group. There are several ways to assign a user to a user group:

    Assigning the user group during user creation in the User Management app from SAP HANA cockpit.
    Moving existing users to a user group, using the User Group Management app from SAP HANA cockpit.
    During user creation, using the CREATE USER | ALTER USER SQL statement and using the syntax element SET USERGROUP.

Note
A user can belong to only one user group.
Demonstration - Assigning a User to a User Using Group SAP HANA Cockpit
Demo
Start Demo
Assigning a User to a User Group Using SQL

The following is the SQL reference documentation for the CREATE USER statement including theSET USERGROUP syntax element.
Code Snippet

CREATE [ RESTRICTED ] USER <user_name>
   [ <authentication_options> ]
   [ <validity_specification> ] 
   [ <set_user_parameters> ] 
   [ <ldap_group_authorization> ] 
   [ SET USERGROUP <usergroup_name> ]

The syntax element SET USERGROUP <usergroup_name> assigns the user during the creation to the specified user group. The syntax element SET USERGROUP is optional, if the SET USERGROUP is omitted, the user is assigned to the user group of the user administrator who executed the CREATE USER statement.
Example 1: Creating a User and Assign the User Group

This example creates a new user named Admin01 with the initial password Welcome1 as a member of the user group Cloud_Admins.
SQL

CREATE USER Admin01 PASSWORD Welcome12345 SET USERGROUP Cloud_Admins;

While in SAP HANA Cloud, all users must be assigned to a user group, it is not always necessary to specify the user group explicitly:

    If the user group administrator is the administrator of only one user group (in other words has the OPERATOR object privilege on only one group), users created by this administrator are automatically added to the user group.
    By executing the SET USERGROUP statement, you can specify the user group to which all users created within the current session are automatically added (until you execute the UNSET USERGROUP statement).

Example 2: Move a User to a User Group

This example moves the user Admin01 from the user group Cloud_Admins to the user group DEFAULT.
SQL

ALTER USER ADMIN01 SET USERGROUP DEFAULT;

To move a user from one group to another, the user group administrator needs to have the OPERATOR object privilege on both groups.

Summary

In this lesson, you learned how to assign SAP HANA user to SAP HANA user groups using SAP HANA cockpit or using SQL.
Further Reading

For further reading about SAP HANA user accounts, see the following sites:
Using SAP HANA Cockpit

    Create a database user | SAP Help Portal
    Change a Database User | SAP Help Portal

Using SQL Console

    Create a Database User | SAP Help Portal
    Alter a Database User | SAP Help Portal