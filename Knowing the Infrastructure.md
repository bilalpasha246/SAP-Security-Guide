## Use Cases

Identity Provisioning supports the following use cases:

- **Provisioning from Source to Target Systems:**
    
    The main use case of Identity Provisioning is to read users and groups from a source system and provision them to a target system. Filtering and/or mapping are applied during job execution.
    
- **Hybrid Integration with Identity Management Systems:**
    
    Identity Provisioning can be used for integrating cloud solutions with on-premise or cloud identity management systems that support the SCIM 2.0 standard, such as SAP Identity Management and SAP Cloud Identity Access Governance.
    
    In a hybrid integration scenario, Identity Provisioning acts as a proxy between a cloud solution and an on-premise or cloud system. This means that the Identity Provisioning is used for configuring and exposing the cloud solution as a proxy system and connecting it to the external identity management system without making a direct connection between them.
    
- **Real-Time Provisioning from Identity Authentication:**
    
    Identity Provisioning can be used for immediate, real-time provisioning of Identity Authentication users to any target system. Unlike the standard provisioning, where reading and writing of users is triggered by jobs, real-time provisioning is triggered by events (such as user self-registration or user modification in Identity Authentication).
    
- **Storing Users and Groups in Local Identity Directory:**
    
    Identity Provisioning is mainly used for provisioning users and groups. However, it can also be used for storing users and groups when a specific type of system, Local Identity Directory, is configured. In a typical use case, the Local Identity Directory is first configured as a target system, where users and groups are provisioned to, and then configured as a source system, from where users and groups are read and provisioned to target systems.
    
    The identity directory provides a system for Cross-domain Identity Management (SCIM) 2.0 REST API for managing resources (users, groups, and custom schemas).
    

## Key Points on the Features

### Prerequisites

To use Identity Provisioning, you must obtain a tenant.

### Tools

You can access the Identity Provisioning administration console as an HTML5 application.

### Regional Availability

You can access Identity Provisioning tenants on the infrastructure of the SAP BTP.

### Tenant Model

SAP Cloud Identity Services – Identity Provisioning functionality can be added to the Identity Authentication Service tenant.

### Bundle Tenant

A bundle tenant is an instance of Identity Provisioning that comes with a set of preconfigured provisioning systems relevant to one or more bundled SAP Cloud solutions.

Caution

**Effective March 15, 2022, new Identity Provisioning bundle tenants are created on the infrastructure of SAP Cloud Identity Services only.**

### Standalone Tenant

A standalone tenant allows you to use Identity Provisioning as a separate (standalone) product.

Caution

**Effective October 20, 2020, Identity Provisioning is offered bundled with SAP Cloud solutions.** You can obtain and use it, along with Identity Authentication, as part of a bundled SAP Cloud solution that you must purchase. The service is no longer sold as a standalone product. Existing customers of standalone Identity Provisioning can use it as is until the end of their contracts.

The scope of the standalone tenant is not restricted. It can be used for provisioning of users and groups to and from all supported systems by the Identity Provisioning service.

Depending on the infrastructure or the environment your standalone tenant runs on, you can access and operate it.