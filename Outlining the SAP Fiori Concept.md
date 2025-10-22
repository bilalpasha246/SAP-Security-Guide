# Outlining the SAP Fiori Concept

Objective

After completing this lesson, you will be able to understand the SAP Fiori Concept.

## The SAP Fiori Concept

![Illustration of the SAP Fiori design concept integrating People, Business, and Technology.](https://learning.sap.com/service/media/topic/c920653b-87f3-4012-a0c9-c5829d90c822/ADM945_24_en-US_media/ADM945_24_en-US_images/01_01_UnderstandingTheSAPFioriConcept_001.png "Illustration of the SAP Fiori design concept integrating People, Business, and Technology.")

SAP has a long history of working together with customers to help them leverage the latest technology innovations: Mainframe with SAP R2, Client/Server architecture with SAP R/3, World Wide Web with mySAP.com and in-memory computing with SAP HANA.

But what about a good user experience? How does SAP meet users' needs in the most effective and enjoyable way?

SAP's understanding of how to create true innovation manifests in the award-winning user experience called SAP Fiori. 

SAP Fiori is the user experience for SAP software through all SAP products - such as SAP S/4HANA, Ariba Mobile, and SAP Hybris Cloud for Customer, and SuccessFactors.

Business applications should be ready for digitization and the cloud to meet future prerequisites.

Furthermore, they should be simple, intuitive, personalized, and tuned to the way users actually work. Therefore a user-centered and design-driven development is necessary.

This all should be based on a stable technology which uses web and open standards as well as in-memory computing.

What are the goals?

- To improve user productivity by simplifying and automating day-to-day tasks across any device.
- Reduce training and support costs with simple, role-based screens that speed ramp-up and minimize user errors.

Shift from monolithic solutions to activity-based apps.

SAP Fiori consists of 3 parts:

- SAP Fiori UX gives us the design direction.
- SAP provides developer tools and technology.
- Products provides with content like SAP Fiori apps.

![Illustration on SAP Fiori Launchpad.](https://learning.sap.com/service/media/topic/c920653b-87f3-4012-a0c9-c5829d90c822/ADM945_24_en-US_media/ADM945_24_en-US_images/01_01_UnderstandingTheSAPFioriConcept_004.png "Illustration on SAP Fiori Launchpad.")

SAP Fiori Launchpad can run stand-alone in a browser or in SAP Business Client (FLP connection) accessing an Application Server ABAP-based SAP system. It can be also integrated with SAP Enterprise Portal as well as with SAP Business Technology Platform. This offers a unified SAP Fiori user experience.

In this course, we will focus on the most common option, SAP Fiori Launchpad in a browser and connecting with Application Server ABAP.

The SAP Fiori Launchpad on other platforms is technically not the same. Therefore, some features for SAP Fiori Launchpad on ABAP Stack may not be available on other platforms. Also the configuration and authorization differ from platform to platform but the concept as well as the user experience are the same.

## Practice System Exercise: Access the Training System Landscape

Select Start Exercise to start the simulation.

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_FBF36EF1F7DFCF95:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

### Business Example

You want to use SAP Fiori Launchpad in the training landscape. In the SAP Fiori Launchpad, you want to explore the user actions menu and check the notifications.

### Task 1: Log In to the Training Landscape and System

In the training landscape, you want to log on to the SAP S/4HANA development system **S4D** where you will maintain the authorizations..

#### Steps

1. Log in to your training landscape.
    
    Note
    
    Login information will be provided by the trainer.
    
    1. Follow the guidance of the trainer.
        
2. Log on to the SAP GUI of the system S4D. Use the following data:
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Initial password provided for the user.|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        

### Task 2: Start the SAP Fiori Launchpad

In _Google Chrome_, start the SAP Fiori Launchpad. Examine the home page and work with some SAP Fiori Apps.

#### Steps

1. Open Google Chrome and start the SAP Fiori Launchpad. Examine the URL.
    
    1. In the _Microsoft Windows_ start menu, choose _Google Chrome_.
        
    2. In _Google Chrome_, go to _Bookmarks_.
        
    3. In _Bookmarks_, choose _10 Development_ → _s4dhost_ → _10 S4D SAP Fiori Launchpad_.
        
    4. On the login screen, enter the username and password.
        
        |Field|Value|
        |---|---|
        |_User_|**train-##**|
        |_Password_|The password you set at the beginning of the exercise|
        
    5. Examine the URL.
        
2. Examine the SAP Fiori Launchpad Information dialog box for the _SAP Fiori Shop_ app that is in space _Reference Apps._.
    
    1. In the _SAP Fiori Launchpad_, go to space _Reference Apps._ and launch the _Shop_ app tile.
        
    2. In the upper-right corner, select the user actions menu.
        
    3. Choose _About_.
        
    4. Examine the app information.
        
    5. Choose _OK_.
        
3. In the SAP Fiori Shop app, buy a product.
    
    1. In the SAP Fiori _Shop_ app, select a product.
        
    2. Choose _Add to Cart_.
        
    3. In the upper-right corner of the screen, choose _Shopping Cart_.
        
    4. Choose _Go to Checkout_.
        
    5. Choose _Buy Now_.
        
4. Access your purchase order via the notification in the SAP Fiori Launchpad.
    
    Note
    
    Your user is allowed to handle the purchase orders of other users, so be careful to only work with your purchase orders.
    
    1. In the upper-right corner of the screen, choose _Notifications_. You should see that there is a new notification.
        
    2. Select the most recent purchase order.
        
    3. Approve the product that has been ordered by your own user.
        
        Hint
        
        If the purchase order does not show your product, select the purchase order of your user on the left.
        
        Remember that your user is allowed to handle the purchase orders of all users.
        
    4. Choose _SAP_ logo to return to the FLP home screen.