Objective

After completing this lesson, you will be able to understand Authorization Concepts for ABAP CDS.

## Virtual Data Model Based on CDS Views

#### Development Paradigm Shift

Moving calculations to the database to benefit from its features is not new to SAP HANA. Stored procedures could be used previously for calculations in many databases. However, they were rarely used in ABAP. They only run in the database they are developed in and are not transportable. With SAP S/4HANA, the ABAP Repository was extended with two new database objects: ABAP Core Data Services (CDS) Views and ABAP Managed Database Procedures (AMDP). CDS Views are deployed as SAP HANA views in the SAP HANA Database (HDB), and the AMDPs are deployed as stored procedures. This is comparable to deploying a transparent table of the ABAP repository as a database table in any DB.

On one hand, ABAP CDS Views are classic database views that are compatible with any DB. On the other hand, they include side elements such as annotations, which can only be interpreted by a HANA database. Although CDS Views are stored in the ABAP repository.

## Declarative Authorizations - Classic Authority Checks

### Classic Authority Checks

Authorization checks in programs are performed using the ABAP command AUTHORITY-CHECK which depends upon the PFCG role assigned to the user.

A program may contain any number of authorization checks.

![Illustration on Access Control Classic Approach.](https://learning.sap.com/service/media/topic/eaff8190-9cc8-4036-ba70-cef481b9d92c/ADM945_24_en-US_media/ADM945_24_en-US_images/AccessContolClassicApproach.png "Illustration on Access Control Classic Approach.")

![Illustration on Classic Authority Checks.](https://learning.sap.com/service/media/topic/eaff8190-9cc8-4036-ba70-cef481b9d92c/ADM945_24_en-US_media/ADM945_24_en-US_images/Classic%20Authority%20Checks.png "Illustration on Classic Authority Checks.")

## Basics of Core Data Services (CDS) from a Developers Point of View

#### Definition

Many technologies exist that introduce higher-level models on top of SQL to add semantics and ease consumption – for example, OData EDM models, the Semantic Layer in the BI platform, JPA and enterprise objects in Java, and the business objects frameworks in ABAP. Those higher-level models share many commonalities, but are usually specific to their technology. This prevents their re-use across stacks and increases effort for application developers.

To address this, SAP HANA introduced a set of domain-specific languages (DSL) and services called Core Data Services for defining and consuming semantically-rich data models.

![Illustration on CDS - A Family of Domain Specific Languages.](https://learning.sap.com/service/media/topic/d16d8304-4999-4a06-a9ed-90f9a5bb8181/ADM945_24_en-US_media/ADM945_24_en-US_images/CDS%20%20A%20Family%20of%20Domain%20Specific%20Languages.png "Illustration on CDS - A Family of Domain Specific Languages.")

Core Data Services (CDS)

CDS introduce a common set of domain-specific languages (DSL) and services for defining and consuming semantically rich data models.

Data Definition Language (DDL)

DL is used for defining semantically rich database tables/views (CDS entities) and user-defined types in the database.

Data Control Language (DCL)

DCL is used to define authorizations for CDS entities. The main goal of CDS is to make the usage of SQL easier for application developers. DCL offers a possibility to define the authorizations needed for the CDS entities in a modeled, declarative way.

For more information, see the ABAP Authorization Concept for CDS Entities topic at [http://help.sap.com](http://help.sap.com/).

The developer can either define sophisticated new views or simply wrap an existing table in a CDS view in order to enrich it semantically. For example, ABAP CDS offers a new authorization concept based on roles defined with DEFINE ROLE in a DCL (Data Control Language) source code. In order to let an existing table participate in the new authorization concept, the developer can simply create a CDS view for that table that is connected to a role.

### CDS-Related Repository Objects

![Illustration on CDS-Related Repository Objects.](https://learning.sap.com/service/media/topic/d16d8304-4999-4a06-a9ed-90f9a5bb8181/ADM945_24_en-US_media/ADM945_24_en-US_images/CDS-related_Repo_Obj_001.png "Illustration on CDS-Related Repository Objects.")

### CDS View

![Example of the CDS View.](https://learning.sap.com/service/media/topic/d16d8304-4999-4a06-a9ed-90f9a5bb8181/ADM945_24_en-US_media/ADM945_24_en-US_images/DDL_Source__SQL_View_and_CDS_View_002.png "Example of the CDS View.")

As with conventional database views, the simplest form of a CDS view is a projection – that is, a selection of fields from a single table.

The language used is SQL Data Definition Language (DDL), but in an Open SQL form so that the view can be deployed on any database platform.

The name of the CDS entity is specified after the DEFINE VIEW statement. It is recommended, though not technically necessary, that the name of the DDL source and the name of the CDS view are identical.

### CDS Role

CDS Access Control defines a CDS role. It relates the CDS role to one (or more) CDS views (keyword GRANT SELECT ON …) and defines access conditions for this CDS view (keyword WHERE …). Whenever an ABAP program accesses this CDS view, the database interface will automatically filter the selection result according to the access conditions.

![Example of the CDS Role.](https://learning.sap.com/service/media/topic/d16d8304-4999-4a06-a9ed-90f9a5bb8181/ADM945_24_en-US_media/ADM945_24_en-US_images/Access_Control_002.png "Example of the CDS Role.")

The example shows an access control for flight bookings.

The access control automatically removes bookings for which the user does not have sufficient authorization.

### Access Control - How it works

![Illustration showing how Access Control works.](https://learning.sap.com/service/media/topic/d16d8304-4999-4a06-a9ed-90f9a5bb8181/ADM945_24_en-US_media/ADM945_24_en-US_images/Access_Control_001.png "Illustration showing how Access Control works.")

ABAP CDS enables access control based on a data control language (DCL). Access control in ABAP CDS further restricts the data returned from a CDS entity in ABAP CDS. CDS access control is based on the following:

- CDS roles defined using the DCL statement DEFINE ROLE. Currently, a CDS role is mapped to each user implicitly. This is why they are also known as mapping roles.
- Access conditions defined in a CDS role CDS entities. Access conditions can be the following:
    - Literal conditions that compare elements of a CDS entity with literal values.
    - PFCG conditions that associate elements of a CDS entity with authorizations in the SAP authorization concept.

## Declarative DCL Authorizations

#### Overview

ABAP Core Data Services (CDS) has its own authorization concept based on a data control language (DCL). The authorization concept of ABAP CDS uses the underlying data model to check the authorizations of users.

The CDS authorization concept coexists with the classical authorization concept of SAP NetWeaver Application Server for ABAP (SAP NetWeaver AS for ABAP). You can use the concepts together or independently from another. The classical authorization concept is based on authorization objects. The authorization of a user occurs either implicitly, for example while calling a transaction, or explicitly with the statement AUTHORITY-CHECK. The CDS authorization concept is based on implicit authorization checks that occur during access attempts to CDS entities over service adaptation definition language (SADL).

### Modeled Authorizations based on CDS Views

The CDS authorization concept is based on implicit authorization checks that occur during access attempts to CDS entities over Open SQL.

It is advisable to continue to use classic authorization checks for start authorizations (used to check whether a user can start an application in the first place). CDS access control can be used within an application to perform instance-based authorization checks (used to check the authorization of a user as defined by the data model and the data in question).

The authorization concept of ABAP CDS uses the underlying data model to check the authorizations of users. Data Control Language(DCL) is used to define the authorization for the ABAP CDS view which controls access to the data retrieved based on user.

### Declarative DCL Authorizations

A developer defines a CDS role in a separate CDS source code for a CDS entity using the DCL statement **DEFINE ROLE**. When a CDS entity is accessed using Open SQL, the following is checked:

1. Is a CDS role defined for the CDS entity?
    
    If no role is defined for a CDS entity, no restrictions apply to the data returned by the query.
    
2. Does the current user have the required permissions?
    
    If a CDS role is defined for a CDS entity, the access control management checks the current user for permissions, which are defined by PFCG roles and reads only the data for which permissions exist. CDS roles are implicitly assigned to all users.
    

![Illustration on Access Control DCL Approach.](https://learning.sap.com/service/media/topic/dd6e1064-c006-4f6e-ba73-4dd27fec122e/ADM945_24_en-US_media/ADM945_24_en-US_images/AccessContolDCLApproach.png "Illustration on Access Control DCL Approach.")

![Illustration on usage of Declarative DCL Authorizations.](https://learning.sap.com/service/media/topic/dd6e1064-c006-4f6e-ba73-4dd27fec122e/ADM945_24_en-US_media/ADM945_24_en-US_images/Usage%20of%20Declarative%20DCL%20Authorizations%20.png "Illustration on usage of Declarative DCL Authorizations.")