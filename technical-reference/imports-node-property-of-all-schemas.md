---
title: Imports (Node Property of All Schemas)
TOCTitle: Imports (Node Property of All Schemas)
ms:assetid: d0ecbee6-ee9f-4cb6-b531-7c5eabb2083e
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa578526(v=BTS.80)
ms:contentKeyID: 51531390
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Imports (Node Property of All Schemas)

 

Use the **Imports** property to use structure definitions provided by other schemas within the schema you are editing using the XSD include, import, and redefine mechanisms, and to examine the default namespaces and namespace prefixes associated with the schema being edited.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Advanced

## Allowed Values

Allowed values are controlled by the **Imports** dialog box, which you open to examine and/or modify the settings associated with this property.

## Default Value

When a schema is first created, there are three default entries associated with the **Imports** property, as follows:

  - The default namespace, without a prefix, is set to the value of the [Target Namespace](target-namespace-node-property-of-all-schemas.md) property.

  - The BizTalk namespace, which defines the structure of annotations and so on and has the prefix "b", is set to the URI "http://schemas.microsoft.com/BizTalk/2003".

  - The XSD namespace, which defines the overall structure of XSD schema definitions and has the prefix "xs", is set to the URI "http://www.w3c.org/2001/XMLSchema".

## XSD Persistence

The default settings associated with the **Import** property are persisted in the XSD as the values associated with separate instances of the **xmlns** attribute of the **schema** element.

Additional settings associated with the **Import** property, representing imported, included, or redefined schemas, are persisted in the XSD as additional instances of the **xmlns** attribute of the **schema** element and as associated **import**, **include**, or **redefine** elements.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.

You can change the settings associated with the **Import** property by clicking the ellipsis (**...**) button located to the right of the property value field to open the **Imports Dialog** dialog box.

Only schemas and namespaces that are part of the current BizTalk project or part of referenced BizTalk assemblies can be imported.

There are three different ways to use another schema within the schema you are editing, all of which correspond to standard XSD mechanisms: Import, Include, and Redefine:

  - You can "import" another schema into the schema you are editing only if the two schemas have different **Target Namespace** property values.

  - You can "include" another schema (the included schema) into the schema you are editing (the including schema) only if the two schemas have exactly the same **Target Namespace** property values. When including another schema, you must make sure that the including and the included schemas do not have any of the same top level element names, attribute names, or data type names (groups, complex types, simple types, and so on). This is because including another schema is equivalent to copying and pasting the contents of the included schema into the including schema.

  - You can "redefine" another schema (the redefined schema) into the schema you are editing (the redefining schema) only if the two schemas have exactly the same **Target Namespace** property values. When redefining another schema, you must make sure that the redefining and the redefined schemas do not have any of the same top level element names, attribute names, or data type names (groups, complex types, simple types, and so on). This is because redefining another schema is equivalent to copying and pasting the contents of the redefined schema into the redefining schema. Data types that you modify in the schema you are editing are also changed in the schema you are redefining.

For additional information about importing, including, and redefining one schema into another schema, see [XSD Resources on the Web](https://msdn.microsoft.com/en-us/library/aa547363\(v=bts.80\)).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

