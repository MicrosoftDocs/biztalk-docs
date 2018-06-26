---
title: "Code List Management | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a924c814-d077-4aea-bacb-bf2e8a3dee01
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Code List Management

## Overview
You use XSD to specify a specific set of values that are valid for an element or attribute. This functionality is available using the **enumeration** element. When you derive a data type for a **Field Element** or **Field Attribute** node by restriction, one of the properties that becomes available to you in the **Restriction** category is the **Enumeration** property. Using this property, you can open the **Enumeration Editor** dialog box in which you can enter the values that should be considered valid for the corresponding element or attribute in instance messages.  

 Microsoft BizTalk Server provides an alternative, richer way to manage enumerations in your schemas, known as code lists. Code lists use a Microsoft Access database to store the choices for your various enumerations, which allows you to manage them in a more centralized way. Further, if the enumeration values you need to use consist of non-intuitive numeric codes, which would need to be entered in that form using the **Enumeration** property, the tables you create in an Access database to use with the code list functionality include textual descriptions of these numeric values. The textual descriptions are used in the **CodeList** dialog box rather than their more obscure numeric equivalents.  

## Use the code list  
 You must perform several different steps to use the code list feature, including:  

- You must create an Access database with an appropriately named table, with the expected columns, and populate it with values.  

  - The name of the table is a combination of the **Standard** and **Standard Version** properties of the **Schema** node, separated by an underscore (_) character. For example, if you have set the **Standard** property of the **Schema** node to XML and the **Standard Version** property to MyVersion1, the Access database specified by the **CodeList Database** property must have a table named XML_MyVersion1.  

    More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

  - This table must have three columns, typically named Code, Value, and Desc. The first column identifies rows that are related to one another, where each such row provides one of the enumeration choices that may potentially be allowed for the data that corresponds to the selected **Field Element** or **Field Attribute** node. All rows with the same value in the first column form a group. These values are typically integers, but can be any string that does not contain spaces.  

     The second and third columns of each row in the table must be configured to contain the corresponding value and textual representation of each possible enumeration value, respectively.  

     For example, the following representation of an Access database table for use with the Code List feature contains two sets of three related enumeration values. The specific values in the first column are arbitrary and are used to associate related rows.  


    | Code | Value |  Desc  |
    |------|-------|--------|
    |  1   |  13   |  Red   |
    |  1   |  16   | Green  |
    |  1   |  19   |  Blue  |
    |  2   |   1   | Small  |
    |  2   |   2   | Medium |
    |  2   |   3   | Large  |


- You must properly configure three properties of the **Schema** node:  

  -   The **CodeList Database** property must be set to the name of the Access database you have created.  

  -   The **Standard** and **Standard Version** properties must be set such that when they are combined with a separating underscore (_) character, they form the name of the appropriate table within the specified Access database.  

- To actually make use of the values in the Access database for a particular selected **Field Element** or **Field Attribute** node, you must configure two of its properties:  

  -   You must set its **Derived By** property to **Restriction**. The other property you need to configure, **CodeList**, will not be enabled until you perform this step.  

  -   You must type a value into the **CodeList** property that corresponds to the value in the first column (the **Code** column) of one or more rows in the specified Access database. This action identifies the set of enumeration values that you intend to have correspond to the selected **Field Element** or **Field Attribute** node.  

       Then you must click the ellipsis (**...**) button located to the right of the **CodeList** property value field to open the **CodeList** dialog box. Using the check boxes in this dialog box, select the values that you want to allow as legal values for the instance message data that corresponds to the selected **Field Element** or **Field Attribute** node. You are allowed to select only a subset of the available values. For example, using the preceding table example, if you type the value 1 into the **CodeList** property, the **CodeList** dialog box will contain the choices Red, Green, and Blue. If you select the check boxes for Red and Green, and do not select the check box for Blue, only the former colors will appear in the XSD as valid values for the selected **Field Element** or **Field Attribute** node.  

> [!NOTE]
>  The **CodeList** and **CodeList Database** properties are used at design time only and are persisted in the XSD as corresponding settings for the **Enumeration** property. At run time, all values are verified against the **Enumeration** property only.  

> [!CAUTION]
>  For a given **Field Element** or **Field Attribute** node, do not use both the **Enumeration** property and the **CodeList** property. Using the latter property can result in values entered using the former property to be overwritten.  

## See Also  
 [Considerations When Creating Schemas](../core/considerations-when-creating-schemas.md)