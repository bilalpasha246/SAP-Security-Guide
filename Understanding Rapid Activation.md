## Rapid Activation

SAP Fiori is how business users access SAP S/4HANA innovations. Many SAP S/4HANA customers are keen to make the most of these innovations, whether as a big bang or as a carefully staged journey. That means they may need to activate 100s and in some cases 1000s of SAP Fiori apps and other Fiori launchpad content, such as Web Dynpro ABAP applications and SAPGUI for HTML transactions. If this is your project, naturally you want an easy way to do this.

You can now use the new rapid content activation task lists to dramatically cut the activation effort from days to weeks down to hours to days. You do this by activating delivered SAP business roles as a consolidated single unit, complete with ready-to-test business user IDs. This is very different from the app by app by app approach of early alternatives. The good news is that even if you only intend to activate one business role as a showcase, these new task lists will make things much easier for you too.

![Illustration changing the implementation experience of SAP Fiori.](https://learning.sap.com/service/media/topic/e9d5e61f-fe1a-4227-a2d2-573d3cdfb6cb/ADM945_24_en-US_media/ADM945_24_en-US_images/Rapid_Activations_Goal.png "Illustration changing the implementation experience of SAP Fiori.")

The rapid activation approach is particularly useful when activating apps in your sandpit and demo systems. With some care you may be able to use it for activating apps in your development system too.

The aim of the rapid activation task lists is to help you get started exploring SAP Fiori in SAP S/4HANA as quickly as possible. This is particularly important in the early Explore phase of the SAP Activate methodology, where you are focused on understanding what apps have been delivered with your SAP S/4HANA system. This is the starting point for deciding which apps you will use, and how these apps fit to your organization’s specific business processes and business users.

One of the common missteps of many early SAP S/4HANA customers was to select and activate SAP Fiori apps one by one. This is a very high effort approach. It was also very error prone, as often related apps and dependencies needed to complete the end-to-end app deployment were missed resulting in confusion, frantic troubleshooting, and delays.

SAP Fiori apps are organized very differently to SAP GUI transactions. Compared to SAP GUI transactions, most Fiori apps are not intended to be used standalone or individually. Instead, SAP Fiori navigation enables a high degree of reuse and natural app-to-app navigation as the user completes a task.

It is more than just a change in organization: the UX paradigm of SAP Fiori differs fundamentally to the classical SAP GUI transaction pattern. Instead of big multipurpose transactions, which are typically launched individually (often via the TCode field), SAP Fiori offers a navigation network of task-oriented UIs, which are interconnected via Fiori Launchpad content. This means, there are usually multiple options to launch any app.

The degree of app-to-app forward navigation in SAP Fiori is much higher than SAP GUI transactions. The whole mechanism is controlled by authorizations, that is users see only those apps and links to apps which they are authorized to use. That is another fundamental difference to SAP GUI transactions.

A selective SAP Fiori implementation by cherry-picking single SAP Fiori apps breaks the user experience and leads to very high implementation costs. Since SAP Fiori apps are not designed to be used individually, to support the end-to-end task this may need even you to (re-)configure the complete app-to-app navigation network, which is defined in SAP’s delivered SAP Fiori Launchpad Content. This is why SAP recommends a role-based approach to implement SAP Fiori, that includes the following:

- Copy the SAP-delivered business roles and catalogs and adjust them to your needs.
- Implement complete business roles and not just single SAP Fiori apps.

![Illustration on rapid activation of roles.](https://learning.sap.com/service/media/topic/e9d5e61f-fe1a-4227-a2d2-573d3cdfb6cb/ADM945_24_en-US_media/ADM945_24_en-US_images/Rapid_Activation_of_Roles.png "Illustration on rapid activation of roles.")

The necessary steps to implement SAP Fiori in SAP S/4HANA using Rapid Activation are part of 2 task lists. A task list for activating the SAP Fiori Foundation and a task list for activating SAP Fiori Content by selected business roles.

Task list for SAP Fiori Foundation

- Execute basic configuration for Fiori Launchpad, SAP GUI for HTML and Web Dynpro ABAP common services
- Generate the generic roles for the Fiori Administrator and Fiori User

Task list for SAP Fiori content activation.

For each business role the task list will:

- Activate all the associated Fiori apps
- Activate all the associated Web Dynpro for ABAP applications
- Generate the business role (that is, the PFCG security role) with default authorizations
- Optionally, generate a Test user per business role

Once you have the SAP Fiori Foundation in place, you use the SAP Fiori Content Activation task list to activate all the apps associated with your selected business roles. You can select one business roles or activate multiple business roles together. You can run the task list as many times as you need to, to complete the activation of all your selected business roles. The more business roles you select in one run, the greater the saving in time and effort.

A good starting point for Rapid Activation is the blog series linked at [https://wiki.scn.sap.com/wiki/display/Fiori/Getting+Started](https://wiki.scn.sap.com/wiki/display/Fiori/Getting+Started), area Activating Apps.

### Rapid Activation Roadmap

Note

As a requirement to use SAP Fiori Rapid Activation the Fiori Front-End Server should be used with the Embedded deployment option. Embedded deployment is the default recommendation for SAP S/4HANA.

If you meet these prerequisites, you can implement the SAP Notes to deploy the Rapid Activation task lists. This is a once-off activity. You will find these steps further described in more detail suitable for your SAP S/4HANA release in the composite SAP note on Rapid Activation for SAP Fiori. A good starting point for all composite SAP notes is SAP note: 2902673 "Rapid Activation for SAP Fiori in SAP S/4HANA - Overview".

![Illustration on Rapid Activation roadmap.](https://learning.sap.com/service/media/topic/e9d5e61f-fe1a-4227-a2d2-573d3cdfb6cb/ADM945_24_en-US_media/ADM945_24_en-US_images/Rapid_Activation_Roadmap.png "Illustration on Rapid Activation roadmap.")

A good starting point for Rapid Activation is the blog series linked at [https://wiki.scn.sap.com/wiki/display/Fiori/Getting+Started](https://wiki.scn.sap.com/wiki/display/Fiori/Getting+Started), area Activating Apps.