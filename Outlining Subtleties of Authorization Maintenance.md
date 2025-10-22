When maintaining and editing authorizations in role maintenance, different terms and icons appear that are perhaps not always correctly interpreted. What task do the traffic lights perform, for example?
![[Pasted image 20251009103208.png]]
The traffic lights are among the most important icons for the administration of authorizations. You can use them to obtain an overview very quickly. They display the current maintenance status of the authorizations at various levels. The different icons here are _Green_, _Yellow_, and _Red_.
**Green:** All fields below this level have been filled with values.
**Yellow:** There is at least one field (but no organizational level) below this level for which no data has been proposed or entered.
**Red:** There is at least one organizational level field (also known as org level) below this level for which no value has been maintained.
![[Pasted image 20251009103254.png]]
Functions that are provided by the context menu of the object classes, authorization objects, authorizations, and authorization fields are:

**Assignment of authorizations:** Displays the transactions that use this object.

**Full authorization:** You can set full authorization.

**Assigning full authorization for all empty fields:** If you require a role with full authorizations or want to assign "*" to all empty fields for test purposes, follow the procedure below.

**Field contents:** Choose the maintain icon to maintain an authorization field value. Alternatively, you can double-click the authorization field content, or click an empty field. You enter the values in a separate input window.

**Copy:** If you choose copy, a complete specification for an authorization object is copied with all fields. The status of the template is retained.

**Merge:** You can merge identical field contents for authorization fields of an authorization object .

If the activation and maintenance statuses are the same, the second condition comes into play. Authorizations can be merged only if one of the further conditions is met.

- One of the authorizations is included in the other authorization, with reference to all fields (the identity is also considered as a special case).
    
- Only one field is different in the two authorizations; all others are the same.
    
    There are further exceptions here, however:
    
    - An authorization that has empty fields cannot be merged with another authorization where at least one of these fields has content.
        
    - An authorization that has fields with full authorization (*) cannot be merged with another authorization where at least one of these fields does not have full authorization.
        

**Delete:** Delete the content of a field or delete an inactive authorization, or delete all inactive authorizations.

**Activate/Deactivate:** You can technically hide authorizations and show specifications for the check in the profile (the entry is retained). Although deleting the authorization has the same effect, it is not as simple to return to the default value in that case

![[Pasted image 20251009103705.png]]

#### Status Texts for Authorizations

**Standard:** All field values in the subordinate levels of the hierarchy are unchanged from the SAP defaults.

**Maintained:** At least one field in the subordinate levels of the hierarchy was empty by default and has since been filled with a value.

**Changed:** The proposed value for at least one field in the subordinate levels of the hierarchy has been changed from the SAP default value.

**Manual:** You maintained at least one authorization in the subordinate hierarchy levels manually (it was not proposed by Role Maintenance).

**The "Yellow Traffic Light Problem"**.

#### Status Texts After a Comparison

**Old:** The comparison found that all field values in the subordinate levels of the hierarchy are still current and that no new authorizations have been added.

**New:** The comparison found that at least one new authorization has been added to the subordinate levels of the hierarchy. If you now click _New_ in the application toolbar, all new authorizations in the subordinate levels are expanded.

## Display of Deleted Authorizations and Values for Merging of Authorizations

Following changes to applications in the role menu, the old authorizations are merged with the new authorization default values when authorization maintenance is started. Through this merge process, authorizations can be added, updated, or deleted.

Authorization maintenance displays which authorizations have been added or updated.

The ALV tree technology for authorization maintenance also displays which authorizations have been deleted and which authorization values have been added or deleted.

The ALV display provides the following enhancements for the merging of authorizations:

- In the column for the update status, authorization maintenance now indicates whether a value range has been added or changed at field level, too.
    
- In addition, a second window is displayed at the right or bottom margin, displaying deleted authorizations and values.

![[Pasted image 20251009104423.png]]
## Mass Maintenance of Authorization Values in Roles

Transaction PFCGMASSVAL allows you to change the authorization values of multiple roles at the same time.

This includes the changing of organizational level values, field values of authorizations for a selected object, and cross-object field value maintenance of authorizations for a selected authorization field.

![[Pasted image 20251009104654.png]]