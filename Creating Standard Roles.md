What is Role Maintenance?

Role Maintenance is the central tool for generating authorizations and authorization profiles and assigning them to users.

In Role Maintenance, system administrators choose transactions, menu branches (from the SAP menu) or area menus. The functions chosen correspond to the field of activity of a user or a group of users. Role Maintenance offers two different maintenance views:

- Basic maintenance (menus, profiles, and other objects)
    
- Complete view (Organizational Management and workflow)
    

The menu tree set up by system administrators for users with a specific role in the company corresponds to the user menu that appears if a user (to whom the corresponding role is assigned) logs on to the SAP system.

Role Maintenance automatically provides the corresponding authorizations for the functions chosen. Some of these authorizations have default values. Traffic light symbols tell you which values you need to maintain.

Finally, Role Maintenance generates an authorization profile from this data, which you can assign through the role.
![[Pasted image 20251009092003.png]]
What are roles?

A role is a set of functions describing a specific work area. The "Accounts Receivable Accountant" role, for example, contains transactions, reports, and/or Internet/Intranet links that an accounts receivable accountant needs for his or her daily work. Through roles, you also assign the authorizations that the user, in the example, the accounts receivable accountant, needs to access the transactions, reports, and so on, contained in the menu.

Roles are used to implement the menus that users can work with after they have logged on to the SAP System. You can use roles predefined by SAP and roles that you have created yourself. You can find the predefined roles using the "F4" help under _SAP Menu_: _Tools__Administration__User Maintenance__Role Administration__Roles_, or using the menu path _Menu_ → _Display Role Menu_, or by choosing the "Other Menu" button.

You can use the report _RSUSR070_ to display the role templates that are delivered by SAP.

In addition to the normal "Login" users, you can assign object types such as jobs, organizational units, or positions to roles. This is referred to as integration using Organizational Management.![[Pasted image 20251009092117.png]]
All the work steps you need to perform to create a role, including assigning the role to the user, are listed in the following as a thread.

To call Role Maintenance, choose "Create menu" on the _SAP Easy Access_ initial screen, or choose the following menu path: _Tools_ → _Administration_ → _User Maintenance_ → _Role Administration_ → _Roles_. The corresponding transaction code is **"PFCG"**.

#### Thread

- - The first step is defining the role and entering a short description of its contents.
- - In the second step, you define the activities for the user role. The result of this definition process is a role (or several roles) that collects all activities of the role - represented by means of transactions, reports, and Web addresses.
- - Simultaneously, you define what the menu tree for the new user role should look like.
- - Thereafter, the authorizations for the activities selected are created and profiles generated. This step normally involves the greatest administrative maintenance effort.
- - Subsequently, the users are assigned to the roles.
- - Finally, depending on the settings in PFCG, the comparison with the user master records of the users which have just been assigned to the roles is performed.![[Pasted image 20251009092302.png]]
**Basic Maintenance** allows you to:

- Access all of the functions for role maintenance
    
- Assign the roles only to SAP users
    

The **Complete View** (Organizational Management) displays all assignments and data for a role.

This view is useful for users in Personnel Planning and Development, particularly for organizational management and workflow. The Complete View allows you to:

- Access all of the functions for role maintenance
    
- Change the validity time period of the role
    
- Link tasks with a role
    
- Assign the role to objects in the organizational plan and restrict the validity dates for each assignment
    
To make the process of creating a role easier to remember, all process steps are shown repeatedly in the from of a "to do" list in this lesson.![[Pasted image 20251009092351.png]]
![[Pasted image 20251009092359.png]]
SAP does not use different names for single and composite roles. When creating or naming your roles, you should consider a naming concept that differentiates between single and composite roles. It is also useful to include a system abbreviation in the naming concept.

## Determine Activities and Design User Menus
![[Pasted image 20251009092601.png]]![[Pasted image 20251009092603.png]]
Definition of the roles:

Using roles, you define which activities are assigned to a specific role in the company. The authorization administrator selects those transactions in Role Maintenance that users with a specific role in the company must perform regularly. The administrator also chooses any Web addresses if these are useful for the daily work of a role holder (for example, a weather forecast service would be of interest to field service personnel). In addition, frequently needed reports can also be added to the user menu.

You can create completely new roles if required. In most cases, however, it is easier to use the roles delivered by SAP as a **template**, to **copy** them, and then change them to meet your own requirements. You can choose the copy icon on the initial screen of transaction PFCG.

You have two options when copying:

1. **"_Copy selectively_"**
    
    You decide what is copied.
    
2. **"_Copy all_"**
    
    Personalization and user assignment are also automatically copied.

![[Pasted image 20251009093159.png]]
![[Pasted image 20251009093219.png]]Changing the functions:

You can adjust the transactions listed in the menu tree of a role to meet your individual requirements:

- You can delete transactions that you do not need and add new ones (by choosing the "Transaction" button or by copying transactions "from other roles" or from other "menus").
    
- You can add reports (by choosing the "Report" button). Role Maintenance generates a transaction code (which is either created automatically or which you define yourself) that can be used to start the report from the menu. You can also include queries, BW reports, and transactions with variants in this way.
    
