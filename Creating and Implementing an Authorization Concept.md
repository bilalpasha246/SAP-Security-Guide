![[Pasted image 20251008124618.png]]

The procedure used here is based on the principles of the SAP implementation method. Many consultancy companies use a similar model, usually with their own name. When combined, the individual steps of this method ensure quick and efficient implementation of the SAP system.

Setting up an authorization concept must be planned and implemented step-by-step using a project plan. In the example used here, the project was divided into five key points at the uppermost level (these are often also called phases):

- #### Project Preparation
    
    Inclusion of all relevant decision-makers for the SAP implementation and selection of the internal and external members of the project team.
    
- #### Business Blueprint
    
    The business requirements of the implementing company are determined. The Business Blueprint is a visual representation of the status of the company that is to be realized in the SAP implementation. All business processes are analyzed and described here. This is the basis for the later authorization concept.
    
- #### Implementation
    
    Configuration and fine tuning of the SAP system. The business processes created and described in the previous phase are the starting point for the implementation of the roles.
    
- #### Final Preparation
    
    Testing of all interfaces, training of users, and migration of business data into the SAP system.
    
- #### Go Live & Support
    
    Start of SAP production operation, specification of procedures, and measurement items for ongoing checking of the benefits of the investment in the SAP system.

![[Pasted image 20251008124958.png]]

To fulfill a certain task, the employee responsible must normally use several applications. The transactions and reports used for a business activity can be combined into roles.

It is important that users can only process those tasks that they are authorized to perform, and are prevented from making unintentional or incorrect changes in system areas that are outside their competence. Since all SAP components use authorizations to control access to their functions, administrators only assign those authorizations to each role that is necessary to perform the role-specific tasks.
#### Step 1: Preparation

![[Pasted image 20251008125229.png]]

Set up a team responsible for the specification and implementation of the user roles and the authorization concept.

Identify the business areas affected and their special security requirements. Like the control mechanisms selected, these can vary from area to area. Normally, the security requirements of the Human Resources department are more demanding than those of other departments. Therefore, you must first determine the desired security level.![[Pasted image 20251008125355.png]]When developing the role and authorization concept, the challenge is to coordinate business requirements at a cross-department level and protect sensitive data against potential dangers.

While user roles and the authorization concept are specified with the cooperation of the individual business areas, they are normally implemented by the IT department. This is why you must set up a cross-area and cross-department project team.

The team members have the following tasks:
- Create SAP-dependent role descriptions in the "Analysis & Conception" step.
    
- Cooperate with the IT department during implementation.
- 
- Set up and run through test scenarios.

To ensure that both the authorization concept and the procedures for user administration and authorization management comply with the control regulations of the company, the internal invoice verification department must be involved in the authorization project at an early stage.

#### Step 2: Analysis & Conception
![[Pasted image 20251008125525.png]]

Specification of the role and authorization concept:

- Identify required roles. Determine task profiles based on the organization chart and a business process analysis. Check if SAP role templates can be used.
    
- Specify relevant applications functions (transactions, reports, Web links) to the roles. Make any required adjustments if role templates are used.
    
- Specify if the roles are higher-level roles or specific roles; that is, if they are subject to any restrictions resulting from organizational or application-specific control mechanisms.
![[Pasted image 20251008125633.png]]

User roles are technically implemented using individual, composite, and derived roles. Based on the transactions and reports selected for each role, the Role Maintenance automatically determines all authorization objects required for performing the functions specified, and creates the corresponding authorization profile.

Using individual, composite, and derived roles, you can model the role structure in two ways:

- You can model each role as an individual role that contains all required functions. If some functions are used unchanged in multiple roles, the associated transactions and reports are contained in several individual roles. If general function modifications are required, this consequently affects several individual roles.
    
- Alternatively, you can model each role as a composite role consisting of individual and derived roles. In this case, the individual and derived roles represent activity blocks, that is, groups of interrelated functions (for example: all functions needed for a specific business scenario). Since individual and derived roles contain encapsulated functions, they can be used in multiple or composite roles. The advantage of this approach is that multiple access to transactions used in several individual roles is avoided. Therefore, organizational or process-related modifications that affect several user roles can be applied by adjusting a single role.![[Pasted image 20251008130005.png]]

The authorization list is a Microsoft Excel table that helps the project team to model the user roles before they are implemented in the SAP system. Using this list, the roles can be developed before the system is installed.

In the authorization list, you create user roles and specify the associated transactions. In this example, it consists of two worksheets:

- #### Sheet 1: Process View (Roles Design - Scope)
    
    The structure shows the business processes that were selected during the analysis and conception of the enterprise. The job roles and user roles are specified and linked with the processes here.
    
- #### Sheet 2: Transaction Overview for Each Role (T Code for Each Role)
    
    You can generate an overview of the transaction assignments for each role in the transaction overview (after the modeling on sheet 1).

![[Pasted image 20251008131445.png]]During the first conception and implementation approach, individual functions are encapsulated in separate roles (for example, the Basis authorizations of the end-users).

