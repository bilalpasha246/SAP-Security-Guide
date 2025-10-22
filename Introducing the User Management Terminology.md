Objective

After completing this lesson, you will be able to explain the SAP HANA user management terminology and how they relate to each other.

## Introducing User Management

For user administrators involved in managing users in the SAP HANA environment, understanding the terminology associated with user management is essential for effectively implementing access controls, ensuring segregation of duties, and maintaining system security.

By familiarizing themselves with these key terms and their interrelationships, user administrators can efficiently orchestrate user management strategies, streamline access control implementation, and safeguard the integrity of the SAP HANA database environment.

SAP HANA user management features concepts such as user groups, roles, privileges, and user provisioning, each playing a crucial role in governing user access and permissions within the system.

### The User Management Terminology Explained

What is a Person?

A "Person" represents a human user, such as an employee, administrator, or any individual who requires access to the database for performing tasks or accessing data. Each person in the database is typically associated with a unique user ID and is assigned the appropriate access rights to limit the level of access to data and the actions that can be performed within the database.

Within user management processes, differentiating between human users (Persons) and technical or system users enhances clarity and helps in applying appropriate security and administrative policies.

What is a User Account?

A user account is a critical component that represents an entity with the ability to log into and interact with the SAP HANA database system. A user account is needed for both human users and technical or system users that require access to the database and its functionality.

What are Privileges?

Privileges are specific rights or permissions granted to user accounts or roles that determine what actions the users can perform and what resources they can access within the SAP HANA database system. Privileges ensure that only authorized users can perform certain tasks or access certain data, aligning with the principle of least privilege.

What is a Role?

A role is a collection of privileges that can be assigned to user accounts to grant them specific access rights and permissions within the SAP HANA database system. Roles serve as a mechanism to streamline and manage user authorizations by grouping related privileges together and simplifying the assignment process.

What is are User Groups?

User groups are a way to organize and manage users by grouping them based on specific characteristics, job roles, or business functions. User groups can have one or more dedicated group administrators to make it easier to administer users, especially in large and complex environments where individual user management can become cumbersome. User groups do not control data access. A user's authorization (roles and privileges) controls data access. By leveraging user groups, administrators can efficiently assign roles, manage privileges, and apply consistent policies to multiple users at once.

What are Role Groups?

Role groups support a separation of role management tasks. This is useful if you want different aspects of your authorization setup managed by different administrators. In an SAP HANA Cloud environment, SAP uses role groups to separate the management of customer-owned roles and SAP-owned roles and therefore the authorization on underlying objects.

Note

Role groups are only available within SAP HANA Cloud. The on-premises SAP HANA database doesn’t support role groups.

### User Provisioning Tasks

![The diagram shows the different tasks performed by a user administrator.](https://learning.sap.com/service/media/topic/dab9273a-4d41-4916-9328-55a699c0f1b6/HAHC94_2409_en-US_media/HAHC94_2409_en-US_images/User_01_Lifecycle.png "The diagram shows the different tasks performed by a user administrator.")

Initial User provisioning involves the following tasks:

- Creating user accounts
- Creating user groups
- Assigning user to user groups
- Creating roles
- Assigning roles and/or permissions to users
- Maintaining user parameters

After setting up the initial user and authorization concept, you need to make sure that the users and roles keep up to date with all the changes happening in your organization. To maintain the user and authorization structure, the following additional user administration tasks are required to be performed:

- Changing users authorizations due to job and role changes inside the company
- Deleting users when they leave the organization
- Reactivating users after too many failed log on attempts
- Deactivating users if a security violation has been detected
- Resetting user passwords

Normally these user provisioning tasks are divided over several user administrators (segregation of duties) to ensure that no single person has complete control over granting, modifying, or revoking user access to the database, reducing the risk of unauthorized access, data breaches, or other security vulnerabilities.

### Summary

In this lesson, you learned about the meaning of the terminology person, user accounts, privileges, roles, user groups, and role groups in the context of SAP HANA user management tasks performed by the user administrator.

### Further Reading

For further reading about SAP HANA user management, see the following sites:

**SAP HANA Cloud:**

- [User Management | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/user-management)
- [Privileges | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/privileges)
- [Database Roles | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/database-roles)
- [User Groups | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/user-groups)
- [Role Groups | SAP Help Portal](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-security-guide/role-groups)

**SAP HANA database:**

- [User Management | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/dea55d23bb571014bf25f6ed0d3b2b17.html)
- [Privileges | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/fb0f9b103d6940f28f3479b533c351e9.html)
- [Database Roles | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/e7f358b6e85b4610a2b62c5a25755fc0.html)
- [User Groups | SAP Help Portal](https://help.sap.com/docs/SAP_HANA_PLATFORM/b3ee5778bc2e4a089d3299b82ec762a7/b9174d035f274ce481387700c13b7d2c.html)