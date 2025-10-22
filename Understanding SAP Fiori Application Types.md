# Understanding SAP Fiori Application Types

Objective

After completing this lesson, you will be able to explore SAP Fiori Types and Recommendations.

## SAP Fiori Application Types

#### Overview

There are three different application types for SAP S/4HANA Fiori applications. Each of them is differentiated not only by their usage, but also by their architecture and configuration.

![Illustration on SAP Fiori Architecture Application Types for SAP S/4HANA.](https://learning.sap.com/service/media/topic/c7d7cf93-ea46-4331-9545-82deaa55b711/ADM945_24_en-US_media/ADM945_24_en-US_images/01_02_UnderstandingSAPFioriArchitectureWithS4HANA_002.png "Illustration on SAP Fiori Architecture Application Types for SAP S/4HANA.")

SAP S/4HANA contains further classic applications using an SAP Fiori theme. These apps can be called from the SAP Fiori launchpad and need a specific configuration. They are called legacy apps. Legacy apps are Web Dynpro and SAP GUI for HTML Applications, which already existed before SAP Fiori was announced. Customers may choose which legacy apps they want to have in their _SAP Fiori launchpad_ using the configuration and customizing for SAP Fiori.

Legacy apps are developed with Web Dynpro and GUI for HTML technologies. They are not mobile enabled but provide an SAP Fiori look and feel.

SAPUI5 is the technology for the most SAP Fiori apps. In SAP S/4HANA, there are different subtypes of these apps, depending on their use case.

There are apps that are launched by using an app launcher tile. For these apps, what information is displayed and how it is displayed is defined as part of the provided app-specific content. You cannot adapt or configure the information displayed by these apps. However, in the SAP Fiori launchpad, you can control what each user sees by grouping these apps into catalogs and spaces and assigning them to roles.

Apps that are launched by using an app launcher tile can be:

Transactional Apps

- Usage of ABAP to provide the classic approach for functions of a business system
    
- Available for SAP S/4HANA and SAP Business Suite on any DB
    

Analytical Apps

- Usage of analytical capabilities of SAP HANA to provide insights in business data
    
- Available for SAP S/4HANA and SAP Business Suite on HANA
    

Apps that are launched using SAP Fiori Search or through navigation from other apps are called Object Pages.

Object Pages / Fact Sheet Apps

- Usage of Enterprise Search capabilities of SAP HANA to provide search results
    
- Available for SAP S/4HANA and SAP Business Suite on HANA
    

SAP Fiori Search is part of the SAP Fiori Launchpad and provides a contextual search.

![Screenshot showing SAP Fiori Apps Reference Library.](https://learning.sap.com/service/media/topic/c7d7cf93-ea46-4331-9545-82deaa55b711/ADM945_24_en-US_media/ADM945_24_en-US_images/01_01_UnderstandingTheSAPFioriConcept_006.png "Screenshot showing SAP Fiori Apps Reference Library.")

SAP Fiori is foremost a collection of apps representing the new user experience of SAP and the face of SAP S/4HANA. SAP Fiori apps can be categorized by line of business, industry, and most important user role, as well as technical foundation. All available apps can be explored using the _SAP Fiori apps reference library_. See [https://www.sap.com/fiori-apps-library](https://www.sap.com/fiori-apps-library).

Each SAP Fiori app has a unique _App ID_. When running the app in the _SAP Fiori launchpad_, choose _About_ in the _Me Area_. The subsequent UI shows information about the app including the _App ID_.

The _App ID_ can be used to search for the documentation of the app in the _SAP Fiori reference library_ and it is visible in the header of the documentation.

Hint

The _App ID_ of a transaction is its transaction code.

### Example for a SAPUI5 Fiori App

![Screenshot showing the example of SAP Fiori SAPUI5 App.](https://learning.sap.com/service/media/topic/c7d7cf93-ea46-4331-9545-82deaa55b711/ADM945_24_en-US_media/ADM945_24_en-US_images/ExampleSAPUI5FioriApp.png "Screenshot showing the example of SAP Fiori SAPUI5 App.")

Analytical apps provide insight into the real-time operations of your business by collecting and displaying analytic information and indicators, such as KPIs, directly in your browser. To do this, the analytical apps combine the data and analytical power of SAP HANA with the integration and interface components of SAP Fiori.

For example, Overview Pages, Analytical List Pages, and other apps that mix transactional and analytical capabilities.

Transactional apps perform transactional tasks, such as creating a leave request for an employee or managing quotations. SAP Fiori transactional apps represent simplified views and interactions with existing business processes and solutions. They generally run on any database except if they are developed and shipped with SAP S/4HANA Then, they run only with SAP HANA database.

Each SAP Fiori app has a unique _App ID_. When running the app in the _SAP Fiori launchpad_, choose _About_ in the _Me Area_. The subsequent UI shows information about the app including the _App ID_.

The _App ID_ can be used to search for the documentation of the app in the _SAP Fiori reference library_ and it is visible in the header of the documentation.

### Example for Legacy Apps

![Screenshot showing the example of Legacy App (SAP GUI).](https://learning.sap.com/service/media/topic/c7d7cf93-ea46-4331-9545-82deaa55b711/ADM945_24_en-US_media/ADM945_24_en-US_images/ExampleSAPGUIforHTMLApp.png "Screenshot showing the example of Legacy App (SAP GUI).")

Since the release of SAP S/4HANA 1610, SAP GUI for HTML Applications, which are also classic transactions, can be found in the _SAP Fiori reference library_. Due to SAP Fiori 2.0 and the SAP Belize theme, they are an official part of SAP Fiori. The transactions are limited to those targeting end users and those available in SAP S/4HANA 1610 or later.

Hint

The _App ID_ of a transaction is its SAP GUI transaction code.

![Screenshot showing the example of Legacy App (WebDynpro).](https://learning.sap.com/service/media/topic/c7d7cf93-ea46-4331-9545-82deaa55b711/ADM945_24_en-US_media/ADM945_24_en-US_images/ExampleWebDynproApp.png "Screenshot showing the example of Legacy App (WebDynpro).")

Like SAP GUI for HTML Applications, transactional _Web Dynpro ABAP_ applications are also part of SAP Fiori 2.0. All SAP GUI for HTML Applications and _Web Dynpro_ applications are shown as exclusive to the SAP HANA database in the _SAP Fiori reference library_. The reason for this is that the documented release is SAP S/4HANA 1610 or later – and this one is exclusive to the SAP HANA database.

## SAP Fiori App Recommendations Analysis

![Screenshots showing SAP Fiori App Recommendations Logon.](https://learning.sap.com/service/media/topic/ab09f276-36f4-4d11-b341-0f329519bdcf/ADM945_24_en-US_media/ADM945_24_en-US_images/2.3.5_Application_Types_-_SAP_Fiori_App_Recommendations_001.png "Screenshots showing SAP Fiori App Recommendations Logon.")

The _SAP Fiori reference library_ offers recommendations for SAP Fiori apps by analyzing the usage of an existing system landscape. You can start the analysis on the main page by choosing _Get SAP Fiori App Recommendations_. A logon with an SAP user is mandatory.

![Screenshots showing SAP Fiori App Recommendations Analysis.](https://learning.sap.com/service/media/topic/ab09f276-36f4-4d11-b341-0f329519bdcf/ADM945_24_en-US_media/ADM945_24_en-US_images/2.3.5_Application_Types_-_SAP_Fiori_App_Recommendations_002.png "Screenshots showing SAP Fiori App Recommendations Analysis.")

The analysis needs a usage and some system profiles as input:

Usage Profile

A usage profile is a list of the most used transactions in a system. These can be collected based on feedback of end users or by tracing the transactions that are used in the system, for example, by using the _Workload Monitor_ (ST03).

System Profile

A system profile is a list of installed software components in an SAP system. These can be collected using the system information of a system or by using functions of the SAP Solution Manager, for example, the _Landscape Management Database (LMDB)_.

![Screenshot showing SAP Fiori App Recommendations Analysis List View.](https://learning.sap.com/service/media/topic/ab09f276-36f4-4d11-b341-0f329519bdcf/ADM945_24_en-US_media/ADM945_24_en-US_images/2.3.5_Application_Types_-_SAP_Fiori_App_Recommendations_003.png "Screenshot showing SAP Fiori App Recommendations Analysis List View.")

The analysis results in a list of apps with information about their relevance and system requirements depending on the usage and system profiles. The list can be filtered in many ways, for example, by application types, line of business, or roles. Details of each app can be accessed by just clicking on one entry or you can switch from the list view to the detail view, which jumps to a filtered view of the _SAP Fiori reference library_.

## Process Discovery for SAP S/4HANA Transformation

### Business Process Intelligence

Business Process Intelligence is an integrated process management suite that provides you with insights, which then can be transformed into actions. Process Discovery is a free analysis tool to get started with Business Process Intelligence and SAP S/4HANA.

Any successful digital transformation includes the analysis of current business processes, the performance, and the existing gaps. And the SAP’s solution to get these unique insights is a free service – Process Discovery for SAP S/4HANA Transformation.

Process Discovery has evolved from the SAP Business Scenario Recommendations on Spotlight. It is an analysis tool to get you prepared for the SAP S/4HANA Transformation. It is free of charge for every SAP maintenance customer.

Process Discovery is aimed at answering the questions "Why moving to SAP S/4HANA?", "What are the benefits?", "What is different, and what is new?". It also provides information about how SAP can support customers in their transformation journey.

Process Discovery provides customers with unique insights in terms of business process performance and system usage based on data extracted from the ECC (SAP ERP) system. It compares the performance and usage to one of the industry peers, so customers can better understand what topics they want to target first in terms of transformation. It gives tailor-made recommendations based on the insights. This helps to build a business case for moving to SAP S/4HANA and secure the buying from business executives.

The solution helps customers to analyze business processes and understand their current business process performance. The main goal is to automate the business processes and to implement intelligent technologies to support business goals. Also, Process Discovery helps to identify new functionalities from SAP S/4HANA provided by SAP Fiori apps, and also the capabilities of SAP BTP.

![Illustration on Process Discovery.](https://learning.sap.com/service/media/topic/dc8f4fad-94fd-4fad-a1dc-6ded0a04acf5/ADM945_24_en-US_media/ADM945_24_en-US_images/Process_Discovery.png "Illustration on Process Discovery.")

Process Discovery is a combination of two complementary tools:

#### Process Discovery Summary

- interactive PDF for business executives
- provides executive summary
- starting point to build a case for SAP S/4HANA
- gives recommendations

This PDF document is mainly meant to support business executives. It gathers all the information about the SAP S/4HANA content. It provides recommendations that customers can use together with SAP and with the partners to build a business case and leverage the capabilities of SAP S/4HANA.

**Process Discovery Solution** – currently named Spotlight (might be renamed)

- reporting tool as online application
- analyzes process performance and efficiency
- identifies areas for improvement and sees where is potential for automation
- identifies where processes can be standardized

The Process Discovery solution is an online analysis report called _Spotlight_ that is mainly meant for process experts. It helps them prepare to move to SAP S/4HANA, gives recommendations on how to fill the gaps, create innovations, and automations enabled by SAP BTP, or when to design new processes.

![Screenshot showing Process Discovery on Spotlight.](https://learning.sap.com/service/media/topic/dc8f4fad-94fd-4fad-a1dc-6ded0a04acf5/ADM945_24_en-US_media/ADM945_24_en-US_images/Spotlight_Demo_Env.png "Screenshot showing Process Discovery on Spotlight.")

When customers transition form SAP ERP to SAP S/4HANA, they would want to make use of SAP Fiori. They would also want to find out how to improve their existing business processes and what SAP Fiori Apps can be used for that.

Process Discovery on Spotlight can make recommendations based on data from customer's ECC system. The data is extracted via a data extraction report (it requires an implementation of some SAP notes) and loaded into the Spotlight tool.

![Screenshot showing Spotlight App Recommendations.](https://learning.sap.com/service/media/topic/dc8f4fad-94fd-4fad-a1dc-6ded0a04acf5/ADM945_24_en-US_media/ADM945_24_en-US_images/Spotlight_App_Recom.png "Screenshot showing Spotlight App Recommendations.")

It generates a detailed master report how to optimize existing processes, but also gives recommendations which Fiori Apps to use.

Note

_Process Discovery on Spotlight_ is used for scenarios of moving from SAP ERP to SAP S/4HANA and identify the gaps.

There is also another tool called _Pathfinder on Spotlight_ that helps you identifying improvements in your current SAP S/4HANA system.

Access the demo Spotlight environment via this link: [https://demo.spotlight.cloud.sap](https://demo.spotlight.cloud.sap/)

### How to get started with SAP Process Discovery?

On the _Start your Transformation Journey to SAP S/4HANA with Process Discovery_ page [https://www.s4hana.com](https://www.s4hana.com/), you will find instructions how to prepare your ECC system in order to be able to use Process Discovery and how to order the service tool.

Note

Note the request is currently system-specific.

There is as a lot of useful information such as the sample Process Discovery Summary PDF document, which you can download. And, you can also access the online demo environment of the Spotlight solution.

## Practice System Exercise: Explore SAP Fiori Apps Reference Library

Select Start Exercise to start the simulation.

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_66A0FE9DC3EEA195:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

### Business Example

You want to check how many apps are available for SAP S/4HANA 2021. To do so, you want to use SAP Fiori Apps Reference Library.

### Task 1: Open the SAP Fiori Reference Library

Open the SAP Fiori Apps Reference Library, and check how many apps are available for SAP S/4HANA 2021. Explore the Manage G/L Account Master Data (Version 2) app, which is available for a general ledger accountant.

#### Steps

1. In _Google Chrome_, open the SAP Fiori Reference Library.
    
    1. In the _Microsoft Windows_ start menu, choose _Google Chrome_.
        
    2. In _Google Chrome_, go to _Bookmarks_.
        
    3. In _Bookmarks_, choose _SAP Fiori_ → _SAP Fiori Apps Reference Library_.
        
    4. Examine the URL.
        
2. Check how many apps are available for SAP S/4HANA 2021.
    
    1. In the _SAP Fiori Apps Reference Library_, choose _SAP Fiori Apps for SAP S/4HANA_.
        
    2. Choose _All Apps_.
        
        #### Result
        
        The number of SAP Fiori apps for SAP S/4HANA is shown in the header.
        
    3. Choose _Back_.
        
    4. Choose _By Product Version_ to filter the results.
        
    5. Choose _SAP Fiori for SAP S/4HANA 2023_.
        
        #### Result
        
        The number of SAP Fiori apps for SAP S/4HANA is shown in the header.
        
3. Examine which apps are available for an account manager. Don't forget to remove the filters.
    
    1. In the _Search_ field, enter **account manage**.
        
        #### Result
        
        Available apps for an account manager are shown.
        
4. Search for the **Manage G/L Account Master Data (Version 2)** app.
    
    1. In the _Search_ field, enter **Manage G/L Account Master Data (Version 2)**.
        
    2. Choose _Manage G/L Account Master Data (Version 2)_.
        
    3. Below the subtitle, select the release version _SAP S/4HANA 2023_ latest FPS.
        
    4. Select the _IMPLEMENTATION INFORMATION_ tab.
        
    5. Expand _Configuration_.
        
    6. Examine the details.
        

#### Result

The configuration information of the Manage G/L Account Master Data (Version 2) app relevant to SAP S/4HANA 2023 latest FPS is shown.

### Task 2: Optional: Use SAP Fiori App Recommendations

You want to explore which SAP Fiori apps you can use in you SAP S/4HANA system based on the business process executed with SAP GUI transactions. To do so, you want to use SAP Fiori App Recommendations and create an analysis.

This exercise requires an SAP account.

#### Steps

1. Log on SAP Fiori App Recommendations in the SAP Fiori apps reference library using your SAP user.
    
    1. In the Google Chrome favorites, choose _SAP Fiori Apps Reference Library_ in the _SAP Fiori_ folder.
        
    2. On the home page, choose _Get SAP Fiori App Recommendations_.
        
    3. Log on using your SAP account.
        
2. Create a new analysis **Sample Analysis (ADM945)** for the product suite **SAP S/4HANA** using the **Sample Usage Profile (Shared)**.
    
    1. Select _Create new analysis_.
        
    2. Choose _Step 2_.
        
    3. In the _Usage Profile_ field, select **Sample Usage Profile (Shared)** from the dropdown menu.
        
    4. Choose _Step 3_.
        
    5. In the _Analysis for Product Suite_ filed, select **SAP S/4HANA** from the dropdown menu.
        
    6. In the _Back-End System Profile_ field, select **Sample Backend Profile (Shared)** from the dropdown menu.
        
    7. Choose _Step 4_.
        
    8. In the _Analysis Name_ field, enter **Sample Analysis (ADM945)**.
        
    9. In the _Description_ field, enter **Example for ADM945**.
        
    10. Choose _Get SAP Fiori App Recommendations_.
        
3. Filter the list of apps of your analysis by _Application Type__SAP Fiori - Analytical_ and _Role__Accounts Payable Accountant_. Switch to detail view and examine the feedback options.
    
    1. Choose _Application Type_.
        
    2. Select _SAP Fiori - Analytical_ and choose _OK_.
        
    3. Choose _Role_.
        
    4. Select _Accounts Payable Accountant_ and choose _OK_.
        
    5. Choose _Detail View_ at the bottom.
        
    6. Select some apps on the left and display the details.
        
    7. Choose the speech balloons in the lower right corner and review the feedback options.