- You can add Internet sites (by choosing the "Other" button). Similarly, you can add links to documents (such as Microsoft Excel files). You add links to documents in the same way as you add links to Internet pages. Instead of the URL, you then enter the path of the required file.

Changing the menus:

You can create, delete, move, or rename directories. The operation is similar to that of graphical file managers.

To distribute the role to a particular target system, choose _Distribute_. Note that the authorization data for the role is not distributed together with the role. You must therefore add the authorization data for distributed roles in the target system. There are other settings that you need to take into account for this distribution. For more information, see the _F1_ help.

You can also use transaction ROLE_CMP to compare and adjust role menus across systems.
![[Pasted image 20251009093328.png]]


![[Pasted image 20251009093944.png]]
![[Pasted image 20251009093954.png]]

Creating the authorizations and authorization profiles:

Role Maintenance automatically generates authorizations based on the menu functions that you have chosen before. Role Maintenance cannot, however, propose "default value" authorizations that are suitable for everyone in the company. Therefore, the authorization administrator must normally post-process the authorizations manually in cooperation with the user departments and the audit division. By choosing "Organizational Levels", you can simultaneously maintain a large number of authorization fields. This greatly simplifies the manual post-processing work.

In the example, the transaction SO01 (SAP Office) was added to the role "_MY_ROLE_" (which was created by copying the SAP template). As a result, the yellow traffic lights appear in the menu tree in the above example, The authorization for file access is a good example to show why manual post-processing is necessary. Role Maintenance cannot know if the users should have only **read access** or also **write access** to the files.

Although Role Maintenance automatically generates the authorizations, you can also add authorizations manually to an existing profile, which might be desirable in some cases. To do this, choose the "_Change Authorization Data_" button on the "_Authorizations_" tab page, and then "_Edit_ → _Insert Authorizations_". The following options are available:

- Selection criteria:
    
    Here you can find authorizations for objects grouped by object class.
    
- Manual input:
    
    If you know the name of the authorization object for which you want to manually add authorizations, you can enter it here directly.
    
- Full authorization:
    
    This option fills all authorizations with the value "*".
    
- From profile...:
    
    Here you can use authorizations from individual profiles.
    
- From template...:
    
    If you want to create a user with "almost all" authorizations, you can use the SAP authorization templates designed for this purpose.

![[Pasted image 20251009094423.png]]

Having maintained the authorizations in accordance with the policies of your company, you can generate the authorization profile. It is only then that the authorizations contained take effect.

During the generation, Role Maintenance collects all entered values and assigns them to a profile. However, one profile can only contain a certain number of authorizations. It is therefore possible that one role has several profiles. You can recognize these profiles from the fact that they have identical names for the first **10 characters**, and an appended number starting with 1-99 (SAP Note _16466_). These are known as sequential profiles.

This division is performed automatically and is decided by Role Maintenance. It depends on the fields used and on the number of entries.


![[Pasted image 20251009094453.png]]![[Pasted image 20251009094509.png]]
Assigning users:

You must assign roles to users so that users are provided with the menu tree for their role when they log on to the system.

You assign roles to users by adding the corresponding names to the list on the _User_ tab page of Role Maintenance. Users can be assigned to more than one role. It makes sense to define roles for specific cross-role activities. An example is the activity "Print". Regardless of their function, all users (who are authorized to print) can be assigned to a role with the activity "Print". This eliminates the need to add the "Print" transaction to a large number of roles, which is a cumbersome task.

It is also possible to assign roles to users for a limited period of time. This makes sense, for example, for year-end closing: Physical inventory activities should only be allowed for a limited time. So that a time-dependent assignment of an activity profile to a user master record becomes effective, you must perform a comparison (see the figure _Compare User Master Record_).

There are two ways to do this:

1. As a background job: Report **_pfcg_time_dependency_** is run before the start of the business day, but after midnight, meaning that the authorization profiles in the user master record always have the most up-to-date status in the morning.
    
2. Alternatively, using transaction PFUD, (User Master Data Reconciliation).
    
    As an administrator, you should regularly execute this transaction as a check. In this way, you can manually process errors that may have occurred and been reported during the background job. Choose the _Complete Reconciliation_ radio button to compare all roles.
    

The last step to be performed is the user master comparison from transaction PFCG.![[Pasted image 20251009095236.png]]
![[Pasted image 20251009095240.png]]

Comparing the user master:

So that users are allowed to execute the transactions contained in the menu tree of their roles, their user master record must contain the profile for the corresponding roles.

You can start the user compare process from within Role Maintenance ("User" tab page and "User Comparison" button). As a result of the comparison, the profile generated by Role Maintenance is entered into the user master record.

Hint

The condition for this however, is that the validity period of the role includes the current date. If this is not the case, the role is assigned and entered into the master record, but the profile is not.

If you assign roles to users for a limited period of time only, you must perform a comparison at the beginning and at the end of the validity period. We recommend that you schedule the background job **_pfcg_time_dependency_** in such cases.


