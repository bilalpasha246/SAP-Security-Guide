Composite Roles
It is often necessary to describe a work center using more than one single role and the information stored within it about menu structure, authorization data, and user assignments. To simplify maintenance and improve reusability, it is also possible to modularize a work center using several roles, which are then combined in a composite role. This possibility simplifies user administration and makes it easier for the company's HR team or Support department to assign authorizations.![[Pasted image 20251009101924.png]]

Advantages of Composite Roles
- One work center
- One composite role
- One assignment
- One central menu

This container can contain any content. For reasons of clarity, it does not make sense and is therefore not possible to add composite roles to composite roles.

![[Pasted image 20251009102021.png]]

#### Disadvantages of Composite Roles

Since composite roles are only a shell for combined roles, they do not have **any authorization data** themselves.

Creating composite roles makes sense if some of your employees need authorizations from several roles. Instead of adding each user separately to each role required, you can set up a composite role and assign it to the users of that group.

The users assigned to a composite role are automatically assigned to the corresponding (elementary) roles during the comparison. The contents of the composite roles are automatically resolved and the single roles contained in them are entered.

In the master record, the assigned composite roles are displayed as usual, but the associated roles are displayed with "_blue text on a gray background_". These fields cannot be changed. The user assignment can only be changed through the composite role.
![[Pasted image 20251009102106.png]]

If you assign a number of single roles to a user, multiple listings of individual menu entries can occur. For example, if a transaction or a path that is contained in role 1 **and** in role 2, it appears twice. The user menu then contains more than one entry for menu nodes, and frequently confuses end users.

The menu tree of a composite role is, in the simplest case, a combination of the menus of the roles contained. When you create a new composite role, the initial menu tree is empty at first. You can build the menu tree with the menus of the integrated roles by choosing "_Read menu_" (_Menu_ tab page).

1. Menu displays more than the composite role authorizes.
    
    If the combination of a role reduces (previously read and used in a composite role), this has, of course, consequences for the existing menu tree. In such a case, Role Maintenance allows you to completely rebuild the menu tree or process only the changes. If you choose the latter option, Role Maintenance removes all items from the entire menu, which are no longer contained in any of the roles referenced.
    
2. Menu displays less than the composite role authorizes.
    
    If the contents of the assigned roles are extended (menu or authorizations change), these are not automatically visible in the composite role menu.
    
    If you want to change the authorizations (that are represented by a composite role), you must maintain the data for each role of the composite role.


There are two possibilities in role maintenance for the structure of the menu:

1. If the composite role menu has never yet been built, when you choose _Read menu_, every menu of the single roles that have been assigned is immediately imported.
2. However, if it is a _Refresh_, an additional query appears (see the next presentation slide).

![[Pasted image 20251009102418.png]]
You can now choose between _Merge_ and _Reimport_. If you want to discard your settings and restructure the menu, choose _Reimport_. _Merge_, on the other hand, creates a delta between the "actual" situation and the situation as it "ought" to be. This delta describes the change set.

- **Reduction**: In this case, the transactions that no longer appear in the roles are removed from the menu of the composite role. Empty folders may be created. These are displayed in _red_, and you can delete them manually or by choosing _Delete Empty Folders_.

- **Extension**: Those transactions which now additionally appear in the roles are added. You can find these transactions in a separate folder with the description _New menu options_. You can then distribute these to the menu manually. Single roles that have been newly added to the composite role are added with their hierarchy, while transactions from single roles already contained in the composite role are included with no hierarchy.