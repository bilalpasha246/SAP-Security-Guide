## Derived Role Strategy

In practice, there are a number of requirements to create roles whose content differs only in the authorizations and not in the transactions. For example: two sales and distribution employees with the same work center description, but different plants (1000 and 2000). Here are two useful examples for the use of _derived roles_.

1. The menu of the roles is to be identical, but the authorizations for the actions contained in the menu are reassigned in the derived role.
    
2. The menu and the authorizations of the derived role are to be identical, but the organizational units are reassigned in the derived role.
    

The relationships are described in detail on the following pages, and you can see that these roles can be created and maintained very elegantly.![[Pasted image 20251009102746.png]]

Derived roles refer to roles that already exist. The derived roles inherit the menu structure and the functions included (transactions, reports, Web links, and so on) from the referenced role.

### Comparison from the Imparting Role

"_Generate Derived Roles_" button

This action usually copies the **normal fields** (not the organizational levels) to all derived roles and generates the profiles.
### Comparison from the Derived Role

"_Transfer Data_" button

This button is usually used for the "_initial fill_" of the authorizations. This call always copies all general authorization values from the template. If an organizational level in the derived role is not filled, it is also set to the value from the reference role.![[Pasted image 20251009102924.png]]
Unlike composite roles, the derived role has the complete filled menu of the template immediately after the referencing role is entered and the role is saved. The inherited menus **cannot be changed** in the derived roles.

