SAP Cloud Platform Identity Authentication Service (IAS) is a cloud service that provides authentication, Single Sign-On (SSO), user management, and On-Premise integration. IAS can also be used with SAP Identity Management or deployed along with other service offerings from SAP, such as Identity and Access Management as a service.![[Pasted image 20251007141940.png]]

Key features of SAP Cloud Platform Identity Authentication are:
- Secure authentication for cloud and On-Premise service provider applications
- Single Sign-On functionality from anywhere on any device (Web and desktop SSO)
- Social login through Twitter, LinkedIn, Facebook, and Google
- Strong authentication with configurable multifactor authentication enforcement, such as using time-based one-time passwords or Web two-factor authentication and fast identity online (FIDO) capabilities. Two-factor authentication based on one-time passwords
- Risk-based authentication is applied to service provider applications, user group assignment, and Internet Protocol ranges
- Easy Application onboarding
- Support of SAP and third-party software
- Password policies on the level of service provider applications
- Customizable look-and-feel features, including support to set up company branding
- User self-services, including self-registration and password reset
- Configurable user registration form
- REST APIs for user management
- Setup of custom privacy policies and terms of use on the application level
- Usage reporting capabilities
- Delegated authentication through integration with On-Premise user stores and corporate identity providers
- Identity federation based on SAML 2.0

There are two Usage Options for Identity Authentication:
1. Identity Authentication as an IdP proxy for seamless, flexible integration with customers’ existing IAM infrastructure
2. Identity Authentication as the landscape-wide identity provider offering secure authentication and user management capabilities

SAP’s Identity Authentication service is a proxy Identity Provider (IdP) in this scenario. This means it doesn’t directly authenticate the user's credentials but delegates that responsibility to an underlying identity provider (a corporate user store or another identity provider). In other words, while the SAP system still directs authentication requests to the Identity Authentication Service, another system linked to the Identity Authentication Service verifies user credentials.![[Pasted image 20251007142538.png]]

