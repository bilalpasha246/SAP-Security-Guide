## Error Analysis for Authorization Problems

If you cannot find documentation about authorization for a transaction, or if a _failed authorization check_ is always reported when you execute a transaction, there are two ways in which you can determine the required authorizations:

1. With the authorization error analysis and transaction code SU53.
    
2. With the system trace for authorization checks STAUTHTRACE.
    

## Analyzing Authorization Checks
![[Pasted image 20251015124407.png]]
In the next example, a transaction from the _FI_ area was executed and terminated due to a missing authorization. The system message is: **You are not authorized for this function.**

To analyze this error, choose the menu path _System_ → _Utilities_ → _Display Authorization Check_ or enter transaction code SU53 in the command field.
![[Pasted image 20251015124428.png]]
You can now analyze the last error in your system that occurred due to a missing authorization. You can call transaction SU53 in any session, not just in the session in which the error occurred.

**Example:** In the previous figure, the user calls transaction VA07. The message "You are not authorized for transaction VA07" appears.

Then, the user calls transaction SU01 and will display the user data of another user. In this case, the authorization object _S_USER_GRP_ is checked. The authorization object is assigned to the user, but the required authorization values (activity "03" and user group "Training") are not assigned.

To analyze the missing authorization, the user enters transaction code SU53 in the command field and the system displays the authorization object that caused the last failed authorization checks. The system displays the value of the authorization object that the program required.

In the case of missing authorization values for a specific authorization object, you can check which other authorization values are assigned to the user.

Transaction SU53 displays the maximum of 100 failed authorization checks for each user in the upper area. It displays these for the last three hours at most. If there are very many active users and very many failed authorization checks, the number of checks and the period that is covered can also be smaller for a user. In addition, it displays the context in which the check occurred (that is, the transaction, RFC function module, or service). In the lower area, the authorizations of the user are displayed for all of the authorization objects that are displayed.

The system uses a ring buffer in the shared memory of the application server for saving failed authorization checks. Web Dynpro applications can also access this memory area.

The size of the buffer depends on the number of work processes, which is defined by profile parameters. It consists of 100 authorization checks for each work process in the standard system. This number can be changed by setting the profile parameter _auth/su53_buffer_entries_. The profile parameter can be maintained using transactions RZ11 and RZ10.

The user can also use transaction SU56 to view which authorizations are currently in his or her buffer.

## System Trace for Authorization Checks

If you do not know the required authorization, you can use the system trace or the authorization error analysis to determine them. You can use the system trace function to record authorization checks in your own and in external sessions using the system trace function : System Trace for Authorization Checks STAUTHTRACE. As an alternative, you can also use the system trace: _Tools_ → _Administration_ → _Monitor_ → _Traces_ → _System Trace_ (transaction ST01).

The trace records each authorization object that is tested, along with the object's fields and the values tested.

The system trace for authorization checks (transaction STAUTHTRACE) provides an optimized user interface to trace authorization checks. It works in the same way as the system trace (transaction ST01). However, it only evaluates authorization checks.

The evaluation of the system trace for authorization checks can be performed for the current server. It is also possible to start and stop the system trace for authorization checks on all servers or on selected servers of a system. When you display the authorization checks that were performed, the system displays an additional column containing the name of the server.![[Pasted image 20251015124949.png]]

You can analyze authorizations as follows:

1. Choose _Tools_ → _Administration_ → _Monitor_ → _Traces_ → _System Trace_ or transaction ST01.
    
2. Choose the _Authorization Check_ trace component.
    
3. To restrict the trace function to your own sessions, choose _Edit_ → _Filter_ → _Shared_. Enter your user ID in the _Trace for user only_ field in the displayed dialog box.
    
4. Start the trace by choosing the _Trace on_ button. The trace is automatically written to the hard disk.
    
5. Execute the relevant system actions.
    
6. Once you have completed the analysis, choose _Trace off_.
    
7. To display the results of the analysis, choose _Goto_ → _Analysis_ or the _Analysis_ button. Select the desired file and choose _Start Reporting_.
    

The results of the authorization check are displayed in the following format (see also the previous figure):


The return code shows whether or not the authorization code was successful.

##Information Systems for Administrators and Audit

You should not immediately implement the result of a trace or of transaction SU53 as new roles or profiles. First, analyze the system for existing settings. The _Information System_ and the _Audit Info System_ (which is used by auditors) are available to the administrator for this purpose.

You can use the User Information System to obtain an overview of the authorizations and users in your SAP system at any time using search criteria that you specify. In particular, you can display lists of users to which authorizations classified as critical are assigned. You can also use the User Information System to do the following.

### Examples from the User Information System

- Compare roles and users
    
- Display change documents for the authorization profile of a user
    
- Display the transactions contained in a role
    
- Create where-used lists
    

We recommend that you regularly check the various list that are important for you. Define a monitoring procedure and corresponding checklists to make sure that you continually review your authorization plan. We especially recommend that you determine which authorizations you consider critical and regularly review which users have these authorizations in their profiles.

![[Pasted image 20251015125704.png]]

Another way to read information from the system is a special role concept for auditing (previously done using _Audit Information System_).

The content of the concept has been revised by the auditing and risk management working group of the German-Speaking SAP User Group e.V. (DSAG), in cooperation with customers and partners. This group has considered a wide range of information from external and internal auditors, IT specialists, and consultants who examine SAP applications or whose companies implement SAP software. For more information, see _http://www.sap.com/germany/discsap/revis/index.htm_.
![[Pasted image 20251015131308.png]]


The **Audit Information System (AIS)** is a checking tool for:

- System checks
    
- Audit (business audit)
    
- Tax audits
    
- Internal auditing
    
- External auditing
    

The AIS role concept improves the **flow** and **quality of the check**.

The Audit Information System is a tool used by auditors to optimize a system and examine any weak points. The old menu-based version (AUDIT area menu) was replaced by a role-based environment. The role concept used now includes the same collections, structuring, and defaults for standard SAP programs, but is easier to scale. The content is defined using the transaction PFCG ( → _Tools_ → _Administration_ → _User Maintenance_ → _Role Administration_); the old transaction SECR is no longer used.

The roles are constructed to match the flow of the check for different check fields with default control data/evaluation programs for the area **"Business"** and **"System Audit"**. The roles can be found in PFCG with the ID "SAP*AUDITOR*"

![[Pasted image 20251015131328.png]]

The delivered single roles are split into two groups:

1. Authorization roles
    
2. Transaction roles
    

The authorization roles are easy to identify. The role names always end with the suffix "*_A". This means that all roles that do not end with a simple "A" are the corresponding menu roles.

Accordingly, the following condition applies:

- The authorization roles contain (manual) authorization values, but do not have a menu (such as SAP_AUDITOR_BA_SD**_A**).
    
- The transaction roles contain a menu, but do not have any authorization values (such as SAP_AUDITOR_BA_SD).
    

If you are now asking yourself "Why not use a single role with menu and authorizations?", there is a simple explanation.

What happens when you enter a transaction code in the role menu and then display the authorization data? Correct. Default authorization values are displayed for objects and fields. In many cases, however, there are too many defaults for auditing purposes, since the authorization goes far beyond just **"Display Authorization"**. If you were to modify these defaults for your own requirements, the time and effort needed to make changes to the content would be much too high (note: maintenance status "Changed").