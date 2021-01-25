---
description: "Learn more about: Root Reference (Node Property of All Schemas)"
title: Root Reference (Node Property of All Schemas)
TOCTitle: Root Reference (Node Property of All Schemas)
ms:assetid: 66ec55e0-e634-4ce0-8eb8-711b638f6272
ms:mtpsurl: https://msdn.microsoft.com/library/Aa560552(v=BTS.80)
ms:contentKeyID: 51528576
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Root Reference (Node Property of All Schemas)

 

Use the **Root Reference** property to specify the node that represents the outermost element in the XML business document represented by the schema.

## Applies to Nodes of Type

[Schema](schema-node-properties.md)

## Category

Reference

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Drop-down list choice</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes the <strong>root_reference</strong> attribute, if present, resulting in classes being generated for all root nodes when the schema is compiled.</td>
</tr>
<tr class="even">
<td>Node names of all root <strong>Record</strong> nodes in the schema.</td>
<td>The other available values are the names (<strong>Node Name</strong> property value) of the root <strong>Record</strong> nodes currently defined in the schema.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, resulting in classes being generated for all root nodes when the schema is compiled.

## XSD Persistence

As the value of the **root\_reference** attribute of the **schema/annotation/appinfo/schemaInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select the **Schema** node in BizTalk Editor.

Any root **Record** node in your schema can be configured as the value for the **Root Reference** property.

BizTalk Mapper uses this property to determine which root node and substructure to use in the map if a schema has multiple root nodes. If it is not set, BizTalk Mapper will prompt for the appropriate root node to use for mapping.

If you configure this property, use the schema to develop a map, and then later change the value of this property, the map will not automatically update to use the new root reference.

If the **Root Reference** property is not set, .NET classes will be generated for each and every root **Record** node (direct child nodes of the **Schema** node) during the BizTalk project build process (also known as schema compilation). You should avoid this scenario when you have a large number of such root nodes defined in your schema because so many .NET classes will be generated in the resulting BizTalk assembly and ultimately deployed to the database. If a particular root node is always going to be used for instance validation and so on, you should set it as the value of the **Root Reference** property, resulting in a single .NET class being generated for the schema.

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

