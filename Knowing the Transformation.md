

Objective

After completing this lesson, you will be able to describe the concept of transformations.

## Transformations - Overview

Maintain the transformation logic, which corresponds to the structure and logic of your systems.

### Overview

For every system supported by the Identity Provisioning service, there is an initial (default) transformation logic that converts the system-specific JSON representation of the entities from/to one common JSON. You can see it on the _Transformations_ tab when you create a new system, after saving it. You can adjust the transformation mapping rules to reflect the current setup of entities from the source or target system.

### How It Works

During the provisioning job, the source system reads its entities, and then using the configured read transformation, converts the source system-specific JSON to the common JSON format. This common JSON format is then passed to the target system, which applies the write transformation.

The administrator of the Identity Provisioning service can change this behavior by adapting the transformation logic to only read the entities that should be provisioned to the target system. This filter can speed up the processing of the entities and their provisioning to the target system.

### Transformation Editors

The Identity Provisioning service provides two editors for working with the transformation code: graphical editor and JSON (text) editor. The graphical editor is displayed by default.

## Parameterized System Transformations

They use parameters taken from the system property sets. The parameters consist of a _unique key_ and a _value_. Like the standard properties, they can be configured in the system's _Properties_ tab and/or in the system's destination properties (in the platform cockpit). When one parameter exists in both property sets, the system properties have priority over the system destination properties.

In the JSON data, the unique key of one of these parameters is surrounded by the percent symbol (%). During the transformation evaluation, each occurrence of **%<...>%** is replaced by the corresponding parameter's value. Parameter references without a value are left unchanged – for example:

#### Examples

|**LDAP parameters – list**|**LDAP parameters – mapping transformation**|
|---|---|
|ldap.attribute.user.mail=mail|#### Sample Code<br><br>Code Snippet<br><br>Copy codeSwitch to dark mode<br><br>```<br><br>/* LDAP Server (source) system: */<br><br>{<br>                "sourcePath": "$.%ldap.attribute.user.mail%[0]",<br>                "targetPath": "$.emails[0].value",<br>                "optional": true<br>            },<br><br><br><br>            {<br>                "sourcePath": "$.%ldap.attribute.user.givenName%[0]",<br>                "targetPath": "$.name.givenName",<br>                "optional": true<br>            },<br><br>```|
|ldap.attribute.user.givenName=givenName|
|ldap.attribute.user.groups=memberOf|

## Internal Properties

Note

Identity Provisioning uses internal properties in various cases. Customers must not use internal properties.

An example of this is shown in the following table:

#### Example

|**Property Name**|**Value**|
|---|---|
|destinationName|The name of the destination created in SAP BTP cockpit|

## Transformation Types

Learn about the types of JSON transformations that are needed for the provisioning jobs.

### Context

Two types of transformations occur before the provisioning of entities:

1. **Read Transformation** – from the source system to the provisioning framework. It reads the data in the source system and transfers it to the intermediate JSON data in the provisioning framework. The reading of entities from the source system can be complete (full read) or partial (delta read).
2. **Write Transformation** – from the provisioning framework to the target system. It prepares the data to be written to the target system.

Both transformations result in JSON data.

