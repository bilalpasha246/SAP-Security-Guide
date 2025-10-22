To identify potential needs beyond this baseline security level for specific systems, an assessment must be conducted on which systems require an additional explicit risk analysis, for example, because they are of a particular criticality or nature. For such systems, a further risk analysis must be conducted, and corresponding countermeasures to the identified risks must be individually developed and applied.

An SAP Security Baseline is typically derived from several sources:

- Recommendations from SAP, for example, from SAP security services like the [security chapter of the EarlyWatch Alert](https://help.sap.com/docs/SUPPORT_CONTENT/sm/3518047086.html) (or note [863362](https://me.sap.com/notes/863362)) or the [SAP Security Optimization Service](https://support.sap.com/en/offerings-programs/support-services/security-optimization-services-portfolio.html).
- Documentation from SAP, for example, the product-specific Security Guides on the [SAP Help Portal](https://help.sap.com/docs/), [Security Whitepapers](https://support.sap.com/en/security-whitepapers.html), or [Security Notes](https://support.sap.com/en/my-support/knowledge-base/security-notes-news.html).
- Organization-specific guiding documents, like an overall Security Policy or an IT Security Policy, must be respected.
- More requirements or deviations are explicitly decided by Security Consultants/Auditors.

![[Pasted image 20251008103524.png]]

The overview of the typical approach is as follows:

1. SAP security services, for example, the security chapter of the EarlyWatch Alert or the SAP Security Optimization Service, help compare exemplary systems against SAP recommendations and derive corresponding general requirements for all SAP systems.
2. SAP system-specific input and requirements are derived from internal governing or guiding sources, such as general security policies or specific decisions on certain topics.
3. A company-specific SAP Security Baseline is built based on the input from internal sources and SAP.
4. The regulations in this SAP Security Baseline can then be transformed into a technical representation of the to-be status for SAP systems. So-called "Target Systems" cover this in the SAP Solution Manager's application configuration validation.
5. In operations, the SAP systems can continuously be monitored for compliance with the SAP Security Baseline, for example, by using the application Configuration Validation. This allows for a cross-system overview of selected technical aspects, like the security configuration or critical authorizations. These results can be evaluated within Configuration Validation and used in SAP Solution Manager-based dashboards, Monitoring and Alerting Infrastructure in Solution Manager, and risk management tools like SAP GRC Process Control.

SAP is committed to delivering trustworthy products and cloud services. Secure configuration is essential to ensuring safe operations and data integrity. Therefore, SAP has documented recommendations to help configure the best security for their SAP portfolio.

The following security recommendation guides for SAP products and cloud services enhance with further products.
