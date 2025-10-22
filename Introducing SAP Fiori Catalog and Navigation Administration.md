The SAP Front-End Server is an SAP NetWeaver ABAP Stack like any SAP ERP or SAP S/4HANA Backend Server. It comes with no business add-on installed. The recommended SAP Fiori system landscape splits the UI from the business logic on the SAP Backend Server.![[Pasted image 20251007094847.png]]

In the On-Premise edition, when considering applications’ usage, architecture, and configuration, there are three types of SAP S/S4HANA applications:

1. **Legacy apps** are Web Dynpro and GUI for HTML Applications. They are not mobile-enabled but provide an SAP Fiori look and feel. Depending on their use case, these apps have different subtypes.
2. **SAP Fiori Search** is part of the SAP Fiori Launchpad and provides contextual search.
3. **SAP Fiori SAPU15 apps** such as Transactional Apps, Analytical Apps, and Object Pages also have their user interface deployed on the Front-End Server. It is not part of the central UI software component but needs specific product UI add-ons. Multiple apps for the same user group/industry are bundled into one product UI add-on (for example, HCM). All SAP Fiori apps and the SAP Fiori Launchpad use OData as the protocol for data transfer. The SAP Fiori Launchpad has several OData services that are called to run the SAP Fiori Launchpad and provide data such as groups, tiles, and personalization. OData service provisioning is done by the SAP Gateway Foundation (SAP_GWFND).

![[Pasted image 20251007095021.png]]

As discussed in the previous unit, standard SAP GUI transactions are called using either a role menu or directly via the transaction code window on the standard GUI screen. The transaction code is mapped directly to the corresponding program using transaction SE93 on the Backend Server.
![[Pasted image 20251007095233.png]]

The PFCG role contains the program's start authorization and required data access authorizations. Transaction SU24 maps the backend data access authorizations to the transaction code included in the role menu.

With SAP Fiori apps, access to the Back-End Server data occurs similarly. Fiori Catalogs and Fiori Spaces or Groups determine access to the SAP Fiori Launchpad and specific Fiori Tiles. In the SAP Fiori Launchpad, the tiles available to a user are displayed in a Space or Group. These Spaces or Groups are maintained on the Front-End Server. The tile definition and the specific target mappings that point to implementing each SAP Fiori app contain the Fiori catalog.

![[Pasted image 20251007095336.png]]

For a user to access a specific Fiori app, the user must have a PFCG role on the Front-End Server, which contains both:
- A Fiori Space or Group assignment containing the specific tiles assigned to the user.
- A Fiori Catalog assignment containing the specific tiles in the assigned Fiori Space/Page or Group.

In other words, the user needs the Front-End Space and Catalog assignments for the start authorizations and visibility of the tiles in the SAP Fiori Launchpad. Authorization is also required on the Backend Server to access the specific objects and data the Fiori app calls.

![[Pasted image 20251007095501.png]]

The SAP Fiori launchpad content manager lets you make system-wide or client-specific changes. System-wide changes are stored in the configuration scope, and client-specific modifications are stored in the customizing scope.

Depending on the scope of your changes, use the SAP Fiori app in the launchpad or one of the following transactions in SAP GUI:

- The client-specific customizing layer is addressed via the transaction **/UI2/FLPCM_CUST**.
- The configuration layer is addressed via the transaction **/UI2/FLPCM_CONF** and is cross-client.

SAP delivers predefined catalogs. The technical catalog, marked with the ID *_TC_" prefix, defines the tile and target mapping. SAP also provides samples and ready-to-use business catalogs as recommendations, marked with the ID *_BC_* prefix.

On-Premise and Private Cloud customers can define their catalogs by copying the tiles and target mappings from one of the SAP catalogs.