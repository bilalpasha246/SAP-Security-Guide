
Security Expectations

Requirements for protecting sensitive data:

- A company must meet certain legal requirements based on their country of operation. These include, for example, data protection laws (personal data, family status, illnesses, and so on), or employee protection.
    
- A company must be able to adhere to agreements with and requirements of partners and vendors, and to ensure their implementation.
    
- A company must publish and enforce security policies, so that a secure environment can be established and maintained. This applies both to data used externally and to data used internally.
    

Cost-Benefit Relation

- There are a large number of different possible threats. Perfect security could only be achieved with cross-dimensional assignment of authorizations. However, the benefits achieved in this way are often not relative to the costs incurred.
    
    With some values, it is cheaper to replace a loss than to protect the data at great expense. A company should therefore concentrate on areas in which a clear benefit can be realized through this expenditure. This saves unnecessary investments of time and money.
    
- It is impossible to ensure complete security against all potential threats. Therefore, a company must be able to weigh up the extraordinary risks of a threat against the costs of a security system.

![[Pasted image 20251008113023.png]]

When developing a security concept, you must first determine **what** you want to make safe. Which **assets** must be protected? To which categories do these assets belong (for example: hardware, software, data, persons)? When assigning assets to categories, consider the consequences of losing these assets. When calculating the value of fixed assets, for example, you should take into account the loss of value due to depreciation, damage, or theft.

You must also determine **against what** you want to protect your assets. What are potential **dangers**? Sources of danger could be, for example, technology, the environment, or persons.

- Persons: Important employees leaving the company, dissatisfied or inexperienced employees. Hackers with criminal intent.
    
- Technology: Processing errors (caused by applications or operating systems), viruses, power supply interruption, hardware failure.
    
- Environment: Fire, flood, dust, earthquakes.

Once you have identified your assets and the potential sources of danger, you can develop security mechanisms. You must determine an appropriate protective measure for each source of danger. These **measures** should also be assigned to different categories (for example: organizational, technical, environmental).

- Organizational measures; Training, internal security policy, procedures, roles, responsibilities.
    
- Technical measures: Inclusion of electronics for checks (routers). Access authorizations for systems and data.
    
- Environmental measures protect physical system components against natural sources of danger.


![[Pasted image 20251008113232.png]]

To avoid unauthorized system access, for example, system and data access control mechanisms are provided at the application level.

When protecting an SAP system, you must consider the following:

- Security must be implemented at all levels, since the overall security depends on the weakest part.
    
- A complex authorization concept is therefore only one aspect of an overall security concept.
    
This course deals only with the security mechanisms at application level. The other levels are covered in the SAP courses ADM950 and ADM960.

![[Pasted image 20251008113342.png]]![[Pasted image 20251008113550.png]]**People** perform **roles** that belong to **business scenarios**. In the example above, _Karen_ performs the "Create Purchase Requisition" role in the PROCUREMENT business scenario.

A **person** can have multiple **roles**. _John_, for example, has been assigned the roles "Service Representative", "Create Purchase Requisition", and "Release Purchase Requisition".

A **role** is a group of **activities** performed within business scenarios. For example, the activity CREATE PURCHASE REQUISITION belongs to the "Create Purchase Requisition" role.

A **role** generally includes all **activities** that may occur in the respective **scenario**.

A single role can be involved in several **scenarios**. The EMPLOYEE, for example, participates in the SELF-SERVICES and the REPORTING scenarios, among others.

A single **scenario** may require the participation of multiple **roles**. In this way, the roles "Service Representative", "Create Purchase Requisition", "Release Purchase Requisition", and, for the supervisor, the role "Business Purchaser" are all involved in the PROCUREMENT scenario.

**Business scenarios** are groups of **activities** performed by one or more **employees** in their respective **roles**. The PROCUREMENT scenario, for example, comprises the activities CREATE PURCHASE REQUISITION, RELEASE PURCHASE REQUISITION, and CREATE PURCHASE ORDER.


![[Pasted image 20251008113845.png]]


To implement roles technically, you must create roles (or composite roles) using the Role Maintenance.

A role consists of the following components:

- Role Menu
    
    The **transactions**, reports, Web links, and so on, in a role are combined into a **menu**, to which the users of the role have access.
    
- Authorizations
    
    The **authorizations** define the access rights for business functions and data.
    
- User
    
    To grant the access rights of a role to a **user**, you must assign the user to the role. You can assign users using either the Role Maintenance or user administration.
    

SAP delivers a large number of predefined roles with SAP systems. Customers can use these roles as templates and customize them to meet their individual requirements. You can use the report RSUSR070 and the selection "SAP*" to display all the role templates that are supplied by SAP.