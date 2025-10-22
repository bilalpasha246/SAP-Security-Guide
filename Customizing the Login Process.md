## SAP Cloud Identity Authentication Service

SAP Cloud Identity Authentication Service provides simple and secure access to Web-based applications with various authentication methods at any time and from anywhere.

### Authentication and Single Sign-On in the Cloud

The Identity Authentication service provides secure and simple access based on the following factors:

- Identity federation based on SAML 2.0
- Web Single Sign-On SSO and desktop SSO
- Secure on-premise integration to reuse existing authentication systems
- Social login and two-factor authentication
- Risk-based authentication

![A diagram illustrates secure access and user management features using cloud identity and authentication services.](https://learning.sap.com/service/media/topic/c06182e0-8bea-4681-9cbc-7b1bb126f7de/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p1_001.png "A diagram illustrates secure access and user management features using cloud identity and authentication services.")

The Identity Authentication service provides user and access management based on the following factors:

- User administration and integration with on-premise user stores
- User groups and application access management
- User self-service, for example, password reset, registration, and user profile maintenance
- System for Cross-domain Identity Management (SCIM) API

The Identity Authentication service provides the following enterprise features:

- Branding of end user UIs
- Password and privacy policies

The following image illustrates the architecture of SAP Identity Authentication, showing how users such as customers, partners, and employees securely access SAP Cloud solutions and third-party applications via SAML or OpenID Connect using a centralized identity provider integrated with various on-premise and corporate user directories.

![The diagram focuses on Identity Authentication. It illustrates customers, partners, and employees connecting through SAML/OpenID to SAP services and cloud platforms via an on-premise user store or a corporate identity provider.](https://learning.sap.com/service/media/topic/c06182e0-8bea-4681-9cbc-7b1bb126f7de/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p1_002.png "The diagram focuses on Identity Authentication. It illustrates customers, partners, and employees connecting through SAML/OpenID to SAP services and cloud platforms via an on-premise user store or a corporate identity provider.")

### Open Security Standards

The Identity Authentication service is interoperable with all application supporting SAML* 2.0 standard or OpenID Connect (OIDC).

![A diagram illustrates secure access and user management features using cloud identity and authentication services.](https://learning.sap.com/service/media/topic/c06182e0-8bea-4681-9cbc-7b1bb126f7de/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p1_001.png "A diagram illustrates secure access and user management features using cloud identity and authentication services.")

### Delegated Authentication- Identity Authentication Service as a Proxy to a Corporate Identity Provider (IdP)

The Identity Authentication service has the following IdP proxy features:

- Authentication that is delegated to corporate IdP login
- Reuse of existing SSO infrastructure
- Easy and secure authentication for employee scenarios
- Federation based on the SAML 2.0 standard

![The diagram illustrates the flow of identity authentication: A user interacts with a corporate identity provider, which uses SAML for identity authentication. This results in access to applications in the cloud.](https://learning.sap.com/service/media/topic/c06182e0-8bea-4681-9cbc-7b1bb126f7de/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p1_004.png "The diagram illustrates the flow of identity authentication: A user interacts with a corporate identity provider, which uses SAML for identity authentication. This results in access to applications in the cloud.")

### Delegated Authentication - Authentication with an On-Premise User Store

The Identity Authentication service can connect to an on-premise user store.

- Users' credentials are taken from:
    - Active Directory (through LDAP)
    - AS Java (which can be either local UME, ABAP store or AD)
- There is no user replication required to the cloud
- Internal network ports do not need to be exposed to the Internet
- Other Identity Authentication product features can be used, including UI configuration policies and two-factor authentication

![The diagram illustrates how the user uses Identity Authentication to access Applications, connecting through Cloud Connector, LDAP, and Active Directory.](https://learning.sap.com/service/media/topic/c06182e0-8bea-4681-9cbc-7b1bb126f7de/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p1_005.png "The diagram illustrates how the user uses Identity Authentication to access Applications, connecting through Cloud Connector, LDAP, and Active Directory.")

### Delegated Authentication Reuse of Windows Domain Authentication (SPNEGO)

SPNEGO authentication provides the following:

- Users authenticated with Microsoft Active Directory can utilize SSO for Cloud applications without re-authentication
- Reuse of existing corporate identity infrastructure
- Secure authentication and SSO for Cloud and on-premise Web applications

![The diagram illustrates the user's access flow: The user gets a Kerberos token from Active Directory, requests access via SPNEGO, proceeds to Identity Authentication, and then accesses Applications](https://learning.sap.com/service/media/topic/c06182e0-8bea-4681-9cbc-7b1bb126f7de/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p1_006.png "The diagram illustrates the user's access flow: The user gets a Kerberos token from Active Directory, requests access via SPNEGO, proceeds to Identity Authentication, and then accesses Applications")

### Delegated Authentication Conditional Authentication

The following image illustrates an Identity Authentication system that manages access for employees, externals, and partners using various attributes, and connects to both corporate and partner identity providers.

![The diagram shows how partners, externals, and employees connect via IP address range, email domain, as a member of a user group and user type to authenticate their identity. Once authenticated, they connect to partner identity providers and corporate identity providers.](https://learning.sap.com/service/media/topic/c06182e0-8bea-4681-9cbc-7b1bb126f7de/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p1_007.png "The diagram shows how partners, externals, and employees connect via IP address range, email domain, as a member of a user group and user type to authenticate their identity. Once authenticated, they connect to partner identity providers and corporate identity providers.")

Depending on several factors, different types of users can be rerouted to different IDPs for authentication.

![The diagram shows two identity providers (IdP 1 and IdP 2) with login icons, both connecting to the IAS, which in turn connects to an application in a cloud.](https://learning.sap.com/service/media/topic/c06182e0-8bea-4681-9cbc-7b1bb126f7de/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p1_008.png "The diagram shows two identity providers (IdP 1 and IdP 2) with login icons, both connecting to the IAS, which in turn connects to an application in a cloud.")

As a proxy to multiple IdPs, the Identity Authentication service provides:

- A secure business network and allows partner users to login via their corporate IdP
- Authentication that is initiated by the corporate IdP
- An optional check for correct user group assignment can be configured upon successful authentication; a sync of users from IdPs to groups in the Identity Authentication service is required

### User Creation Sources

The following image illustrates various methods for provisioning users in an identity authentication system, enabling secure access to applications.

![Diagram shows identity authentication with methods: self-registration, syncing through IPS, CSV upload, manual creation, and programmatically through SCIM.](https://learning.sap.com/service/media/topic/c06182e0-8bea-4681-9cbc-7b1bb126f7de/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p1_009.png "Diagram shows identity authentication with methods: self-registration, syncing through IPS, CSV upload, manual creation, and programmatically through SCIM.")

## Branding and Customization

The following image highlights the customizable features and product capabilities of a login and registration system, including company branding, user interface customization, terms and conditions management, responsive design, and multilingual support.

![Customization and product features are listed. Customization includes company logo, app name and logo, color style, terms of use and privacy policy, UI text adjustment via API, and e-mail templates. Product features include responsive UIs and multilanguage support. Two ample screenshots show login and terms and conditions screens.](https://learning.sap.com/service/media/topic/a5682c07-871b-4ed3-84cf-54059db9f83f/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_Cloud_Platform_Identity_Authentication_Service_p2_001.png "Customization and product features are listed. Customization includes company logo, app name and logo, color style, terms of use and privacy policy, UI text adjustment via API, and e-mail templates. Product features include responsive UIs and multilanguage support. Two ample screenshots show login and terms and conditions screens.")

The following image shows a collage of enterprise login screens from SAP products.

![There are six sample logon screens of different styles shown.](https://learning.sap.com/service/media/topic/a5682c07-871b-4ed3-84cf-54059db9f83f/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p2_002.png "There are six sample logon screens of different styles shown.")

### User Self-Services

The Identity Authentication service provides a convenient user self-service that includes the following features:

- Self-registration
- Account confirmation via e-mail
- Forgotten password reset
- Editing of account details or password change
- Activation of two-factor authentication
- Linking or unlinking of social accounts

![There are three sample screenshots: an SAP Cloud Identity interface showing a profile with personal details, a registration form , and a dialog-box entitled Forgot my Password prompting the user to reset the password.](https://learning.sap.com/service/media/topic/a5682c07-871b-4ed3-84cf-54059db9f83f/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p2_003.png "There are three sample screenshots: an SAP Cloud Identity interface showing a profile with personal details, a registration form , and a dialog-box entitled Forgot my Password prompting the user to reset the password.")

### Access Protection for Applications

The following access protection is provided for applications:

- Protecting the registration to applications from spam and abuse
- Preventing bots from automated fake user registrations to your applications
- Google reCAPTCHA and phone verification provide further protection through self-registration

![There are three sample screenshots: a registration form showing fields for personal details, a reCAPTCHA with vehicle image selection, and a prompt to verify your phone number. The header reads Access Protection for Applications.](https://learning.sap.com/service/media/topic/a5682c07-871b-4ed3-84cf-54059db9f83f/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p2_004.png "There are three sample screenshots: a registration form showing fields for personal details, a reCAPTCHA with vehicle image selection, and a prompt to verify your phone number. The header reads Access Protection for Applications.")

### Logon Overlays in Customer Applications

The customer application logon screen can be programmed to integrate with the application. It has out-of-the-box integration with SAP Cloud portal.

![The screenshot shows the logon screen as an overlay.](https://learning.sap.com/service/media/topic/a5682c07-871b-4ed3-84cf-54059db9f83f/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_p2_005.png "The screenshot shows the logon screen as an overlay.")

## Authentication Options

The Identity Authentication service provides the following authentication features:

- Basic authentication
- Based on user ID/e-mail and password
- Reuse of Windows domain logon
- Kerberos token used for SSO
- Two-factor authentication
- Second factor is authenticated on a mobile device
- Delegated logonPs
    - Social Id
    - Corporate IdP

![Four authentication methods are listed: basic authentication, reuse of the windows domain logon, two-factor authentication, and delegated logon. The diagram illustrates the user accessing applications via identity authentication, displaying a login screen, code, social media icons, and an applications cloud.](https://learning.sap.com/service/media/topic/fb28b09b-7995-45a6-bc6f-75e1e4a2aeb2/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_P3_001.png "Four authentication methods are listed: basic authentication, reuse of the windows domain logon, two-factor authentication, and delegated logon. The diagram illustrates the user accessing applications via identity authentication, displaying a login screen, code, social media icons, and an applications cloud.")

### Two-Factor Authentication with SAP Authenticator

A one-time password (OTP) is required for login in addition to the password or security token. The second factor authentication is used in high security scenarios.

The SAP Authenticator mobile app creates a one-time password (six-digit) on a mobile device. It is available for iOS and Android and is RFC 6238 compatible (with authenticator apps from Google and Microsoft).

![There are sample instructions for two-factor authentication, using a QR code and secret key. Separately, a smartphone screen shows the app displaying a current passcode for verification.](https://learning.sap.com/service/media/topic/fb28b09b-7995-45a6-bc6f-75e1e4a2aeb2/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_P3_002.png "There are sample instructions for two-factor authentication, using a QR code and secret key. Separately, a smartphone screen shows the app displaying a current passcode for verification.")

### Control Access to the Application

The following image shows SAP Identity Authentication (IAS) applying conditional access rules—such as group membership, IP range, and registration status—to trigger two‑factor authentication before granting application access.

![In the flowchart, the user connects to the Identity Authentication service, and then completes two-factor authentication, before reaching the application.](https://learning.sap.com/service/media/topic/fb28b09b-7995-45a6-bc6f-75e1e4a2aeb2/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_P3_005.png "In the flowchart, the user connects to the Identity Authentication service, and then completes two-factor authentication, before reaching the application.")

### Custom Password Policy Configuration

The following image shows that the custom password policies can be configured to enhance account security.

![The screenshot shows the interface for configuring custom password policies. Options include setting password length, password lifetime, the maximum duration of inactivity, the number of reusable old passwords,the number of allowed failed login attempts, and the duration of the locked period.](https://learning.sap.com/service/media/topic/fb28b09b-7995-45a6-bc6f-75e1e4a2aeb2/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_P3_006.png "The screenshot shows the interface for configuring custom password policies. Options include setting password length, password lifetime, the maximum duration of inactivity, the number of reusable old passwords,the number of allowed failed login attempts, and the duration of the locked period.")

### OAuth

|   |   |
|---|---|
|- OAuth is an **open standard** for access delegation.<br>- It is used as a way for users to **grant web application access** to their information on another web application but **without giving them the passwords.**<br>- "OAuth 2.0 focuses on client developer simplicity while providing **specific authorization flows** for web applications, desktop applications, mobile phones, and living room devices."<br>- Source taken from the OAuth website.|![The image includes four statements about OAuth, sometimes specifically OAuth 2.0. The source is https://oauth.net/2/.](https://learning.sap.com/service/media/topic/fb28b09b-7995-45a6-bc6f-75e1e4a2aeb2/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_P3_007.png "The image includes four statements about OAuth, sometimes specifically OAuth 2.0. The source is https://oauth.net/2/.")|

### OAuth Authorization Flow

The OAuth authorization process is as follows:

1. The resource owner makes a call to protected resources using the OAuth 2.0 client.
2. The OAuth 2.0 client doesn't have an access token for the target system and redirects the browser to the authorization endpoint of the authorization server. This redirection is called authorization code request. At the authorization server, the resource owner is authenticated and can further restrict access or grant access to the preselected scopes.
3. The authorization server sends the authorization code back to the OAuth 2.0 client by redirecting the resource owner's user agent back to the redirection URI (which was defined during OAuth 2.0 client registration).
4. The OAuth 2.0 client sends an access token request to the authorization server's token endpoint. This access token request contains the authorization code.
5. The authorization server receives the access token request at its token endpoint and validates the authorization code. After a successful validation, the authorization server returns an access token to the OAuth 2.0 client.
6. The OAuth 2.0 client uses the access token to request resources.
7. The resource server grants the OAuth 2.0 client access to protected resources in accordance with the access token.

![The flowchart of OAuth Authorization shows how the resource owner, the authorization server, and the resource server exchange authorization codes and tokens for resource access. The text that follows provides more details.](https://learning.sap.com/service/media/topic/fb28b09b-7995-45a6-bc6f-75e1e4a2aeb2/SECCL1_24_en-US_media/SECCL1_24_en-US_images/U5_SAP_CPIAS_P3_008.png "The flowchart of OAuth Authorization shows how the resource owner, the authorization server, and the resource server exchange authorization codes and tokens for resource access. The text that follows provides more details.")