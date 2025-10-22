Objective

After completing this lesson, you will be able to administer systems and execute provisioning jobs.

## Adding a System

### Overview

In this unit, you will learn - as an administrator - how you can set up the Identity Provisioning service so that entities from a source system are easily transferred to a target system.

Before triggering provisioning, make sure that you have performed the required setup.

You can perform the following operations:

- Add source, target, and proxy systems
- Set up configuration properties specific for your systems and scenarios
- Define mapping rules between the data models of sources and targets
- Provision entities between systems
- Run and schedule provisioning jobs
- View job logs
- Export and import systems

### Add a System

You can add source, target, and proxy systems in the Cloud Identity Services.

## How to Configure Source Systems

This demonstration shows how to configure source systems. When you define a source system, you detail what kind of system it is and you receive an initial template where you can adjust how entities (users and groups) should be read and, if needed, filtered, or adapted. One simple example, which is now more than two decades old, is between ABAP-based systems. A user like DDIC or SAP is very important in the context of an ABAP system, but there is no point in creating it as a user for Active Directory.

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_990342712B00B1:demo)

## How to Explore Target Systems

This demonstration shows how to manage target systems. At first glance, the definition of a target system is very similar to a source system, but some additional details appear, for example, the possibility of a target system receiving entities from multiple source systems and also the need to enrich entities' properties with missing details. For example, imagine that the target system requires a detail like the user organization. The source application might not provide it, but if it's mandatory in the target system, you must, at least, place a default that later might be adjusted in the target application. When connecting and sharing the user-relevant data across many diverse systems, you might need to also adjust the corresponding schemas.

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_B7029BB32608CEA2:demo)

## How to Explore Proxy Systems

This demonstration shows how to manage proxy systems. Proxy systems combine the characteristics of source and target systems. They read from a source system, provide a repository where entities can be stored in their own schema, and from where they can be sent to other target systems. While defining a proxy system, two transformations are generated, one for reading and the other one for writing, and both can be adjusted to address specific needs. Like in other transformations, the editor can be presented with a graphical interface or with a JSON coding interface.

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_5F1C740A672E96BD:demo)

## How to Explore Administration Options

This demonstration shows how to use different administration options available in the Cloud Identity Services UI. Here you can find how to easily jump to the documentation available at help.sap.com or trigger a support request. Depending on the application lifecycle management procedures in your project, you can clean the content of an existing tenant, but if it's a productive or otherwise sensitive environment, make sure just the provisioning logs relevant for compliance initiatives are safely stored.

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_1C5A9F7012A5829D:demo)

## On-Premise Systems in SAP Cloud Identity Infrastructure

Set up the connection to on-premise systems, such as SAP AS ABAP, LDAP Server, Microsoft Active Directory, SAP S/4HANA On-Premise, when your Identity Provisioning bundle or standalone tenant is running on the SAP Cloud Identity Services infrastructure or SAP BTP.

### Connecting to On-Premise Systems in SAP Cloud Identity Infrastructure

Set up the connection to on-premise systems when your Identity Provisioning bundle or standalone tenant is running on the infrastructure of SAP Cloud Identity Services.

#### Prerequisites

1. Ensure your tenant is running on SAP Cloud Identity Services infrastructure.
2. You have installed the Cloud Connector (for SAP BTP, Cloud Foundry environment) and have done the initial configuration.

#### Context

If your provisioning scenarios involve on-premise systems, this requires a separate configuration in three places:

1. SAP BTP cockpit, where you subscribe to the Cloud Identity Services connectivity plan in your Cloud Foundry subaccount
2. SAP Cloud Connector, where the connection to your Cloud subaccount is established, and the back-end (on-premise) system is defined
3. Identity Provisioning administration console, where you configure the on-premise provisioning systems

## Full and Delta Load

When you set up your systems and start a scheduled provisioning task, the standard behavior of the process reads all the entities from the source system. This mode prevents data loss and always keeps your target system synchronized with the source. However, it can take a long time for every job to be executed.

Delta read is a concept for optimizing the amount of data retrieved from the source system. Delta read is much faster, but sometimes might have limitations. For a source system to support delta read mode, its API should allow the implementation of this feature.

For example, the _Microsoft Active Directory_ source system uses the _uSNChanged_ attribute.

The main difference between delta and full read is as follows:

- _Delta read_ – only modified data is read from the source system and triggered to the target one. Modified data means new entities and updates on existing entities. Entities deleted from the source system will not be deleted from the target. They can be deleted only during a _full read_ job.
- _Full read_ – all entities (new, updated, deleted, and existing unchanged ones) are read and checked every time a provisioning job is triggered to the target system.

To keep source and target systems completely synchronized, you can use the **Resync** type of provisioning job.

Note

We recommend that you enforce full reads from time to time if the connector is in delta read mode. To achieve this, you must set up the following source system property: ips.full.read.force.count. For example, ips.full.read.force.count = **10** will result in alternating full reads after every 10 delta reads are performed.

