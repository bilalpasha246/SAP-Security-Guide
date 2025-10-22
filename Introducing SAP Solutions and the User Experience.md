SAP has a long history of working with customers to help them use the latest technology innovations. For example:
- Mainframe with R2
- Client/Server architecture with R/3
- Worldwide Web with mySAP.com
- In-memory computing with SAP HANA
![[Pasted image 20251007074611.png]]![[Pasted image 20251007074727.png]]
Users log on to the SAP system using a frontend device at the **presentation layer**. They have various interfaces from which to choose to access the specific business process function or functions required for their job function. Each process function is executed using the frontend interface.

The **application layer** represents where the business logic and configured business process functionality are designed and implemented. It contains the infrastructure and resources to support end-user requests to execute requested functions. The application layer is made up of an instance. An instance represents a collection of processes and resources that support presentation layer connections to facilitate process execution.

Finally, the **data storage layer** comprises precisely one database and is the repository for all the SAP system's data and objects.

![[Pasted image 20251007075105.png]]

SAP UI development has two goals:
- Improve user productivity by simplifying and automating day-to-day tasks across any device.
- Reduce training and support costs with simple, role-based screens that speed ramp-up and minimize user errors.

With the release of SAP S/4HANA, SAP Fiori is the dominant interface for access to new SAP applications and solutions, both on-premise and within the cloud. SAP focuses on SAPUI5 as the latest technology for new features and business cases to support the shift to activity-based app design.
![[Pasted image 20251007075402.png]]

- **Homepage:** The homepage is the heart of the SAP Fiori launchpad and the central access point for SAP Fiori apps. The page contains tiles used to launch apps and can also show more application information. Because the launchpad is role-based, only apps relevant to the user’s role profile are shown.
- **Spaces:** A space and its pages structure the most relevant apps for users with a specific business role. Launchpad spaces display tiles that allow users to launch apps. They can also show more application information. As the launchpad is role-based, only apps relevant to the user’s role profile are shown.
- **Tiles:** A tile is a container that represents and displays an app that can be launched on the Fiori launchpad page. The app tiles are only available for use securely via specific business roles assigned to the business user.
- **User Actions Menu:** The User Actions Menu allows users to access their settings, preferences, and secondary shell functions, such as the App finder and personalization features. It also provides access to recent activities and a shortcut to tasks that need continued work. Certain groups of apps are displayed depending on the user's role. The menu is accessed by clicking the icon or photo on the right-hand side of the shell bar.
- **Notifications:** Users can access notifications by clicking the Notifications button on the right of the shell bar. The notification list displays system-generated notifications from various sources, such as the workflow inbox or chat notifications for taking immediate action.

![[Pasted image 20251007075707.png]]

SAP Fiori Launchpad can be run on an SAP NetWeaver ABAP Stack, SAP Enterprise Portal, SAP Business Client, SAP Fiori Client, and SAP Cloud Platform.

The SAP Fiori Launchpad is not technically the same on other platforms. Therefore, some features of SAP Fiori Launchpad on the SAP NetWeaver ABAP Stack may not be available on other platforms. Also, the configuration and authorization are different from platform to platform. However, the concept and the user experience are the same.