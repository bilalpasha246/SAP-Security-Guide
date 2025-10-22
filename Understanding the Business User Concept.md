![[Pasted image 20251009090031.png]]
This harbours the risk of inconsistencies and also generates additional maintenance work. The business user concept is designed to avoid this.

SAP S/4HANA is introducing a new identity model for business users, which is based on the "principle of one". A business user is defined as a natural person who is represented by a business partner and a link to a user in the system. Business users interact with the software in the context of a business process, for example, in the role of a purchaser, a sales representative, or a production planner.

SAP S/4HANA Business User Management enables and supports the entire life cycle of business users such as organizational changes, change of employment, or retirement. A user in SAP S/4HANA has a one-to-one relationship with a corresponding business partner (natural person). This reduces redundant maintenance and prevents outdated information. Personal data and workplace address data can be obtained centrally.

![[Pasted image 20251009090302.png]]

![[Pasted image 20251009090349.png]]The business user is a SU01 user, but also has a one-to-one relation to the corresponding business partner. This relationship is time independent and cannot be changed anymore.

The business user concept is used in many new applications in SAP S/4HANA. SU01 users with Classic Address (Identity Address Type 00 - User's Old Type 3 Address) lead to limitations because the new business user model is a prerequisite for many business applications. As soon as Fiori apps are activated and used, business users are mandatory (for example Teams, CreditAnalyst in Credit Management or Situations).

The business partner contains the personal information, for example private address, workplace address, bank details, vendor and customer related data. The business partner and SU01 user share personal details and workplace address related data. The advantage of the new business user model is that the entire lifecycle of that person works without redundant maintenance of user address data. Business users can still be managed using transaction SU01, Central User Administration or identity management systems.

Using the example of SU01 the following data categories exist:

Person

The personal data for the business user is derived from the corresponding business partner. In case HCM integration is active this data is mapped from the corresponding employee of the HCM system (SAP SuccessFactors or SAP HCM).

Work Center

The work center data for the business user is derived from the workplace address of the corresponding business partner. In case HCM integration is active, the function and department fields are mapped by default from the corresponding employee of the HCM system.

Communication

The communication data for the business user is derived from the workplace address of the corresponding business partner.

Company

During the conversion of a SU01 user from SAP Business Suite (classic user) to a business user in SAP S/4HANA the company address is copied to the business partner workplace address.

## Create a user master record for a business user
![[Pasted image 20251009091005.png]]

HCM integration active means that you rely on the HR mini master (HR infotype based PERNR data model including the PA-Tables). This HR mini master can be locally maintained (for example via transaction PA30 or PA40) or via real integration scenarios with SAP SuccessFactors Employee Central or an external (third party) HCM system.
### Create a Business User using PA30 and PA40

The prerequisite for this scenario is that HCM integration is active.

Using transaction PA40, an employee must be created in HCM to whom a System ID is assigned in transaction PA30.

You then create a user for this System ID in SU01. The Maintain Users screen indicates that this is a user with business partner assignment.![[Pasted image 20251009091054.png]]

### Create a Business User using Maintain Employees App

The prerequisite for this scenario is that HCM integration is not active.

You can use the SAP Fiori app to create a business partner of the type Employee. The employee is assigned an Employee ID and a User ID. Therefore start SAP Fiori App Maintain Employees and choose Create. Then create an Employee with Employee ID and User ID.
![[Pasted image 20251009091219.png]]

You then create a user for this User ID in Su01. Start transaction SU01 to create an SU01 user. Enter the User ID in the User filed and choose Create User. The Maintain Users screen indicates that this is a user with business partner assignment.
![[Pasted image 20251009091246.png]]