This property only impacts scheduled runs; manually triggered runs are ignored. In case it is not set, only delta read jobs will be executed.

When the Identity Provisioning reads entities from a source system for the first time, it always triggers a **full read** job. If the job is successful, the service can then continue with delta read jobs (if such are activated). During a delta read job, the service reads only the entities that are new or have been modified after the last successful job.

The following table lists all source systems that currently support _delta read_ mode.

### Supported Systems

#### Supported Systems

|**System Type**|**Details**|
|---|---|
|**SAP SuccessFactors**|Default mode: **Delta read**<br><br>You can switch to full read if you set up the relevant property: ips.delta.read = **disabled**|
|**SAP SuccessFactors Learning**|Default mode: **Delta read**<br><br>You can switch to full read if you set up the relevant property: ips.delta.read = **disabled**|

#### LDAP-based Systems

|**System Type**|**Details**|
|---|---|
|**Microsoft Active Directory**|Default mode: **Full read**<br><br>You can switch to delta read if you set up the relevant property: ips.delta.read = **enabled**<br><br>Keep the following specifics and limitations in mind as you proceed:<br><br>- In order to have a notion for any deleted objects in delta read mode, the _Active Directory Recycle Bin_ optional feature must be enabled.<br>- Make sure that the service user, which is used in the AD destination, has a **Domain Admin** role, otherwise the connector won't be able to extract any data from the recycle bin.<br>- Due to the _linked attributes_ concept of AD, there is a limitation in the Microsoft Active Directory read connector when performing in delta read mode. We recommend that you enforce full reads periodically in order to avoid data loss.<br>- You need to set limitations about which particular attributes are read. For this purpose, set the properties ldap.user.attributes and ldap.group.attributes and add uSNChanged to the attributes list. Otherwise, the provisioning job will run in full read mode.|

#### SCIM-based Systems

|**System Type**|**Details**|
|---|---|
|**Identity Authentication**|Default mode: **Full read**<br><br>You can switch to delta read if you set up the relevant property: ips.delta.read = **enabled**<br><br>Note<br><br>When using SAP Central Business Configuration and Identity Directory SCIM API (in short, SCIM API version 2), delta read mode is only supported for user resources.<br><br>For delta read of resources (users and groups), remember the following API requirements:<br><br>- The system API should return **lastModified**, which is a subattribute of the **meta** attribute. The **lastModified** subattribute denotes the most recent date and time when the resource details were updated at the service provider.<br>- The system API has to also support filtering by the **lastModified** attribute, and the system should support the **gt** operator in filter expressions.|
|**Local Identity Directory**|
|**SAP Central Business Configuration**|
|**SAP CPQ**|
|#### SCIM System<br><br>(General SCIM system, if it fulfills the API requirements)|

## How to Explore Real-Time Provisioning

This demonstration shows how to access the real-time provisioning configuration screens. Besides the schedule transfer of entities across different systems, like users and groups, you might need to immediately make a new user or group available. Here, you find where to define a system candidate for real-time provisioning and explore some of the available options for authentication into the recipient (target) system where the new entities will be created, from basic authentication to certificates, even if OAuth is now a widespread method.

Demo[Start Demo](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_FA24A4395EC289AB:demo)

## Provisioning Job - Start and Stop

You can start and stop a provisioning job from the Identity Provisioning administration console or from an API client by using the Identity Provisioning tenant admin API.

#### Prerequisites

- Your source and target systems are configured and enabled.
- (Optional) You have run a **Simulate** and/or a **Validate** job before you run the actual provisioning job to verify that Identity Provisioning configurations produce the desired result in the target systems.

### Job Types

The Identity Provisioning service provides the following types of provisioning jobs:

#### Types of Provisioning Jobs

|**Run From**|**Job Type**|**Real Provisioning**|
|---|---|---|
|Admin console|**Read Job** - Reads all entities from the source system and provisions only new or updated entities to the target system. If the job is run in **delta read** mode, it reads and provisions only new or updated entities in the source system.|Yes|
|**Resync Job** - Reads all entities from the source system and provisions all entities to the target system.|
|**Simulate Job** - Estimates the number of entities that will be created, updated, deleted, or skipped in the target system. Provides the expected results of a resync job without modifying the target system.|No|
|**Validate Job** - Verifies how entities (users and groups) would be mapped from source to target systems without modifying them.|
|API client|Use the Identity Provisioning tenant admin API to run a provisioning job from an API client. The API is available on the SAP Business Accelerator Hub.|Yes|

### Start a Job

To run a job, select a source system and choose _Jobs  <Job_Type>_ and _Run Now_.

### Schedule a Job

To schedule a job run, select a source system and choose _Jobs_→_Read Job_→_Schedule_.

### Stop a Job

To stop a running job, select a source system and choose the _Stop Job_ button in the _Action_ column.