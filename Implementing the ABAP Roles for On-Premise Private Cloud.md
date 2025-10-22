The important terminologies in the authorization concepts are as follows:

- **Authorization Object Class:** This high-level category groups related authorization objects for better organization and easier management.
- **Authorization Object:** An authorization object is a specific, predefined set of authorization fields that define a particular combination of conditions required for access control.
- **Authorization Field:** The Authorization Object is subdivided into groups of fields. These individual fields specify the detailed conditions for access.
![[Pasted image 20251007092242.png]]

1. **Authorization Object Class:** BC_A (Basis-Administration)
2. **Authorization Object:** S_USER_GRP (User Master Maintenance: User Groups)
3. **Authorization Fields:**
    - **CLASS** (User Group in User Master Maintenance): SUPER (The specific User Group to allow access)
    - **ACTVT** (Activity): 01 (Create), 02 (Change), 03 (Display

![[Pasted image 20251007092759.png]]

Users are assigned to roles in the role maintenance transaction (transaction PFCG) or the user maintenance transaction (transaction SU01). Within SU01, by selecting the User tab page, the user IDs assignments are maintained. When selecting user IDs, the system uses the current date as the start of the validity period of the assignment and sets 31.12.9999 as the end date, by default. However, both the start and end validity dates can be changed as per business requirement.

Users are assigned to roles in the role maintenance transaction (transaction PFCG) or the user maintenance transaction (transaction SU01). Within SU01, by selecting the User tab page, the user IDs assignments are maintained. When selecting user IDs, the system uses the current date as the start of the validity period of the assignment and sets 31.12.9999 as the end date, by default. However, both the start and end validity dates can be changed as per business requirement.![[Pasted image 20251007093437.png]]

A user master record comparison determines whether authorization profiles can be added or removed from the current user based on their current or updated role assignments. During the comparison, profiles are added to a user master record due to newly added roles. If role assignments are manually or time-dependently removed, the corresponding authorization profiles are deleted from the user master record.