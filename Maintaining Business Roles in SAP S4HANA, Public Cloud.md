You can use the **SAP Fiori Apps Reference Library** provided by SAP to understand what apps are available and which delivered business roles and business catalogs reference specific apps.
![[Pasted image 20251007110742.png]]
The SAP Fiori Apps Reference Library is a comprehensive online repository that contains detailed information about every SAP Fiori app available by SAP product and version. It is designed to aid users, developers, and administrators by providing complete documentation of each app, including how to use and configure it, technical details and prerequisites for each app's use and deployment, and so on.

You can use the library to:

- Get key information for each app
- Find configuration information required to integrate apps into the SAP Fiori launchpad
- Review changes and updates from previous app versions
- Use installation and configuration information for specific apps
- Link together key SAP resources and documentation.

![[Pasted image 20251007110818.png]]

![[Pasted image 20251007110937.png]]

For the SAP S/4HANA Cloud, public edition, production system, SAP recommends that customers create custom business roles based on the specific applications and requirements defined for their implementation. For this purpose, SAP delivered the **Maintain Business Roles** app.

Typically, to define a business role from scratch using the Maintain Business Roles app, you perform the following steps:
1. Maintain General Role Details
2. Assign Business Catalogs
3. Maintain Restrictions
4. Assign Launchpad Spaces and Pages

The definition of a business role contains basic details about the business role. You can use the Maintain Business Roles app to define the following General Role Details when creating your role:

- **Business Role ID:** The business role ID can be created in the customer namespace and contain the letters BR to denote that it is a business role. Do not begin your business role IDs with BR because this namespace belongs to SAP.
- **Business Role Description:** The business role description can contain an easy-to-understand description describing the purpose of the business role and its function(s).
- **Business Role Long Text:** You can use the long text field to provide a more detailed description or explanation of the business role, including its applications, any dependencies with other roles, and so on. Also, documentation concerning changes and updates to the business role can be documented here to chronicle its evolution.
- **Business Role Group:** Business role groups are defined using the Business Role Groups app. You can assign business role groups to help you organize by area and easily search for all business roles of a specific category (for example, assign business users to them). Grouping also facilitates the maintenance of authorizations. If you are the super administrator for all areas, you can delegate maintenance tasks to administrators for their relevant areas, such as Financials. In this case, you create a business role group for Financials.
- **Access Categories:** Access categories represent the default access categories for the business role. Restrictions can be used to refine and restrict access.
- **Business Role Template ID:** If the business role was created using one of the business role templates delivered by SAP, the ID is linked to the business role definition for maintenance and reporting purposes.
- **Leading Business Role ID:** The Leading Business Role ID field denotes whether a business role has been derived from another business role. Derived business roles can simplify creation and maintenance in scenarios where multiple business roles must be created with the same standard access. The leading business role contains the basic settings, such as access restrictions, the assigned business catalogs, and common restrictions, such as the General Accountant or Plant Manager. The values defined in the leading business role can't be changed in the derived business role. You can, however, define extra values for the derived business role.
- **Is Leading Business Role:** The Is Leading Business Role checkbox designates the business role as the leading or parent business role. More roles can be derived from a leading business role.