![The flowchart shows the data transformation process. The source system connects to the provisioning network, reading the data. The provisioning framework connects to the target system, writing the data.](https://learning.sap.com/service/media/topic/f41bebfe-d4cd-47a8-b3c7-97f33a5d7014/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Transformation_scr.png "The flowchart shows the data transformation process. The source system connects to the provisioning network, reading the data. The provisioning framework connects to the target system, writing the data.")

Every supported system holds and requires specific JSON data. To convert the source JSON data to an intermediate JSON version (which can be used for transformation to a supported target system), the Identity Provisioning administrator can use the suggested JSON transformation logic on the _Transformations_ tab and adapt it to the required transformation.

All transformations from the source systems transform their specific JSON data to intermediate data according to the _System for Cross-domain Identity Management_ (SCIM 2.0) specification.

Note

**Proxy systems** contain both _Read_ and _Write_ transformations.

## Transformation Examples

The following example explains how transformations work.

### Basic Transformation

The basic transformation copies all attributes from the input JSON messages to the output JSON ones.

Code Snippet

Copy codeSwitch to dark mode

```
{
      "sourcePath": "$",
      "targetPath": "$"
},
```

## Source, Intermediate, and Target Data

In this example, the source system JSON data contains the **sn[0]** attribute.

The read transformation converts this attribute to **name.familyName** in the intermediate JSON data. Then, the write transformation reads the **name.familyName** attribute and maps it to **name.familyName** in the target system.

### Source Entity Data (from Microsoft Active Directory)

Code Snippet

Copy codeSwitch to dark mode

```
{
        "sAMAccountName": ["jsmith"],
        "mail": ["john.smith@company.com"],
        "givenName": ["John"],
        "sn": ["Smith"],
        "memberOf": ["group1"],
        "memberOf_2": ["group21", "group22"],
        "memberOf_3": ["group31", "group32", "group33"]
}
```

### Read Transformation (Intermediate JSON Data)

Code Snippet

Copy codeSwitch to dark mode

```

{
    "user": {
        "mappings": [

...

            {
                "sourcePath": "$.%ldap.attribute.user.id%[0]",
                "targetVariable": "entityIdSourceSystem",
                "correlationAttribute": true
            },
            {
                "condition": "('%ldap.attribute.user.id%' == '%ldap.attribute.dn%')",
                "constant": "",
                "targetVariable": "nestedPathRegex",
                "functions": [
                    {
                        "function": "concatString",
                        "prefix": "(?i)cn=.*?,(.*?)",
                        "suffix": ",%ldap.user.path%"
                    }
                ]
            },
            {
                "condition": "('%ldap.attribute.user.id%' == '%ldap.attribute.dn%')",
                "sourcePath": "$.%ldap.attribute.user.id%[0]",
                "targetPath": "$['urn:sap:cloud:scim:schemas:extension:ad:2.0:User']['nestedPath']",
                "functions": [
                    {
                        "function": "getMatchedRegexGroup",
                        "regex": "${nestedPathRegex}",
                        "groupIndex": 1
                    }
                ],
                "defaultValue": ""
            },
            {
                "sourcePath": "$.sAMAccountName[0]",
                "targetPath": "$.userName",
                "correlationAttribute": true
            },
            {
                "sourcePath": "$.displayName[0]",
                "optional": true,
                "targetPath": "$.displayName"
            },
            {
                "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
                "targetPath": "$.schemas[0]"
            },
            {
                "sourcePath": "$.mail[0]",
                "optional": true,
                "targetPath": "$.emails[0].value",
                "correlationAttribute": true
            },
            {
                "sourcePath": "$.givenName[0]",
                "optional": true,
                "targetPath": "$.name.givenName"
            },
            {
                "sourcePath": "$.sn[0]",
                "optional": true,
                "targetPath": "$.name.familyName"
            },
            {
                "sourcePath": "$.memberOf",
                "preserveArrayWithSingleElement": true,
                "optional": true,
"targetPath": "$.groups[?(@.value)]"
},

...
```

### Write Transformation (Intermediate JSON Data)

Code Snippet

Copy codeSwitch to dark mode

```

{
    "user": {
        "condition": "($.emails.length() > 0) && ($.name.familyName EMPTY false)",
        "mappings": [
            {
                "sourcePath": "$.groups",
                "preserveArrayWithSingleElement": true,
                "optional": true,
                "targetPath": "$.corporateGroups"
            },
            {
                "sourceVariable": "entityIdTargetSystem",
                "targetPath": "$.id"
            },
            {
                "constant": "urn:ietf:params:scim:schemas:core:2.0:User",
                "targetPath": "$.schemas[0]"
            },
            {
                "constant": "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
                "targetPath": "$.schemas[1]"
            },
            {
                "sourcePath": "$.userName",
                "optional": true,
                "targetPath": "$.userName"
            },
            {
                "sourcePath": "$.emails[*].value",
                "preserveArrayWithSingleElement": true,
                "targetPath": "$.emails[?(@.value)]"
            },
            {
                "sourcePath": "$.userType",
                "optional": true,
                "targetPath": "$.userType"
            },
            {
                "sourcePath": "$.name.givenName",
                "optional": true,
                "targetPath": "$.name.givenName"
            },
            {
                "sourcePath": "$.name.middleName",
                "optional": true,
                "targetPath": "$.name.middleName"
            },
            {
                "sourcePath": "$.name.familyName",
                "optional": true,
                "targetPath": "$.name.familyName"
            },
            {
                "sourcePath": "$.displayName",
                "optional": true,
                "targetPath": "$.displayName"
            },
...
```

### Target Entity Data (Result in Identity Authentication)

Code Snippet

Copy codeSwitch to dark mode

```

{
                  "schemas": [
                          "urn:ietf:params:scim:schemas:core:2.0:User",
                          "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User"
                  ],
                  "id": "P000100",
                  "userName": "jsmith",
                  "name": {
                           "familyName": "Smith",
                           "givenName": "John"
                  },
                  "emails": [
                            {
                                            "value": "john.smith@company.com",
                                            "primary": "true",
                                            "type": "work"
                            }
            ],
            "groups": [
                      {
                                      "value": "group1"
                      }
      ],
      "groups_2": [
              {
                              "value": "group22"
              }
      ],
      "groups_3": [
      {
                              "value": "group31"
                  },
                  {
                              "value": "group32"
                  },
                  {
                              "value": "group33"
                  }
        ]
}
```

## Conditions in Transformations

In this example, you can try to apply a condition on whether an attribute of an entity contains a particular string.

The template for such a condition is the following:

"condition": "$.<attribute> =~ /.*<text>.*/",

where:

- **=~** means that a regular expression (regex) will be tested in the condition
- **/** represents the start and end of the regex
- **.*** represents any symbol
- **<text>** is a placeholder for the string that you want the value to contain

### Example 1

With this example, you can check if the first e-mail address of a user contains a particular domain:

"condition": "$.emails[0].value =~ /.*@example.com/",

### Example 2

With this example, you can assign a user to a group, based on their _userName_ containing a particular string:

Code Snippet

Copy codeSwitch to dark mode

```

{
                 "condition": "$.userName =~ /.*explorer.*/",
                 "constant": "Explorers",
                 "targetPath": "$.groups[0].value"
},
{
                 "condition": "$.userName =~ /.*scifi.*/",
                 "constant": "Scientists",
                 "targetPath": "$.groups[1].value"
}
```

**Result:** This will assign all users that have "explorer" in their_userName_ to the "Explorers" group, and all users that contain "scifi" in their _userName_ to the "Scientists" group.

## Transformation Expressions

The transformation logic is based on JSON. The order of the expressions in the file is decisive for how the transformation is executed. The transformation actions are performed in the sequence defined in the transformation logic.

There is a different transformation logic for every entity (users, groups, or roles).

## Transformation Functions

A function is a hard-coded piece of transformation logic that receives a value denoted by the input specified by a source path or a source variable. As a result, the value is replicated into the target path or target variable accordingly. Functions are used in entity transformations and are included as mappings.

## Transformation Variables

System variables specify particular attributes of the read and written entities. They help you map attributes between source and target transformations so that the entities are provisioned correctly to the target systems.

## Transformation Editors

Identity Provisioning provides the graphical and JSON for managing provisioning system transformations.

### Graphical Editor

This editor allows you to graphically model the entities (users, groups, roles) and their content (attribute mappings and transformation expressions, like conditions, functions, constants, and others). It offers the following advantages:

- **Visualization:**
    
    Entities are organized in colored boxes. Every entity has a dedicated color. Users are always blue, groups are orange, and roles are green. Source and target path attributes are displayed horizontally (side-by-side). They are connected with an arrow which indicates the direction of reading and writing the data. Color-coding makes it easy to identify specific configurations. Ignored entities are grayed out, and skipped operations and conditions are displayed in orange.
    
- **Simplification:**
    
    Typing code and following JSON syntax rules are no longer needed, except in cases when conditions are defined. Expressions and functions along with their possible values are prefilled and available for selection in dropdown lists. The editor takes care of adding the dot notation, that is, separating child elements with a period (.), enclosing string values within double quotes, prepending the dollar sign ($) to the JSONPath expression.
    
- **Validation:**
    
    The JSON validator and the preview ensure that the input is in the expected format.
    

Note

The graphical editor is available only for Identity Provisioning tenants running on SAP Cloud Identity infrastructure. It is the default editor.

The following interactive screenshot shows the main elements of the graphical editor. Hover over the image and select the highlighted areas for more information.

![The screenshot of the graphical editor has two user sections, and under these, there are group sections. The user sections have conditions involving personID and entityIdSourceSystem. There is also a condition using current date for validity period. The group section maps ID to displayName.](https://learning.sap.com/service/media/topic/f3295b7d-2313-4fda-a851-ac9f7b303b07/SECCL1_24_en-US_media/SECCL1_24_en-US_images/Trans_Vis_Editor_scr.png "The screenshot of the graphical editor has two user sections, and under these, there are group sections. The user sections have conditions involving personID and entityIdSourceSystem. There is also a condition using current date for validity period. The group section maps ID to displayName.")

The following example illustrates the means by which the address attribute mapping from the Identity Authentication write transformation is displayed in the graphical editor. Compare the same attribute with its representation in the following JSON editor.

![The screenshot shows that the address attribute, which is marked as optional on the left links to addresses settings on the right, including preserveArrayWithSingleElement: true and conditions for putIfAbsent and putIfPresent.](https://learning.sap.com/service/media/topic/f3295b7d-2313-4fda-a851-ac9f7b303b07/SECCL1_24_en-US_media/SECCL1_24_en-US_images/AttributeMapping_scr.png "The screenshot shows that the address attribute, which is marked as optional on the left links to addresses settings on the right, including preserveArrayWithSingleElement: true and conditions for putIfAbsent and putIfPresent.")

The source path attribute addresses in the internal representation (on the left-hand side) and the target path attribute addresses in the target system (on the right-hand side) are displayed horizontally. The arrow shows the direction of reading and writing the data. The transformation expressions and functions are listed under the respective sourcePath and targetPath attribute for which they are applicable.

## JSON Editor

This editor allows you to work with entities and their transformation mappings in text mode. JSON knowledge is required.

The source path attribute addresses in the internal representation and the target path attribute addresses in the target system are displayed vertically - one below the other.

The transformation expressions and functions are listed in individual lines below the respective sourcePath and targetPath attribute for which they are applicable.