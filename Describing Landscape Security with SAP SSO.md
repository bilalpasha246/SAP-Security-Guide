One key goal of SAP’s Secure Login solution is to establish secure communication between all required components. SSO enables secure communication with certificate lifecycle management and encryption.

Secure Login for SAP SSO provides support for many advanced security capabilities, such as:

- Encryption of data communication for SAP GUI
- Kerberos/SPNEGO, X.509 certificates, and SAML 2.0 support
- Digital signatures
- FIPS 140-2 certified cryptographic functions
- Two-factor authentication
- Risk-based authentication using access policies
- RFID-based authentication
- Hardware security module support

Secure Login Service (SLS)
- Part of the product SAP SSO.
- Provides short-lived certificates to end-user desktops and backend systems.
- Advantage: SLS enables scenarios such as multifactor authentication and certificate lifecycle management.
- Disadvantage: SLS is an additional component.

![[Pasted image 20251008083542.png]]

The preceding figure illustrates the authentication process flow for using the Secure Login Service:

1. The user opens an SAP GUI connection.
2. The user authenticates to the Identity Authentication Service.
3. Optionally, authentication can be delegated to a corporate IdP (such as Azure AD).
4. After successful authentication, the Cloud Certification Authority (CA) issues an X.509 certificate.
5. SAP SLS returns the X.509 certificate, valid for one day, to SLC.
6. The X.509 certificate token authenticates the SAP GUI user to the ABAP system.

SSO using X.509 certificates can use existing Public Key Infrastructure (PKI) to authenticate users seamlessly across multiple systems and applications. This approach provides robust security by using digital certificates.

- SAP SSO can use an existing certificate for authentication.
- Certificates could, for example, come from a smart card or soft token.
- Advantage: No additional component is required, as the SLC does not need to access the cloud services, and the identity provider cannot authenticate.
- Disadvantage: Some value-added scenarios of SLS are not available and can be complex to configure and manage.

In this scenario, the SLS integrates with the existing enterprise PKI for user and server certificates. As a result, certificate signing remains based on established PKI and security policies. Storage and revocation processes remain unchanged.

![[Pasted image 20251008084030.png]]

Some customers already have an approach in place that provides their end users with an X.509 certificate. Options are for example:

1. **Smart Card:** An X.509 certificate coming from a hardware device.
2. **Soft Token:** An X.509 certificate that is automatically deployed on the user’s desktop, for example from a corporate CA.

Secure Login Client can use these certificates for Single Sign-On to the ABAP system as well if the backend configuration is in place. In that case, the Secure Login Client does not need to access the cloud services and there is no authentication by the identity provider.![[Pasted image 20251008084201.png]]
For organizations that have set up their own public-key infrastructure (PKI), they can simply use it with SAP Single-Sign On. In this scenario, the SLS integrates with the existing enterprise KPI for both the user and server certificates. As a result, certificate signing remains based on established PKI and security policies. Storage and revocation processes remain unchanged.

More scenarios and tools extend the capabilities for using and maintaining X.509 certificates. For example, instant user identification based on radio frequency identification (RFID) is supported for PC/SC and WaveID RFID reader devices.