From a technical point of view, all elements of the authorization concept must be assigned a unique identifier. This is why you must define individual naming conventions for all role types.

You can define naming conventions based on different criteria, for example, country, business area (FI, CO, and so on), or application component (FI-AP, CO-PA, and so on).

#### Step 3: Implementation
![[Pasted image 20251008131730.png]]

From a technical point of view, user roles (job roles) can be implemented as composite roles using the Role Maintenance. Composite roles consist of individual and composite roles that each contain the relevant authorizations and menu data. Authorizations specify the scope of access to data and functions. User menus use hierarchical structures to specify the access path to the transactions, reports, and Internet pages released for a specific user.

An example of how you create user roles:

- Create individual roles: Individual roles either describe higher-level functions that are independent of organizational or application-specific restrictions or are used as templates for creating derived roles that are not subject to any restrictions.
    
- Having checked the individual roles used as the derivation basis, you create the derived roles. These contain the desired organizational or application-specific restrictions. For each responsibility area, you create a derived role from an existing individual role.
    
- Finally, the composite roles are created from the implemented individual and derived roles as the technical counterparts of the user roles.
#### Step 4: Quality Assurance & Tests

To ensure that productive operation is not affected, it is important to thoroughly test the user roles in connection with the authorizations before you switch over to production. In addition, the responsible area manager must approve of the role and authorization concept implemented.
![[Pasted image 20251008131910.png]]
To standardize the tests, the relevant process flows must be determined and published. You should use predefined test scenarios that cover all business processes implemented.

The test scenarios should include both **positive checks** and **negative checks** of the authorizations of the individual roles. The positive checks must determine whether the functions are executed as desired, while the negative checks must confirm that all restrictions defined are observed. For example, a human resources administrator can display the users for a specific work center, but not the records for other work centers. The test scenarios must cover all functions that are to be performed by a user role.

If a function cannot be called during the test, you must correct the user roles and the authorization concept. Note that changes may affect several (derived) roles. In extreme cases, you must revise the entire role and authorization concept.

You may also be required to modify the user menus to simplify access to the functions. To ensure that the system becomes more user-friendly, the project team responsible should closely cooperate with the representatives of the relevant business areas.

After fine-tuning the user roles, you must repeat the tests as often as necessary until the user roles implemented completely comply with the security and usability requirements.
#### Step 5: Cutover

Before you create the production users, you must create the master records for user management in your production environment, and possibly configure central user administration.
![[Pasted image 20251008132035.png]]

To simplify the creation of the individual user master records, you first create model records. These model records are used as copy templates for the records of the productive users. In the central system, create a user master record for each role specified in the company-wide role matrix (authorization list). If a role is subdivided into several responsibility areas that are subject to organizational restrictions (company code, cost center, plant, and so on) or application-specific control mechanisms (such as FI authorization groups), you must create a separate record for each responsibility area. Maintain the additional data (parameters, printers, and so on).

After consulting the area managers (data owners), define the roles for each user. Consider that some users may have several roles or different roles in various logical systems (clients). Enter the assignments in a user and role matrix.

To create a master record for a user, you copy the model record for the relevant role and customize this record as required.

Get the final approval of the area managers with regard to the users created and communicate all access-relevant data (system, client, ID, and password) to the end users.![[Pasted image 20251008132148.png]]
The SAP environment offers various possibilities for managing users. Users distributed in a far-reaching system landscape can be managed from within a central system. All users are initially created in a central logical system (client) and then distributed to the other clients in the entire installation.

Before you set up a central user management, you must determine which processes (for example, assigning or locking roles) can be run locally, and if modifications made in local systems (for example, address changes) should be passed on to the central system. Consistent central user management can be set up for such different SAP systems as SAP R/3, APO, and CRM.

After the role and authorization concept is implemented, the members of the project team are normally no longer responsible for managing users and authorizations. Depending on how the tasks are distributed in the company, the users are managed either centrally (for example, using a help desk) or on a decentralized basis (by local location or department administrators). You must assign and train employees for this purpose.
![[Pasted image 20251008132257.png]]
The tasks of the authorization administrators include creating, activating, changing, deleting, and transporting roles.

User administrators deal with setting up, changing, deleting, locking, and monitoring users, and assigning passwords and authorizations.

The user and authorization management tasks should be distributed among several administrators (for example, separate user, authorization data, and profile administrators). By dividing the tasks, you ensure that **no single administrator gets full control of user authorizations** ("dual control principle").

By assigning the user maintenance tasks to local administrators that represent individual departments or locations, you can even further decentralize user and authorization management. Having an administrator on site can also be desirable since first-time users accessing the system often need to be introduced to their task-specific user role. In addition, decentralized administrators are useful for reporting since they know to whom the user IDs refer.

From a technical point of view, decentralization is achieved by subdividing the users into user groups and limiting the rights of the local administrators with regard to the assignment of authorizations. Decentralized administrators may only maintain the users of the group that has been assigned to them. In addition, decentralized administrators should only be allowed to assign authorizations that are required in their department or at their site in accordance with the naming conventions of user roles