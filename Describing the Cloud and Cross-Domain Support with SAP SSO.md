Security Assertion Markup Language 2.0 (SAML 2.0) is an internet standard for exchanging authentication and authorization data between security domains. It is an XML-based protocol that uses security tokens containing assertions to pass information about a principal (usually an end user) between an identity provider and a service provider. the assertion can include the means by which a subject was authenticated, the attributes associated with the subject, and an authorization decision for the given resource. SAML 2.0 enables web-based authentication and authorization scenarios, including SSO.

The service provider is a system entity that provides a set of web applications for common session management, identity management, and trust management. The service providers outsource the job of authenticating the user to the identity provider.

A service provider-initiated SSO workflow can be described as:

1. The user attempts to access a resource protected by SAML 2.0.
2. The SP redirects the user to a SAML IdP for authentication.
3. The IdP queries the user for authentication credentials.
4. The user supplies the requested credentials.
5. The IdP returns the user to the SP with an authentication response.
6. The SP presents the requested resource to the user.

![[Pasted image 20251008084531.png]]

The identity provider is a system entity that manages identity information for principals and provides authentication services to other trusted service providers. Setting up an IdP-initiated SSO with SAP Analytics Cloud is also possible. By default, IdP-initiated SSO is not enabled.

To enable IdP-initiated SSO on a tenant running in an SAP data center, you must request that the IdP administrator add a new assertion consumer service endpoint to your identity provider.

Possible reasons for doing this include:

1. To reduce the number of round-trips in your landscape. Starting at the ISP always redirects the user agent to the IdP. By starting at the IdP, you can save at least one round trip.
2. To make your IdP the single point of access.
3. Perhaps your portal is the host of your SP. Since all users start here anyway, you do not have to send them to the SP; you can return to the portal before sending them to the SP.

