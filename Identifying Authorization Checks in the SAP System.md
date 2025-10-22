![[Pasted image 20251008142203.png]]

The start authorization checks are available for the following applications:

- SAP transactions (authorization object S_TCODE)
    
- Web Dynpro ABAP application (authorization object S_START)
    
- RFC function modules (authorization object S_RFC)
    
- SAP Fiori applications (authorization object S_SERVICE)

#### SAP Transactions (Authorization Object S_TCODE)

When starting a transaction, a system program executes a series of checks to ensure that the user has the appropriate authorizations.

**Step 1:** Check if the user is authorized to start the transaction. Authorization object _S_TCODE_ (transaction start) contains the authorization field _TCD_ (transaction code). The user must have the authorization for the transaction code that he or she wants to run (such as "FB02", Change Document).

**Step 2:** Check if an authorization object is assigned to the transaction code. If this is the case, the system checks if the user has an authorization for this authorization object. The transaction code / authorization object assignment is stored in table **TSTCA**.

If any of the above steps fail, the transaction does not begin, and the user receives a message.

#### Web Dynpro ABAP Application (Authorization Object S_START)

Similar to the authorization object S_TCODE (for transactions), you use the authorization object S_START during the start authorization check of Web Dynpro ABAP applications. It has the three fields AUTHPGMID, AUTHOBJTYP, and AUTHOBJNAM, which correspond to the key fields PGMID, OBJECT, and OBJ_NAME of the object catalog (table TADIR). During the start authorization check, the key of the object catalog entry of the Web Dynpro ABAP application is therefore checked by the Web Dynpro ABAP runtime. For example: If you start the Web Dynpro ABAP application ABC, you require an authorization for the object S_START with the values AUTHPGMID = "R3TR", AUTHOBJTYP = "WDYA" and AUTHOBJNAM = "ABC".

This start authorization check is inactive when delivered and must be activated as described in SAP Note 1413011 - New start authorization check for Web Dynpro ABAP.

If you activate the start authorization check, you can use authorizations to control exactly which Web Dynpro ABAP applications that users can execute

#### RFC Function Modules (Authorization Object S_RFC)

When starting RFC-enabled function modules, authorization object S_RFC is used to check the start authorization.

The authority object S_RFC has the key fields REC_TYPE, REC_NAME, and ACTVT. The authority object S_RFC can be maintained for function groups (REC_TYPE = FUGR) and function modules (REC_TYPE = FUNC).

At run time, the first check is for the function group executed. If this check fails, a second check for the function module is executed.

#### SAP Fiori Applications (Authorization Object S_SERVICE)

Start authorizations for the activated OData services to launch a certain SAP Fiori app. You find the service(s) used per app in the app-specific documentation in the section SAP Fiori Apps.![[Pasted image 20251008142604.png]]
![[Pasted image 20251008142750.png]]
When a user signs on to an SAP system, a user buffer is built containing all authorizations for the user. Each user has his or her own user buffer.

If Mr. Peterson (example from the figure) logs on to the system, his user buffer contains all authorizations that were assigned to the role **MY_FI_AR_DISPLAY_MASTER_DATA** using the profile.

Hint

Every user can display **his or her own** user buffer using transaction SU56.

If you have some additional administrator rights, you can also view the buffers of colleagues. This is indicated most clearly if you can see the icon _Display for Different User/Authorization Object (F5)_ in "SU56".

A user would fail an authorization check if:

- The authorization object does not exist in the buffer.
    
- The values checked by the application are not assigned to the authorization object in the user buffer.