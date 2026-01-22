---
description: "Learn more about: Sensitive Information (Node Property of Property Schemas)"
title: Sensitive Information (Node Property of Property Schemas)
TOCTitle: Sensitive Information (Node Property of Property Schemas)
ms:assetid: 8155e60f-2d47-4b07-81c3-fc99935a9123
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561084(v=BTS.80)
ms:contentKeyID: 51529291
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Sensitive Information (Node Property of Property Schemas)

 

Use the **Sensitive Information** property to configure whether the information that corresponds to this **Field Element** node is sensitive. Information that is designated as sensitive will not be visible within the Group Hub page within the BizTalk Server Administration Console.

## Applies to Nodes of Type

[Field Element](field-element-node-properties.md)

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
<td><strong>Yes</strong></td>
<td>Use this value if the data corresponding to the selected <strong>Field Element</strong> node is sensitive and you want to restrict its visibility within other BizTalk Server components.</td>
</tr>
<tr class="even">
<td><strong>No</strong></td>
<td>Use this value if the data corresponding to the selected <strong>Field Element</strong> node is not sensitive and you want it to have normal visibility within other BizTalk Server components.</td>
</tr>
<tr class="odd">
<td><strong>(Default)</strong></td>
<td>Removes the corresponding annotation in the XSD representation of the schema, if any, resulting in the same behavior as the <strong>No</strong> setting.</td>
</tr>
</tbody>
</table>


## Default Value

**(Default)**, resulting in no corresponding annotation in the XSD representation of the schema, and producing the same behavior as the **No** setting.

## XSD Persistence

As the value of the **isSensitive** (="true" or "false") attribute of the **element/annotation/appinfo/fieldInfo** annotation element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you are editing a property schema and you select a **Field Element** node in BizTalk Editor.

Do not promote sensitive information to property schema **Field Element** nodes for which the **Sensitive Information** property is set to **Yes**, either at design time by specifying property promotion in the schemas governing instance messages and their envelopes or at run time from within custom adapters and pipeline components. Disallowed promotions of the former type are detected at deployment time and disallowed promotions of the latter type result in your call to the `IBaseMessageContext.Promote` method failing at run time.

If you want to keep, but not promote, sensitive information in the message context, set the **Sensitive Information** property of the corresponding **Field Element** nodes to **Yes** and use the `IBaseMessageContext.Write` method in the custom adapter or pipeline component to write the sensitive information to the message context. Doing so will preserve the sensitivity of such information by keeping it from being visible to BizTalk Server administrators and message and service instance tracking users.

If you set this property to **Yes**, entries corresponding to the selected **Field Element** node will not be shown within the following BizTalk Server component:

  - In BizTalk Explorer, in the ***\<Type of Port\>* Send Port Properties** - **Configurations** - **Filters & Maps** - **Filters** dialog box, information designated as sensitive will not appear in the drop-down lists in the **Property** column. This means that data that has been designated as sensitive cannot be used in content-based routing (CBR) scenarios.
    
    To open this dialog box in BizTalk Explorer, right-click a send port, click **Edit**, and then in the ***\<Type of Port\>* Send Port Properties** dialog box, expand **Configurations**, then **Filters & Maps**, and then **Filters**.

## See Also

[Supplemental Node Properties for Property Schemas](supplemental-node-properties-for-property-schemas.md)

