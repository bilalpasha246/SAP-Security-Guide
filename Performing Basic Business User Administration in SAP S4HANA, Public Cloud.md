You are using the **Manage Workforce** app to perform the first tasks of Identity and Access Management (IAM) on SAP S/4HANA Cloud, public edition:
- Create workforce users
- Assign business users

The Manage Workforce app creates and updates worker information for employees and contingent workers, including work agreements and changing employment situations. This app enables you to upload/edit employee information independent of an HR system of record.
![[Pasted image 20251007105454.png]]

During an implementation project, you use the Manage Workforce app to create business users for the project team members in the SAP S/4HANA Cloud starter system and the initial users in the development, test, and production systems.

In SAP S/4HANA Cloud, public edition, a Business User must be assigned as a Worker (it could be an Employee or Contingent Worker type). Once integrated with a customer’s HR system (for example, SAP SuccessFactors Employee Central), the Manage Workforce app becomes read only to ensure only one HR data source. Changes to users must be made directly in the HR system of record after the integration is activated.

Business users are created parallel to a Worker and can be managed from the Maintain Business User app. The app allows for modifying and deleting business users within the system. You can also create business users, but you can only select a worker with no business user associated with the record.![[Pasted image 20251007105954.png]]

The **Maintain Business Users** app processes individual changes to business users. You can lock, unlock, and delete business users from the app. The options to perform these changes are on the application's first initial screen.

To assign business roles to a business user:

1. Open the Maintain Business Users app.
2. Select a business user to go to the details of that business user.
3. Choose Add Business Roles.
4. Select your required business roles and choose OK.
5. Choose Save.