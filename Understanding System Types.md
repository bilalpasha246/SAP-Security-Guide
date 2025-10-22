Objective

After completing this lesson, you will be able to recall and state the definitions of different system types.

## System Types

This section defines the three types of systems that you can use for provisioning identities: _source_, _target_, and _proxy_.

### Source Systems

A source system is the connector used for reading entities (users, groups, or roles). Source systems can be on-premise or cloud-based, SAP or non-SAP, and usually represent the corporate user store where identities are currently maintained. Identity Provisioning reads the entities from the source system and creates or updates them in the relevant target ones. The provisioning is triggered from the _Jobs_ tab of a source system.

You can connect one source system to one or multiple target systems.

### Target Systems

A target system is the connector used for writing (provisioning) entities. Target systems are usually clouds where Identity Provisioning creates or updates the entities taken from the source system.

A target system can be connected to a single or multiple source systems.

In the case of multiple source systems, we recommend that you run the provisioning jobs successively for each system, not simultaneously. By doing this, you will avoid incorrect overwriting or merging of entity data and, therefore, failed provisioning jobs.

### Proxy Systems

A proxy system is a special connector used for hybrid scenarios. It exposes any Identity Provisioning supported back-end system as a SCIM 2.0 service provider, which can be consumed by any SCIM 2.0 compatible client application, without making a direct connection between them.

To achieve this, the Identity Provisioning service uses this special proxy system to execute provisioning operations (create, update, delete, and so on) requested by the client application.

The examples in this section cover the use of SAP Identity Management as a consuming client application, but you can use any other SCIM-based identity management solution.

To provide communication between SAP Identity Management and the back-end system, the proxy application uses a SCIM 2.0 protocol. A system can act as a proxy if it supports both read and write operations.

### Proxy System - How It Works

1. The Identity Provisioning service exposes the back end of a supported system as a **proxy**.
2. An external application (for example, SAP Identity Management) regards the proxy system as its back-end system.
3. The entities (users) exposed by the back-end system are mapped to SCIM 2.0 entities if possible. If not possible, the SCIM standard provides a mechanism to define a new resource type with the appropriate schema. You can use the custom resource type to map the back-end entities.
4. Finally, the external application can start sending REST web service requests to the proxy system in order to read identities from the back end of the SCIM 2.0 system.

![The diagram shows how the identity provisioning service communicates with external consumer systems, such as SAP Identity Management, to supported systems in proxy mode. The systems connect via SCIM endpoint and proxy system connector.](https://learning.sap.com/service/media/topic/d342d4b1-1dd7-4b26-9008-8364c21e94ce/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Proxy_System_scr.png "The diagram shows how the identity provisioning service communicates with external consumer systems, such as SAP Identity Management, to supported systems in proxy mode. The systems connect via SCIM endpoint and proxy system connector.")

## Properties

You need to set mandatory properties to configure the connection between your source and target systems.

Properties help you to customize the way your identities are read from a source system or provisioned to the target one. They can also filter which entities and attributes are going to be read or skipped during the provisioning job. According to their usability, properties can be categorized in the following way:

- Standard
- Credential
- Default
- Parameterized
- Internal

## Property Types

Properties can help you filter which entities and entity attributes are read from the source system or written to the target system. According to their usability, properties can be categorized as follows:

- **Standard System Properties**
    
    Each source, target, and proxy system supports specific types of properties - for example:
    
    #### Examples
    
    |**AS ABAP System**|**SAP SuccessFactors**|
    |---|---|
    |jco.client.r3name=PSE|sf.page.size=100|
    |jco.destination.peak_limit=10|sf.user.filter=firstName John|
    |jco.destination.pool_capacity=5|sf.user.attributes=email|
    
- **Credential Properties**
    
    The values of these properties contain sensitive information that must not be displayed as plain text. The default credential property name is _Password_, which can represent standard passwords, private keys, or OAuth client secrets. When you add a credential property, its value is displayed as an encrypted string.
    
    #### Examples
    
    |**SAP HANA Database**|**SSH Server**|
    |---|---|
    |hana.jdbc.db.password=********************|ssh.password=********************|
    |hana.jdbc.ssh.tunnel.cf.password=********************|ssh.private.key=********************|
    |hana.jdbc.ssh.tunnel.private.key=********************|ssh.totp.secret.key=********************|
    

## Default System Properties

These properties depend on the particular connector type.

#### Examples

|**LDAP Server**|
|---|
|ldap.group.object.class=groupOfNames|
|ldap.user.object.class=inetOrgPerson|
|ldap.attribute.user.mobile=mobile|
|ldap.group.filter=<empty>|
|ldap.user.filter=<empty>|