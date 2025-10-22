![[Pasted image 20251007101205.png]]

1. Risk Analysis and Remediation–find and remediate segregation of duties and critical access violations
2. Access Request Management–automate access administration for enterprise applications
3. Business Role Management–define and maintain roles in business terms
4. Emergency Access Management–monitor emergency access and transaction usage
5. User and SoD Access Review–certify that access assignments are still warranted![[Pasted image 20251007101322.png]]

**Risk and control catalogs** allow for the central definition of risk and the documentation of mitigating controls that can be applied to specific users, user groups, security roles, and so on, to support compliance and audit-related activities.

The **risk analysis engine** is integrated with a workflow provisioning process and a role management process to allow customers to identify risk early before provisioning access to production environments.

The solution identifies and assesses potential access risks and violations and provides tools to remediate these risks through segregation of duties (SoD) analysis, critical access analysis, and remediation workflows.

Once the required rule set has been implemented, SAP Access Control provides real-time, ad-hoc risk analysis or offline batch risk analysis. Risk analysis can be performed at the user level, the role level, or using any number of reporting attributes, including, for example:

- User Group
- Risk by Process
- Access Risk ID
- Risk Level
- Rule Set
- User Type
- System
- Include Role Assignment
![[Pasted image 20251007101627.png]]

Using the standard **Risk Simulation** analysis, auditors can develop the appropriate **Remediation Strategy** by simulating changes to user access and/or role design to eliminate conflict. Simulation is possible at the user, role, and permission levels. If a suitable control has been defined in the Mitigating Control catalog, mitigation controls can be selected and applied during the risk analysis.

SAP Access Control also provides **Access Control Dashboards** to give management and internal auditors a graphical representation of the status of Risk and Remediation activities across each connected system. These dashboards are updated regularly using a series of periodic batch jobs, including batch risk analysis.

Approval procedures and approval workflow are easily created and customizable using a flexible multistage, multipath workflow (MSMP). MSMP workflow provides the backbone for creating, submitting, and approving access requests. Workflow capabilities are also integrated across all functions of access control and can be used to support:

- Risk Maintenance
- Function Maintenance
- Mitigation Maintenance
- Access Request
- Role Maintenance
- User and Compliance Certification

![[Pasted image 20251007103002.png]]

Business Role Management provides the framework to define a standard role creation and role maintenance methodology. The role methodology is customizable and provides a standard, auditable process enforced to ensure compliance with company requirements. Business Role Management delivers a best practice template methodology that includes:

- Define Role
- Maintain Authorizations
- Analyze Access Risk
- Request Approval
- Generate Roles
- Maintain Test Cases and Results![[Pasted image 20251007104030.png]]

SAP Access Control provides several functions that support access certification and review:

- **User Access Review:** User Access Review (UAR) is a workflow-driven process using a standard MSMP workflow. Through this process, a user's access can be reviewed at the Manager or Role Owner level to determine if it is still appropriate. At the end of the review process, continued access is either approved or removed and documented and deprovisioned.
- **SOD Review:** SOD Review is a workflow-driven process using a standard MSMP workflow as well. Through this process, Managers or Risk Owners review users’ access to segregation of duty or critical action risks and determine whether continued access is still required. Continued access is either approved or removal of access is documented. Access can be deprovisioned at the end of the review process.
- **Role Reaffirm:** Role Reaffirm is similar to the UAR process previously outlined but is not workflow-driven. Business Role Management maintains a role reaffirm date as part of the role definition. When that date arrives, a notification can be sent to the respective role owner, who uses Business Role Management to document their approval or propose removing the specific role.
- **Role Certification:** Role Certification is a process whereby a role definition is reviewed periodically to determine if it is still correctly designed, contains proper access and permissions, and still needs production. It is not a workflow-driven process. Like Role Reaffirm, Business Role Management maintains a role certification date as part of the role definition. When that date arrives, a notification can be sent to the role content approver, who uses Business Role Management to certify the role contents.

**Emergency Access Management** (EAM) is a standard SAP GRC Access Control function. EAM provides a controlled framework for defining, managing, granting, and monitoring emergency system access. Through EAM, firefighters can be granted extra system security and temporary access to a superuser or firefighter ID. These special super users are controlled by a firefighter owner and monitored by a firefighter controller. The firefighter owner is charged with approving access to specific IDs, a process that a standard workflow approval procedure can drive.

Once provided access to the firefighter ID, the firefighter can "check out" the ID, which opens a session in the target environment where the firefighter can perform the actions required with the extra security access. The Emergency Access Management tool creates a detailed log of the actions performed using each firefighter ID. It sends that log to the firefighter controller, who monitors and reviews the logs and activities performed by the firefighter.![[Pasted image 20251007104358.png]]

The **Alert Monitoring** functionality collects data on user access and generates alerts when conflicting or critical access is executed. Alerts can also be generated if mitigating control activities are not performed within a specified timeframe. Integration with SAP GRC Process Control can greatly enhance mitigation control management.

![[Pasted image 20251007104506.png]]