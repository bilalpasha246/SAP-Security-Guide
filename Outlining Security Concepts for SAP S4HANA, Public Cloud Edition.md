Access to business applications is controlled by role-based authorization management. To this end, business roles are assigned to business users to provide access to applications and functionality for a user's job requirements. Once a business user is assigned a business role, they can access applications through business catalogs.

The following graphic illustrates the elements of the authorization concept:
![[Pasted image 20251007105029.png]]

- A business user is an employee, contractor, administrator, or anyone who can log on to the SAP S/4HANA Cloud, public edition, and must complete the relevant business tasks. This person needs access to data to fulfill their tasks but only to the data required for these specific tasks.
- A business role is a collection of access rights that can be assigned to business users.
- A business catalog is a set of applications that usually belong together semantically.

![[Pasted image 20251007105113.png]]

1. A business role is assigned to a business user to provide access to applications.
2. One or more business catalogs are assigned to the business role. Administrators control visibility to data by applying general restrictions to individual catalogs within the business role.
3. Catalogs contain apps, access to data, or access to configuration steps. Catalogs carry restriction types with different access categories (write, display, or value help) that can be maintained to control access within the apps and accesses within the catalog.

![[Pasted image 20251007105325.png]]