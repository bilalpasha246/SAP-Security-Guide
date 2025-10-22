![[Pasted image 20251008134118.png]]

**Authorization object class:** A logical grouping of authorization objects (for example, all authorization objects for object class FI beginning with "F_").

**Authorization object:** Groups of 1 to 10 authorization fields together. These fields are then checked simultaneously (example: F_LFA1_APP, vendor: application authorization).

**Authorization field:** The smallest unit against which a check is to be run (ACTVT, APPKZ).

**Authorization:** An instance of an authorization object, that is, a combination of allowed values for each authorization field of an authorization object.

**Authorization profile:** Contains instances (authorizations) for different authorization objects.

**Role:** Generated using Role Maintenance (transaction PFCG), and allows the automatic generation of an authorization profile. A role describes the activities of an SAP user.

**User/user master record:** Used for logging on to SAP systems and grants restricted access to functions and objects of the SAP system based on authorization profiles.

Naming conventions for customer developments (see SAP Notes _20643_ and _16466_):

- Authorizations and authorization profiles are Customizing objects and must therefore not be in the customer namespace (Y, Z). They must not include an underscore in the second position.
    
- Authorization classes, objects, and fields are development objects and must begin with Y or Z (customer namespace).

![[Pasted image 20251008134311.png]]

The authorization fields **BUKRS** (company code) and **ACTVT** (activity) are used in the following authorization objects, among others:

- **M_RECH_BUK**: Authorization to release blocked invoices for specific company codes.
    
- **F_BKPF_BUK:** Authorization to edit documents for specific company codes.
    
- **F_KNA1_BUK:** Assignment of the activities allowed in the company code-specific area of the customer master record.
    

In the authorizations for each authorization object, you can specify which activities (such as create, change, display, and so on) may be performed in which company code. Each object has a specific number of allowed activities, which are described in the object documentation.
![[Pasted image 20251008134914.png]]
- Authorization "A" allows the user to perform the activities create, change, and display in company codes 1000 and 2000.
- Authorization "B" allows the user to perform only the display activity in company codes 1000, 2000, and 3000.

If the user has authorization "A" and authorization "B", they work together. This means that the user can perform the create, change, and display activities in company codes 1000 and 2000, but can only perform the display activity in company code 3000.

![[Pasted image 20251008135126.png]]
You can define several different authorizations for an authorization object. This means that an authorization object has various instances.

Example: Authorization object _F_BKPF_BUK_ has the following authorizations:

- Work center 1: Authorized to create, change and display documents in company code 2000.
    
- Work center 2: Authorized to create, change and display documents in company code 1000.
    
- Work center 3: Authorized to display documents in company code 1000.
    

You can assign multiple authorizations to a work center. Grouped together, these authorizations are called an authorization profile.

Example: Work center 2 has the following authorization profile:

- Authorization to execute transaction code FB02 and FB03.
    
- Authorization to create, change, and display documents in company code 1000.
    
- Authorization to create, change, and display documents in business area 2000.
    
- Authorization to change and display document items for the accounts receivable account type.!

![[Pasted image 20251008135547.png]]
To provide users with user-specific menus after they have logged on to an SAP system, you use roles. These are defined using Role Maintenance.

A role is a set of functions, also known as **activities**, describing a specific work area. The "Accounts Receivable Accountant" role, for example, contains transactions, reports, and/or Internet/Intranet links that an accountant needs for his or her daily work.

In the role, you organize transactions, reports, or Web addresses in a **role menu**.

A large number of roles (>1200) are delivered with the standard SAP R/3 System. Before you define your own roles, check if one of the user roles delivered as part of the standard SAP R/3 System can be used.

Hint

Note that the predefined roles are delivered as templates, and begin with the prefix "SAP_".

For a user to receive authorizations, you must first maintain **authorization data**.

You can then generate the **authorization profile**, and the role is complete.

Hint

SAP strongly recommends the automatic creation of authorization profiles in the form of roles using Role Maintenance. You should only use manual authorization profiles in exceptional cases.

A role can be assigned to any number of users. Through the role, you also assign the authorizations that users need to access the transactions, reports, and so on, contained in the menu.

This **user menu** appears when the user to which the authorization profile was assigned logs on to the SAP system. A user menu consists of the role menus of the assigned roles. It contains the activities that are required by a group of users for their work area.