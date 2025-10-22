Objective

After completing this lesson, you will be able to manage SAP Fiori Spaces and Pages.

## Spaces and Pages for Launchpad Structuring

In newer on-premise releases of SAP S/4HANA, you can start putting together SAP Fiori spaces and pages for your end users, to give them a better SAP Fiori launchpad user experience than available so far with the single home page. This is also a recommended layout structuring for the SAP Fiori Launchpad home page.

![Screenshot showing SAP Fiori Spaces and Pages.](https://learning.sap.com/service/media/topic/f7ea206e-4ed7-4871-a3a5-b4bb9cae53cb/ADM945_24_en-US_media/ADM945_24_en-US_images/03_04_SAP_Spaces_and_Pages.png "Screenshot showing SAP Fiori Spaces and Pages.")

SAP Fiori spaces give you three levels of structuring home page content rather than the one provided by the previous home page approach.

The three levels are:

- Space
- Page
- Section

Users will have one or more spaces that contain one or more pages. The pages show apps clustered in different sections. The spaces mode offers more flexibility to influence the launchpad layout for specific user groups.

Pages are assigned to users via spaces that are assigned to business roles. The business role defines which users see a specific page. If you enable spaces for your users and define specific pages for them, you can reach a better fit. By defining pages with meaningful sections, you can define in which order the apps are sorted on the page.

Hint

You can, for example, sort the most used apps in the top-level section and then create separate sections for apps that belong together. Users can personalize the pages by adding and removing apps.

Spaces are organizational units that combine several pages in a menu that is shown in the navigation bar of the launchpad. They can be assigned to one or more business roles. The pages contain the apps the user works with. When the user clicks on a space in the navigation bar, the first page of the space is shown. The pages then contain the apps for the end users.

SAP delivers spaces and pages for many business roles for SAP S/4HANA 2020, which you can use to get examples of how to structure spaces for these roles, as well as for trying it out in test systems. When you work with your own business roles and catalogs, we recommend that you create your own spaces and pages from scratch.

Note

The classic home page layout with SAP Fiori groups remains possible and can be used in parallel.

## Tools for Managing Spaces and Pages

![Screenshot showing tools for managing spaces and pages.](https://learning.sap.com/service/media/topic/a87eb8b5-c910-45ac-ac01-18ef609fa379/ADM945_24_en-US_media/ADM945_24_en-US_images/03_04_Tools_for_Spaces_and_Pages.png "Screenshot showing tools for managing spaces and pages.")

To manage launchpad structure and layout using spaces and pages, administrators use SAP Fiori apps _Manage Launchpad Spaces_ and _Manage Launchpad Pages_.

With _Manage Launchpad Spaces_ app, administrators can create and manage spaces for the SAP Fiori launchpad. Spaces are organizational units that combine several pages. The pages then contain the apps for the end users. This is how the layout of the SAP Fiori launchpad home screen can be structured. The _Manage Launchpad Spaces_ app provides an overview showing all spaces available in your launchpad and a detailed view for the spaces.

With _Manage Launchpad Pages_ app administrators can create the launchpad pages, define the layout of pages and edit, copy or delete existing pages.

Also, the functionality of the role maintenance (transaction **PFCG**) has been extended. It is now possible to add _Launchpad Spaces_ to the role menu.

Hint

To access these tools, authorization role **SAP_FLP_ADMIN** needs to be assigned to you.

## Creating Spaces with Manage Launchpad Spaces App

There are several possible sequences to create spaces and pages and make them available for users. The recommended sequence if launchpad content creation and role maintenance are separated, is the so called bottom up approach. This means that spaces and pages are created first, and then they are assigned to roles in role maintenance.

With the _Manage Launchpad Spaces_ app you can create and manage spaces for the SAP Fiori launchpad. With spaces you can design the launchpad layout. Spaces are organizational units that combine several pages in a menu that is shown in the navigation bar of the launchpad. They can be assigned to one or more business roles. The pages contain the apps the user works with. A space is shown in the navigation bar of the launchpad. When you click on it, the first page of the space is shown. The pages then contain the apps for the end users. The _Manage Launchpad Spaces_ app provides an overview showing all spaces available in your launchpad and a detailed view for the spaces.

![Screenshowt showing the steps to create own space and page with Manage Launchpad Spaces app.](https://learning.sap.com/service/media/topic/b7b51562-ee4d-4875-951b-084851cb7348/ADM945_24_en-US_media/ADM945_24_en-US_images/03_04_Create_Own_Space.png "Screenshowt showing the steps to create own space and page with Manage Launchpad Spaces app.")

1. Open the _Manage Launchpad Spaces_ app.
2. Select _Create_ and add the space information for the new space.
    
    Enter a unique space ID, a description and a title for the space. All three entries are mandatory.
    
    Note
    
    The space ID has to start with a Z or a Y (Y should only be used for spaces designed by SAP partners). Note that you cannot change the space ID anymore. The space title will be shown in the navigation bar.
    
3. Select the option _Also Create a Page_ and enter the page information.
    
    Enter a page ID, a description and a title for the page. All three entries are mandatory. The page ID must be unique, and it has to start with a Z or a Y (Y should only be used for pages designed by SAP partners). The title will be shown as a menu item in the space menu.
    
4. Depending on your system configuration, you need to enter a transport. You can check the transport assignment of a space in the _Transport_ tab of the _Space Details_ view in the _Manage Launchpad Spaces_ app.
    
    Note
    
    The space is not locked after it was assigned to a transport. A space can be assigned to several transports.
    
5. Choose _Create_. The space details are displayed. The _Pages_ tab shows the newly created, empty page. Here you can add further pages.
    
    Hint
    
    You could now start editing the page by adding apps from business catalogs. However, the recommended way is to establish a role context for space and page. This means, the space is assigned to a business role and only apps that are authorized by the business role should be added to the pages of a space. This is done in transaction **PFCG**.
    

![Screenshots on adding space to Role Menu.](https://learning.sap.com/service/media/topic/b7b51562-ee4d-4875-951b-084851cb7348/ADM945_24_en-US_media/ADM945_24_en-US_images/03_04_Establish_role_context.png "Screenshots on adding space to Role Menu.")

1. In _Role Maintenance_ (transaction **PFCG**), create a new role or edit an existing one.
2. Go the _Menu_ tab.
3. Choose the context menu of the transaction button and select _SAP Fiori_ → _Launchpad_ → _Launchpad Space_.
4. Enter a space ID. You can use the value help for this.
    
    The space ID is the name that you provided when creating the space in the _Manage Launchpad Spaces_ app.
    
    By adding the defined space to a role you make it available for all users with this role.
    
5. Save the role.

## Creating and Editing Pages with Manage Launchpad Pages App

You create and edit pages with _Manage Launchpad Pages_ app. In the app, you also define the layout of pages and edit, copy, or delete existing pages.

When you open the _Manage Launchpad Pages_ app, you can access customer-created or SAP-delivered pages in your system.

1. On _Customer-Created_ tab, choose _Create_ to create a custom page.
2. For newly created pages, enter the page information.
    
    Enter a page ID, a description and a title for the page. All three entries are mandatory.
    
    Note
    
    The page ID must be unique, and it has to start with a Z or a Y (Y should only be used for pages designed by SAP partners). The title will be shown as a menu item in the space menu.
    
3. Depending on your system configuration, you need to enter a transport. The transport assignment of a page is shown in the _Transport_ tab of the _Page Details_ view in the _Manage Launchpad Pages_ app.
    
    Note
    
    The page is not locked after it was assigned to a transport. A page can be assigned to several transports.
    
4. Click on _Create_ to generate the page.
    
    An empty page is displayed in the edit page view.
    
    Note
    
    A page always has to be assigned to a space to make it available to users. If you have created a page from scratch, you need to assign it to the space in the _Manage Launchpad Spaces_ app.
    
5. Assign the page to a space.

![Screenshots on editing page with Manage Launchpad Pages app.](https://learning.sap.com/service/media/topic/f4637923-937b-4da7-b0ab-3198b4ec7ae0/ADM945_24_en-US_media/ADM945_24_en-US_images/03_04_Edit_Page.png "Screenshots on editing page with Manage Launchpad Pages app.")

If you have already created a page and it is assigned to a space, you can edit it in the _Manage Launchpad Pages_ app.

1. Choose _Edit_ (pencil icon) to open the edit mode.
2. On the _Page Content_ tab, you will find a first empty section in the page, which requires a title. Enter a meaningful name for it.
    
    You can add more sections to one page according to your needs.
    
3. You can add apps from the tile catalogs to the sections by choosing _Catalogs_.
    
    Hint
    
    However, if you have defined the role context by assigning the space where the page is in to a business role, you will be able to see all the app tiles from the catalogs inside a role. This prevents from adding tiles to a page that the end user is not authorized to see and thus from potential issues.
    
4. You can also select several apps by ticking the boxes in front of each app title. When you have selected all apps you want to assign to a section, click on _Add_ or simply drag and drop the app tiles to the section.
5. Save your changes.

#### Page Visibility

After you have set up all the pages for a space, go to the _Manage Launchpad Spaces_ app and set the pages visible.

![Screenshot on setting pages visible.](https://learning.sap.com/service/media/topic/f4637923-937b-4da7-b0ab-3198b4ec7ae0/ADM945_24_en-US_media/ADM945_24_en-US_images/03_04_Page_Visibility.png "Screenshot on setting pages visible.")

Until then, the page visibility will remain hidden. This means, that even if the end user has got the roles assigned that contains a space, he or she would not be able to see the pages and any app tiles on the SAP Fiori Launchpad home screen.

## Practice System Exercise: Create Spaces and Pages

Select Start Exercise to start the simulation.

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_6E5B7DFD8EDA43A8:uebung)

Note

If you have access to a practice system, you can now execute this exercise.

To enable end-users to display tiles on the home screen of the SAP Fiori Launchpad, you want to create SAP Fiori spaces with corresponding pages and include them into an existing PFCG role.

In this exercise, you want to create two different SAP Fiori spaces according to the two different job profiles: accounting manager and inventory manager.

And you will also include pages into the spaces:

- Space ID: **Z_ADM945_##_SP_FIN_ACCOUNT**
    
    - Page ID: **Z_ADM945_##_PG_ACCOUNT**
        
    - Page ID: **Z_ADM945_##_PG_BANK_MGMT**
        
- #### Z_ADM945_##_SP_INVENT_MGMT
    
    Page ID: **Z_ADM945_##_PG_INVENT_MGMT**
    

Note

In this exercise, when an object name or value contains ##, replace ## by the number your trainer assigned to you.![Illustration on ADM945: Roles and Spaces Overview.](https://learning.sap.com/service/media/topic/d326e24c-c03a-44cb-8e8b-e6f7a3da5359/ADM945_24_en-US_media/ADM945_24_en-US_images/ADM945_Roles_Spaces_Overview.png "Illustration on ADM945: Roles and Spaces Overview.")

### Task 1: Create SAP Fiori Space for Accounting Manager

You want to create an SAP Fiori Launchpad space for an accounting manager.

#### Steps

1. Log on to SAP Fiori Launchpad of system S4D with your **train-##** user. Use Google Chrome.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. In the _Microsoft Windows_ start menu, choose _Google Chrome_.
        
    2. In _Google Chrome_, go to _Bookmarks_.
        
    3. In _Bookmarks_, choose _10 Development_ → _s4dhost_ → _10 S4D SAP Fiori Launchpad_.
        
        Note
        
        Since SAP S/4HANA 2020 new tools for creating spaces and pages have been introduced. To access those tools, you as an administrator need to have the relevant authorizations that are provided by SAP-delivered role **SAP_FLP_ADMIN**. After you got this, you will see the relevant tools in SAP Fiori Launchpad.
        
2. Start _Manage Launchpad Spaces_ app rom the _Fiori Launchpad_ space and create an SAP Fiori Launchpad space for accounting manager. Use the following data:
    
    Note
    
    The space ID must start with Z or Y and must be unique. It can contain up to 32 characters but must not contain any special characters.
    
    |Field|Value|
    |---|---|
    |_Space ID_|**Z_ADM945_##_SP_FIN_ACCOUNT**|
    |_Space Description_|any feasible description|
    |_Space Title_|**Financial Accounting Space ##**|
    
    1. On the SAP Fiori Launchpad home screen, choose the _Fiori Launchpad_ space.
        
    2. Launch the _Manage Launchpad Spaces_ app.
        
    3. Choose _Create_.
        
    4. In the _Create Space_ dialog window, enter the following information for the space:
        
        |Field|Value|
        |---|---|
        |_Space ID_|**Z_ADM945_##_SP_FIN_ACCOUNT**|
        |_Space Description_|any feasible description|
        |_Space Title_|**Financial Accounting Space ##**|
        
3. Assign a customizing transport request that you have already created in the catalog exercise.
    
    Note
    
    The transport request is displayed in the drop-down menu only if you are the owner of it or you have been assigned as user to it.
    
    1. In the _Create Space_ dialog window, choose the field _Transport_.
        
        #### Result
        
        The customizing transport request that you created in system S4D before is displayed.
        
    2. Select the transport request from the drop-down menu.
        
4. Choose _Create_.
    
5. Choose _SAP_ logo to get back to the FLP home screen.
    

### Task 2: Create SAP Fiori Pages for Accounting Manager

In the _Financial Accounting Space ##_, you want to include two pages that later will contain tiles to reflect typical tasks of an accounting manager.

#### Steps

1. On the FLP home screen, from the space _Fiori Launchpad_ start _Manage Launchpad Pages_ app and create two SAP Fiori Launchpad pages for accounting manager. Use the following data:
    
    Note
    
    The space ID must start with Z or Y and must be unique. It can contain up to 32 characters but must not contain any special characters.
    
    #### Page 1
    
    - _Page ID_: **Z_ADM945_##_PG_ACCOUNT**
    - _Page Description_:
        
        any feasible description
        
    - _Page Title_: **Accounting Page ##**
    
    #### Page 2
    
    - _Page ID_: **Z_ADM945_##_PG_BANK_MGMT**
    - _Page Description_:
        
        any feasible description
        
    - _Page Title_: **Bank Management Page ##**
    
    1. On the home screen of the SAP Fiori Launchpad, choose _Fiori Launchpad_ space.
        
    2. Launch the _Manage Launchpad Pages_ app.
        
    3. Choose _Create_ to create the first page.
        
    4. In the _Create Page_ dialog window, enter the following information for the space:
        
        |Field|Value|
        |---|---|
        |_Page ID_|**Z_ADM945_##_PG_ACCOUNT**|
        |_Page Description_|any feasible description|
        |_Page Title_|**Accounting Page ##**|
        
2. Assign a customizing transport request that you have already created in the catalog exercise.
    
    Note
    
    The transport request is displayed in the drop-down menu only if you are the owner of it or you have been assigned as user to it.
    
    1. In the _Create Space_ dialog window, choose the field _Transport_.
        
        #### Result
        
        The customizing transport request that you created in system S4D before is displayed. Choose it.
        
3. Choose _Create_.
    
4. Choose _Back_ to get to the _Customer-Created_ pages overview and create the second page.
    
    1. Choose _Create_ to create the second page.
        
    2. In the _Create Page_ dialog window, enter the following information for the space:
        
        |Field|Value|
        |---|---|
        |_Page ID_|**Z_ADM945_##_PG_BANK_MGMT**|
        |_Page Description_|any feasible description|
        |_Page Title_|**Bank Management Page ##**|
        
5. Assign a customizing transport request that you have already created in the catalog exercise.
    
    Note
    
    The transport request is displayed in the drop-down menu only if you are the owner of it or you have been assigned as user to it.
    
    1. In the _Create Space_ dialog window, choose the field _Transport_.
        
        #### Result
        
        The customizing transport request that you created in system S4D before is displayed. Choose it.
        
6. Choose _Create_.
    
7. Assign both pages to the _Z_ADM945_##_SP_FIN_ACCOUNT_ space.
    
    1. Choose _SAP_ logo to return to the FLP home screen.
        
    2. Start _Manage Launchpad Spaces_ app.
        
    3. Select _Z_ADM945_##_SP_FIN_ACCOUNT_ space.
        
    4. Choose _Edit_ (pencil button).
        
    5. In the _Search for pages_ field, search for the two pages that you have created. Enter **ADM945_##** to find specifically your pages.
        
    6. Choose _Add_ for both pages.
        
    7. In the bottom right corner, choose _Save_.
        
    8. Choose _SAP_ logo to return to the FLP home screen.
        

### Task 3: Create SAP Fiori Space and Page for Inventory Manager

You want to create an SAP Fiori Launchpad space for an inventory manager. In the space, you want to include one page that later will contain tiles to reflect typical tasks of an inventory manager.

#### Steps

1. Start _Manage Launchpad Spaces_ app and create an SAP Fiori Launchpad space for inventory manager. Use the following data:
    
    Note
    
    The space ID must start with Z or Y and must be unique. It can contain up to 32 characters but must not contain any special characters.
    
    |Field|Value|
    |---|---|
    |_Space ID_|**Z_ADM945_##_SP_INVENT_MGMT**|
    |_Space Description_|any feasible description|
    |_Space Title_|**Inventory Management Space ##**|
    
    1. On the FLP home screen, from the space _Fiori Launchpad_ start _Manage Launchpad Spaces_ app.
        
    2. Choose _Create_.
        
    3. In the _Create Space_ dialog window, enter the following information for the space:
        
        |Field|Value|
        |---|---|
        |_Space ID_|**Z_ADM945_##_SP_INVENT_MGMT**|
        |_Space Description_|any feasible description|
        |_Space Title_|**Inventory Management Space ##**|
        
2. Since you will have only one page in the space, choose the option to create the page right away. Enter the following data:
    
    Note
    
    The page ID must start with Z or Y and must be unique. It can contain up to 32 characters but must not contain any special characters.
    
    |Field|Value|
    |---|---|
    |_Page ID_|**Z_ADM945_##_PG_INVENT_MGMT**|
    |_Page Description_|any feasible description|
    |_Page Title_|**Inventory Management Page ##**|
    
    1. Since it is going to be only one page in the space, set a flag in _Also create a page_ to create the page in the space.
        
    2. In the _Create Space_ dialog window, enter the following information for the page:
        
        |Field|Value|
        |---|---|
        |_Page ID_|**Z_ADM945_##_PG_INVENT_MGMT**|
        |_Page Description_|any feasible description|
        |_Page Title_|**Inventory Management Page ##**|
        
3. Assign a customizing transport request that you have already created in the catalog exercise.
    
    Note
    
    The transport request is displayed in the drop-down menu only if you are the owner of it or you have been assigned as user to it.
    
    1. In the _Create Space_ dialog window, choose the field _Transport_.
        
        #### Result
        
        The customizing transport request that you created in system S4D before is displayed. Choose it.
        
4. Choose _Create_.
    

## Assign SAP Fiori Spaces to PFCG Roles

Select Start Exercise to start the simulation.

Exercise[Start Exercise](https://learnsap.enable-now.cloud.sap/pub/mmcp/index.html?show=project!PR_960EFA452D5DAE9F:uebung)

## Practice System Exercise: Assign SAP Fiori Spaces to PFCG Roles

### Task 1: Assign Spaces to Business Roles

Note

If you have access to a practice system, you can now execute this exercise.

You want to assign your custom-spaces to business roles ADM945_##_BR_FINANCIALS and ADM945_##_BR_INVENTORY so that the pages are available for the **ADM945-##** user with those business roles.

#### Steps

1. Log on to the SAP GUI of the system S4D.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. Choose _SAP Logon_.
        
    2. Select _10 Development_ → _S4D SAP GUI non-SNC [PAS]_.
        
    3. Choose _Log On_.
        
2. Assign _Z_ADM945_##_SP_FIN_ACCOUNT_ space to the _ADM945_##_BR_FINANCIALS_ role.
    
    1. In system S4D, start the role maintenance (transaction PFCG).
        
    2. In the _Role_ field, enter **ADM945_##_BR_FINANCIALS**.
        
    3. Choose _Change_.
        
    4. Go to the _Menu_ tab.
        
    5. In the context menu of the _Transaction_ button, choose _SAP Fiori Launchpad_ → _Launchpad Space_.
        
    6. In the _Space ID_ field, use the value help (F4) and search for the **Z_ADM945_##_SP_FIN_ACCOUNT** space.
        
    7. Choose _Save_ in the lower right-hand corner.
        
    8. Choose _Back (F3)_.
        
3. Assign _Z_ADM945_##_SP_INVENT_MGMT_ space to the _ADM945_##_BR_INVENTORY_ role.
    
    1. Back on the _Role Maintenance_ screen, in the _Role_ field, enter **ADM945_##_BR_INVENTORY**.
        
    2. Choose _Change_.
        
    3. Go to the _Menu_ tab.
        
    4. In the context menu of the _Transaction_ button, choose _SAP Fiori Launchpad_ → _Launchpad Space_.
        
    5. In the _Space ID_ field, use the value help (F4) and search for the **Z_ADM945_##_SP_INVENT_MGMT** space.
        
    6. Choose _Save_ in the lower right-hand corner.
        
    7. Choose _Cancel_.
        
    8. Choose _Back (F3)_.
        

### Task 2: Edit Page Content

You want to edit page content and add apps to it to reflect typical tasks of business roles.

#### Steps

1. Log on to SAP Fiori Launchpad of system S4D with your **train-##** user. Use Google Chrome.
    
    |Field|Value|
    |---|---|
    |_User_|**train-##**|
    |_Password_|Custom password|
    
    1. In the _Microsoft Windows_ start menu, choose _Google Chrome_.
        
    2. In _Google Chrome_, go to _Bookmarks_.
        
    3. In _Bookmarks_, choose _10 Development_ → _s4dhost_ → _10 S4D SAP Fiori Launchpad_.
        
        Note
        
        Since SAP S/4HANA 2020 new tools for creating spaces and pages have been introduced. To access those tools, you as an administrator need to have the relevant authorizations that are provided by SAP-delivered role **SAP_FLP_ADMIN**. After you got this, you will see the relevant tools in SAP Fiori Launchpad.
        
2. In the _Manage Launchpad Pages_ app, create a **Quick Access** section for the **Z_ADM945_##_PG_ACCOUNT** page.
    
    1. On the SAP Fiori Launchpad home screen, choose the _Fiori Launchpad_ space.
        
        If you want to work with groups, you can deactivate the space usage in the user settings. Then you will find the admin tools in the _Fiori Launchpad_ group.
        
    2. Launch _Manage Launchpad Pages_ app.
        
    3. Select _Z_ADM945_##_PG_ACCOUNT_.
        
    4. Choose _Edit_ (pencil icon).
        
    5. Enter a _Section Title_**Quick Access**.
        
3. Add the tiles of the _Display G/L Account Balances_ app and _Display G/L Account Balances - For Ledger_ app to the _Quick Access_ section.
    
    1. In the _Derived from Roles_ section on the right-hand side, choose _Add_ for the _Display G/L Account Balances_ app.
        
        #### Result
        
        The tile is added to the _Quick Access_ section.
        
    2. In the _Derived from Roles_ section on the right-hand side, choose _Add_ for the _Display G/L Account Balances - For Ledger_ app.
        
        #### Result
        
        The tile is added to the _Quick Access_ section.
        
    3. Choose _Save_ ind the lower right-hand corner.
        
    4. Choose _Back_.
        
4. In the _Manage Launchpad Pages_ app, create a **Quick Access** section to the **Z_ADM945_##_PG_BANK_MGMT** page.
    
    1. From the list of custom-created pages, select _Z_ADM945_##_PG_BANK_MGMT_.
        
    2. Choose _Edit_ (pencil icon).
        
    3. Enter a _Section Title_:**Quick Access**.
        
5. Add the tile of the _Manage Banks_ app to the _Quick Access_ section.
    
    1. In the _Derived from Roles_ section on the right-hand side, choose _Add_ for the _Manage Banks_ app.
        
        #### Result
        
        The tile is added to the _Quick Access_ section.
        
    2. Choose _Save_ in the lower right-hand corner.
        
    3. Choose _Back_.
        
6. In the _Manage Launchpad Pages_ app, create two sections **Overview** and **Analysis** to the **Z_ADM945_##_PG_INVENT_MGMT** page.
    
    1. On the home screen of the SAP Fiori Launchpad for system S4D, launch _Manage Launchpad Pages_ app.
        
    2. Select _Z_ADM945_##_PG_INVENT_MGMT_.
        
    3. Choose _Edit_ (pencil icon).
        
    4. Enter a _Section Title_:**Overview**.
        
    5. Choose _+ Add Section_ to create a second section in the page.
        
    6. Enter a _Section Title_:**Analysis**.
        
7. Add the tile of the _Material Documents Overview_ app to the _Overview_ section.
    
    1. In the _Derived from Roles_ section on the right-hand side, drag and drop the _Material Documents Overview_ app to the _Overview_ section.
        
        #### Result
        
        The tile is added to the _Overview_ section.
        
8. Add the tile of the _Physical Inventory Analysis_ app to the _Analysis_ section.
    
    1. In the _Derived from Roles_ section on the right-hand side, drag and drop the _Physical Inventory Analysis_ app to the _Analysis_ section.
        
        #### Result
        
        The tile is added to the _Analysis_ section.
        
    2. Choose _Save_ in the lower right-hand corner.
        
    3. Choose _SAP_ logo to return to the FLP home screen.
        

### Task 3: Log on to the SAP Fiori Launchpad and Examine Spaces and Pages

You want to log on to the SAP Fiori Launchpad with**ADM945-##** test user you created in an exercise before and you want to review if the SAP Fiori spaces and pages that include the apps that are displayed on the FLP home screen.

#### Steps

1. If you have already logged off, log on to the SAP Fiori Launchpad in Mozilla Firefox once again. If not, refresh the home page.
    
    Hint
    
    We do not recommend that you use _Google Chrome_ since you have already logged in to the SAP Fiori Launchpad with your **train-##** user there. To avoid logging off, you can use any other browser in the training landscape to start the SAP Fiori Launchpad if you know the URL. Mozilla Firefox is only a suggestion. However, there you will find all necessary bookmarks.
    
    1. In the _Microsoft Windows_ start menu, choose _Mozilla Firefox_.
        
    2. In _Bookmarks_, choose _10 Development_ → _s4dhost_ → _10 S4D SAP Fiori Launchpad_.
        
    3. Enter the following data:
        
        |Field|Value|
        |---|---|
        |_User_|**ADM945-##**|
        |_Password_|Custom password|
        
    4. Choose _Log On_.
        
    5. Examine the SAP Fiori Launchpad home screen.
        
    
    #### Result
    
    You see the home page layout with the SAP Fiori Spaces ans Pages.
    
2. Enable the spaces for your user via user settings.
    
    1. On the FLP home screen, go to the user-action menu.
        
    2. Choose _Settings_.
        
    3. In the _Settings_ window, go to _Spaces and Pages_.
        
    4. Set the flag in _Use Spaces_.
        
    5. Choose _Save_.
        
    
    #### Result
    
    The page has been refreshed. The layout is now changed. You landed in the _My Home_ space. However, you can see the spaces and by opening the drop-down menu the pages. You can switch between the _Inventory Management Space ##_ and the _Financial Accounting Space ##_.