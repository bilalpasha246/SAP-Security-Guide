## Overview

Based on a trace evaluation, it is easier to maintain the menu and the authorization data of a role, as well as authorization default values for applications.

You can use a system trace or an authorization trace to record authorization checks and their values. This function supports you when maintaining authorization default values (transactions SU22 and SU24) and when maintaining the menu and authorization data for roles (transaction PFCG).![[Pasted image 20251015133215.png]]
In the role maintenance screen (transaction PFCG), the trace evaluation can be used to maintain the role menu. To add applications (transactions, WEB-DYNPROS, and so on) to the role menu, you collect these applications in the system trace (transaction ST01 or STAUTHTRACE). During its runtime, the tracing uses the start authorization checks to log which applications were called. The administrator can then copy these applications to the role menu.

Call transaction PFCG for a role and go to change mode. On the _Menu_ tab, choose _Copy Menus_ → _Import from Trace_. The upper-left half of the dialog box that the system displays contains the _Information_ button. You can obtain all of the information about the use by selecting this button.
![[Pasted image 20251015133344.png]]
## Maintaining Authorization Fields Using Trace Evaluation

In Role Maintenance (transaction PFCG), trace evaluation can also be used to maintain the authorization fields. You can complete the authorization fields of a role with values that you collect in the authorization trace or the system trace. To do this, navigate to authorization data maintenance for a role. Expand the authorizations and choose the _Trace_ symbol at the authorization level. The system then displays a similar dialog box to that for menu maintenance and you can again choose _Information_ to obtain information about the usage.![[Pasted image 20251015133439.png]]
![[Pasted image 20251015133446.png]]
## Maintaining Authorization Default Values Using Trace Evaluation

You can also complete the authorization default values with values that you collect in the authorization trace or the system trace. Call transaction SU24 and display the authorization data for an application. Choose the _Trace_ function.
![[Pasted image 20251015133501.png]]
