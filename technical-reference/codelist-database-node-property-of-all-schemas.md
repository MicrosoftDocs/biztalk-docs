---
title: CodeList Database (Node Property of All Schemas)
TOCTitle: CodeList Database (Node Property of All Schemas)
ms:assetid: 424ee8f0-a870-4d7a-95fb-0432089ad9a8
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa559801(v=BTS.80)
ms:contentKeyID: 51527572
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# CodeList Database (Node Property of All Schemas)

 

Use the **CodeList Database** property to specify the full path of the Microsoft Access database used for code lists. This database allows for easier configuration of enumerations associated with type derivations by restriction, especially when the enumeration choices are in the form of codes that are not particularly intuitive.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

BizTalk

## Allowed Values

Legal, full path file names that identify Microsoft Access database files.

## Default Value

None.

## XSD Persistence

As the value of the **codelist\_database** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.


> [!NOTE]
> <P>The <STRONG>CodeList</STRONG> and <STRONG>CodeList Database</STRONG> properties are used at design time only and are persisted in the XSD as corresponding settings for the <STRONG>Enumeration</STRONG> property. At run time, all values are verified against the <STRONG>Enumeration</STRONG> property only.</P>



To make use of the appropriate database table in the Access database identified by this property, you must use the **CodeList** property associated with **Field Element** and **Field Attribute** nodes.

For conceptual information about working with code lists in BizTalk Editor, see [Code List Management](https://msdn.microsoft.com/en-us/library/aa577951\(v=bts.80\)).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

