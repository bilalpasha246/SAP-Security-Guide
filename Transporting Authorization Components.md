## Options for Transporting Authorization Components

User data and authorization data must be exchanged in system landscapes with multiple SAP systems. The data is either exchanged between different clients of an SAP system or between clients of different SAP systems.

In principle, the SAP authorization concept differentiates between the transport components described here.

### **Which Authorization Components Can Be Transported?**

- User master records
    
- Roles
    
- Authorization profiles
    
- Authorization default values
    

Authorization profiles can be transported together with their roles. Working with authorization profiles without an assigned role should remain the exception. The transport connection of transaction SU02 for maintaining authorization profiles is only mentioned here for completeness and is not discussed further.
![[Pasted image 20251015140216.png]]

User master records can be maintained centrally in one client of a system. If a new client is built, it can initially be filled with the user master records of the maintenance client. Client management transactions can be found under the menu path: _Tools_ → _Administration_ → _Administration_ → _Client Management_ → _..._.

#### Local Client Copy

If a new client is filled with data from another client of the same SAP system, this copy process is called a local client copy. Since the data of both clients is stored in the same database, it is not necessary to transport the data using the network or the operating system. The local client copy is started with transaction SCCL or in the client management with _..._ → _Client Copy_ → _Local Copy_.

#### Client Copy Between Systems

If a new client is filled with data from another SAP system, it can be copied with a client transport (1) or as a remote client copy (2).

1. The client transport exchanges its data with a data export at the operating system level. Transaction SCC8 can be started in the client management by choosing _..._ → _Client Transport_ → _Client Export_.
    
2. In a remote client copy, the data is copied over the network and not as a file. Transaction SCC9 can be found in the client management under _..._ → _Client Copy_ → _Remote Copy_


## Transport roles: With and without profile information, with and without user assignments, in a CUA landscape or without CUA

#### Roles Without Central User Administration

SAP roles are available in all systems and are not transported. If roles that you developed yourself are to be transported between clients or SAP systems, you must differentiate between situations where Central User Administration is implemented, and those in which it is not.
![[Pasted image 20251015140629.png]]
If you are **not** using Central User Administration, roles can be transported with user assignments. The transport is started with a Customizing request, which you can create in Role Maintenance by choosing _Utilities_ → _Mass Transport_. The transport request is either imported into another SAP system with the Transport Management System or into another client of the same SAP system using transaction SCC1. The user master records of the target client must be compared after the import. You can do this manually from Role Maintenance by choosing _Utilities_ → _Mass Comparison_ or periodically in the background (PFCG_TIME_DEPENDENCY). You can also create the background job there.

By default, authorization profiles are transported with roles. If this is not desired, you must prevent the data export in the source system with the control entry (_PROFILE_TRANSPORT:=NO_) in table _PRGN_CUST_. The table entry can be made using maintenance transaction SM30.

You can start the mass generation in Role Maintenance by choosing _Utilities_ → _Mass Generation_.

#### Transporting Roles with User Assignment

If you do not want to transport the user assignments to roles, you can protect the target system with an import lock. To do this, the control table _PRGN_CUST_ must contain the entry (_USER_REL_IMPORT:=NO_).

#### Roles with Central User Administration
![[Pasted image 20251015140802.png]]

Roles must also exist in the systems in which they are assigned to users within the Central User Administration. If systems are assigned to a Central User Administration, roles must be transported without user assignment since these assignments are made in and distributed from the central system. If user assignments were transported, there would be a temporary inconsistency between the actual state of the system and its subsystems. The imported assignments are deleted without being copied to the central system the next time there is a distribution. For security reasons, the import lock for user assignments therefore should be set for systems within the Central User Administration ("SM30", _PRGN_CUST_, _USER_REL_IMPORT := NO_).

A Customizing request for roles is created analogously to the scenario without Central User Administration. The authorization profiles are also transported in the same way.

#### Uploading and Downloading Roles

Normally, it is only possible to exchange data with transport requests between SAP systems with the same release status. For example, if roles have to be exchanged within the Central User Administration across releases, this can be done by downloading or uploading roles, if necessary.

After an upload, the role may have to be edited and generated. You can choose to upload or download in Role Maintenance by choosing _Role_ → _Upload/Download_. You can save multiple roles in a local file at the same time by choosing _Utilities_ → _Mass download_.

![[Pasted image 20251015141345.png]]

The customer tables _USOBX__**_C_** and_USOBT__**_C_**, which control the behavior of Role Maintenance, must be filled in each system in which Role Maintenance is used.

If these tables are adjusted to the customer's needs, they can then be transported as a whole. This means that you transport all the settings for the authorization checks, authorization default values, and the corresponding field values.

1. The transport link can be found under step **3** of transaction SU25, which must be executed when you activate Role Maintenance.
    
2. You can use transaction SU24 to change individual authorization default values. In this case, the system automatically and immediately creates a transport request.
    

In both cases, a transport request is transported and distributed to other SAP systems in the context of the Transport Management System.

