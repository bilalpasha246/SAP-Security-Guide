Historically, access to an SAP system required that a user had a **user master record**, which was maintained via the transaction code **SU01**. The user master record provided a place to define the basic context for a user, such as their user ID, first name, last name, e-mail, and so on. The user master record was also where an administrator assigned the user their **security roles**, which controlled the business actions that the user was authorized to perform, for example, creating a vendor or initiating a payment.

At the functional level, each user also interacted with applications in the context of one or more **business processes**. In sales, for example, a customer can be associated with a specific sales organization, distribution channel, and division. A **business partner** definition was used to link to the application-specific context required to perform a specific business function through an associated business partner role. However, the business partner and business partner role assignment were maintained separately from the user master record in a different application.

![[Pasted image 20251007081452.png]]

With the release of SAP S/4HANA, SAP introduced the **business user** concept based on the "principle of one." The business user represents a new identity model for the user in the SAP application, integrating the business partner concept with the user master record.
![[Pasted image 20251007081657.png]]

![[Pasted image 20251007082314.png]]

Using the example of SU01, the following data categories exist:

- **Person:** The personal data of the business user is derived from the corresponding business partner. If HCM integration is active, this data is mapped from the corresponding employee of the HCM system (SAP SuccessFactors or SAP HCM).
- **Work Center:** The business user's work center data is derived from the workplace address of the corresponding business partner. If HCM integration is active, the function and department fields are mapped by default to the corresponding employee of the HCM system.
- **Communication:** The business user's communication data is derived from the workplace address of the corresponding business partner.
- **Company:** When converting an SU01 user from SAP Business Suite (classic user) to a business user in SAP S/4HANA, the company address is copied to the business partner's workplace address.

