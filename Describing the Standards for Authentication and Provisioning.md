SAML
Regarding authentication, Security Assertion Markup Language (SAML) is a widespread standard for Web-based SSO functionality. It is an XML-based protocol that uses security tokens containing assertions to pass information about an end user (principal) between an identity provider (SAML authority) and a service provider (SAML consumer). The Organization for the Advancement of Structured Information Standards (OASIS) provided the SAML 2.0 specification, which replaced the previous SAML 1.1 specification. Currently, SAP and its customers use SAML2.

The prerequisite for using this standard is an existing trust relationship between the identity provider and the service provider. The service provider must know where to send the authentication requests, and this destination–the place from which the service provider retrieves the target information for the browser redirect–is configured as a trusted identity provider.

OIDC
OpenID Connect (OIDC) is an open standard the OpenID Foundation promotes that extends the OAuth 2.0 protocol with an identity layer. An authorization server verifies the end user’s identity to a Web-based, mobile, or native client. In the context of OIDC, the identity provider is the OpenID provider, and the client is the relying party.

The OpenID provider responds to the relying party through a browser redirect with an OAuth authorization code, which the relying party exchanges in a back channel for an OAuth access token and an identity token (ID token). The ID token is a JWT conveying select information about the end user directly to the relying party. With the access token, the relying party can call the user information service of the OpenID provider to obtain additional information about the end user, for example, data too voluminous to be included in the ID token. This information makes authentication possible. For more details about the OIDC protocol and its steps, see: [OpenID Connect Core 1.0](https://openid.net/specs/openid-connect-core-1_0.html).

Given these advanced token exchange flows in OIDC, support for SAML for direct integration between SAP BTP and a corporate identity provider is no longer strategic. SAP chooses to integrate SAP BTP with SAP Cloud Identity Services through OIDC. A setup using either SAML or OIDC authentication can easily handle heterogeneous systems that use different identifying attributes of users. For example, while some systems use an e-mail address for the logon, such as user.name@sap.com, others require a username, such as JDOE. A configuration in the SAML identity provider or OIDC provider supports mapping per service provider or relying party. Specific values, such as the user's identifying attribute or the subject name identifier in SAML and OIDC terms, must be specified for configuration purposes. Some service providers can require other attributes, such as the user’s country or name. Obtaining the proper information from the user store eliminates any synchronization effort between the service provider and the identity provider.

SCIM
SCIM is an open standard for the automated exchange of user information in a system landscape. It provides a standard format for typical operations on user accounts, such as retrieval, creation, modification, and deletion. Users are described using specific attributes, attribute schemes, and group memberships. Attributes can contain, for example, contact information, group memberships, and assignments to authorization entities.
![[Pasted image 20251007143712.png]]
SCIM is SAP's standard protocol for provisioning, and a common SAP-specific SCIM schema exists across SAP applications. Although point-to-point SCIM connections from an IDM to SAP applications are possible, SAP recommends provisioning users and groups with the Identity Directory in SAP Cloud Identity Services. From that repository, Identity Provisioning replicates them to the target SAP applications.




