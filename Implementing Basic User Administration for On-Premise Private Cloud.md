![[Pasted image 20251007082519.png]]

Suppose that a username and password combination is created in an SAP system for a user. In that case, logging on to the host's operating system with the same username and password combination is impossible. However, identical username and password combinations can be created for SAP systems and operating systems.

You can use the SAP Fiori app to create a business partner for the Employee type. The employee is assigned an Employee ID and a User ID. To begin, choose the SAP Fiori App **Maintain Employees** and choose **Create**. Then, create an Employee with an Employee ID and User ID.![[Pasted image 20251007090950.png]]

Then, you create a user for this User ID in **SU01**. To create a SU01 user, start transaction **SU01**. Enter the User ID in the User field and choose **Create User**. The Maintain Users screen indicates that this is a user with a business partner assignment.

In an SAP system, an authorization check is performed every time a transaction is called. If you attempt to start a transaction for which you are not authorized, the system rejects the login and displays an appropriate error message.![[Pasted image 20251007091145.png]]

![[Pasted image 20251007091217.png]]

In the SU01 transaction in SAP, various user types can be assigned to users. These user types determine the level of access and permissions that a user has within the system. Some of the common user types include:

- **Dialog user:** This is a standard user type for interactive access to SAP applications. Dialog users can log in and perform transactions within the system.
- **System user:** This user type is used for technical system processes and background operations. System users typically have restricted access and are used for automated tasks.
- **Service user:** Service users are used for specific application services within the SAP system. They have restricted access to specific tasks related to their assigned service.
- **Reference user:** This user type is used for creating templates for new users. Reference users have predefined settings and authorizations that can be used to create new user accounts.
- **Communication user:** Communication users are used for external communication with other systems or applications. They are typically used for system-to-system communication and have restricted access and permissions.
![[Pasted image 20251007091430.png]]
