Objective

After completing this lesson, you will be able to set up the required provisioning entities.

## Identity Provisioning Service

The Identity Provisioning service ensures the synchronization of the entities between a source system and one or multiple target systems.

- _Source_ – а system where the company is currently managing the corporate identities.
- _Target_ – а system that must be populated with corporate users and other entities.

You can configure the required provisioning entities to ensure proper synchronization between source and target systems. You can also use proxy systems for indirect connections between a system supported by Identity Provisioning and an external application that uses a SCIM 2.0 API to consume identities from the proxy system. For example, you can use SAP Identity Management as an external consuming application.

Properties help you to customize the way your identities are read from a source system or provisioned to the target one. They can also filter which entities and attributes are to be read or skipped during the provisioning job.

For every system supported by the Identity Provisioning service, there is an initial (default) transformation logic that converts the system-specific JSON representation of the entities from/to one common JSON. You can keep the default transformation or modify the mapping rules to reflect the current setup of entities from your source or target system.

## How to Explore Schemas

This demo shows the building blocks used to structure the user repositories. A schema is used both by Identity Authentication and the Identity Provisioning services. It details the properties that an entity like a user should have. For a payroll-related system, the employee number is relevant, but not for systems where the agent is a customer or a supplier. Understanding schemas and their requirements are crucial so you can easily reuse an entity among many diverse systems. What is relevant for an LDAP repository or an Ariba user repository system will have some common properties and some specific properties.

Demo[  
](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_7FCCEA26B00CFEB4:demo)