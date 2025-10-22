Secure Login provides strong encryption, secure communication, and Single Sign-On (SSO) between a wide variety of SAP components:

- SAP GUI and SAP SSO 3.0 with Secure Network Communications (SNC)
- HTML-based user interfaces and SAP SSO 3.0 with Secure Socket Layer – SSL (HTTPS)
- Third-party application servers supporting Kerberos and X.509 certificates

Secure Login Client allows you to benefit from the advantages of SNC without being obliged to set up a public-key infrastructure (PKI). Secure Login allows users to authenticate with one of the following authentication mechanisms:

- Smart cards and USB tokens with an existing PKI certificate
- Microsoft Crypto Store with an existing PKI certificate
- Microsoft Windows Credentials
- Username and password (several authentication mechanisms)
- LDAP server
- RFID identification

Many of these authentication methods can be used in parallel. The Secure Login solution also supports Risk-Based Authentication. A policy server provides authentication profiles that specify how to log on to the desired system. Based on contextual information and configurable rules, customers can configure a dynamic environment that can vary the authentication process during login. Contextual information could include client IP addresses, user roles, and certificates. This information could be used to enhance the authentication process, for example, by:

- Allowing access to specific resources only from certain IP ranges
- Require a second authentication factor if the first authentication step was based upon a password instead of an X.509 certificate
- Enforce two-factor authentication for particular groups (for example, Administrators)

SAP Single Sign-On (SSO) using Kerberos provides secure access to SAP business applications at a reduced total cost of ownership (TCO). This scenario is based on a user’s authentication to the Microsoft Windows domain during the desktop login process. Active Directory provides a Kerberos security token that SAP business applications accept as proof of identity. Authentication is supported on desktop systems running Windows OS, MacOS X, and mobile devices (iOS) that are part of the Windows domain, provided the user has an account in Active Directory.

