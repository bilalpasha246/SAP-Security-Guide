## SAP Fiori Launchpad Deployment Options

#### Overview

Besides the embedded SAP FES deployment and the SAP FES as a central hub, there are several deployment options available for SAP Fiori. This lesson provides an overview of the different SAP Fiori deployment options for SAP S/4HANA and SAP Business Suite systems and the recommended system landscape setup.

Furthermore, SAP is strategically evolving the **SAP Business Technology Platform (SAP BTP)** as an integration and extension platform and enhancing the capabilities to establish a central point of access. Organizations can implement an SAP Fiori launchpad in the cloud using the dedicated **SAP Launchpad service**, which acts as common UX integrator for SAP and non-SAP solutions (both on-premise and in the cloud). SAP Launchpad service enables customers building a common user experience on top of multiple SAP S/4HANA systems.

### SAP Fiori for SAP S/4HANA -Deployment Options

Based on the technical deployment options, the following figure shows the deployment options when focusing on an SAP S/4HANA implementation.

![Illustration showing the deployment options for SAP Fiori for SAP S/4HANA.](https://learning.sap.com/service/media/topic/ea2986a1-85c8-4201-a4fe-349f425b6643/ADM945_24_en-US_media/ADM945_24_en-US_images/SAP_Fiori_for_SAP_S4HANA_Deployment_Options.png "Illustration showing the deployment options for SAP Fiori for SAP S/4HANA.")

SAP S/4HANA Cloud is a cloud-based, integrated ERP solution (Software-as-a-Service), which comes with build-in SAP Fiori experience and launchpad.

When implementing SAP S/4HANA (on-premise) you have two options to adopt SAP Fiori experience. The recommended setup for SAP Fiori is the embedded SAP Fiori front-end server. To simplify the activation of SAP Fiori for S/4HANA you can leverage task lists to automate the setup of SAP Fiori launchpad, Fiori Apps and business roles, and so on.

Alternatively, an SAP S/4HANA system with a dedicated standalone SAP Fiori front-end server (for each SAP S/4HANA system) might be an option for certain use cases.

### SAP Fiori Deployment – OData Provider Options

The following figure shows the different options for consuming back-end data within SAP Fiori apps.

![Illustration showing the OData provider options for SAP Fiori Deployment.](https://learning.sap.com/service/media/topic/ea2986a1-85c8-4201-a4fe-349f425b6643/ADM945_24_en-US_media/ADM945_24_en-US_images/SAPFioriLaunchpadDeploymentOptions.png "Illustration showing the OData provider options for SAP Fiori Deployment.")

When SAP Fiori apps are deployed on-premise, the UI components are installed on the SAP Fiori front-end server (hub or embedded deployment). To access business data from the back-end, OData service calls are handled by the SAP Gateway component on the SAP Front-end server, which calls the OData service implementation in the back-end system leveraging the Gateway back-end components.

To retrieve the necessary data for your SAP Fiori applications from the back-end, you have different options:

- SAP Gateway – embedded or hub/standalone server
- OData provisioning service on SAP BTP

When deploying SAP Fiori apps on SAP BTP, the SAP Fiori UI components are installed on the platform while connecting to the respective back-end system via the Cloud Connector. The OData request is then handled by SAP Gateway in the same way as for the on-premise setup. The can be also handled by the OData provisioning service.

For SAP Business Suite back-end systems, you may use OData Provisioning service on SAP BTP as an alternative data access method. This lightweight service manages the OData communication.

SAP Integration Suite is the recommended option to connect any kind of data sources if not all data sources are based on OData.