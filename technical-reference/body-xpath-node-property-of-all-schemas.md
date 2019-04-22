---
title: Body XPath (Node Property of All Schemas)
TOCTitle: Body XPath (Node Property of All Schemas)
ms:assetid: 69ea9e35-fa36-4bbf-bc74-74d7938edd22
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/Aa560625(v=BTS.80)
ms:contentKeyID: 51528674
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Body XPath (Node Property of All Schemas)

 

Use the **Body XPath** property to identify the portion of the schema that defines the body of the message associated with the selected root **Record** node in an envelope schema.

## Applies to Nodes of Type

[Record](record-node-properties.md)

## Category

Parse

## Allowed Values

XPath values are specified using the schema subtree displayed within the **Body XPath** dialog box, which can be opened using the ellipsis (**...**) button located to the right of the **Body XPath** property value field.


> [!NOTE]
> <P>Only canonical XPath values are supported by the BizTalk Server engine. They must be constructed using the default schema format (for example: <CODE>/*[local-name()="..." and namespace-uri()="..."]</CODE>). Also note that <CODE>position()="..."</CODE> specifiers cannot be used in the XPath.</P>



## Default Value

None.

## XSD Persistence

As the value of the **body\_xpath** attribute of the **schema/annotation/appinfo/recordInfo** element.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a root **Record** node in an envelope schema in BizTalk Editor (envelope schemas are those schemas for which you have set the [Envelope](envelope-node-property-of-all-schemas.md) property of the **Schema** node to **Yes**).

## See Also

[Node Properties of All Schemas](node-properties-of-all-schemas.md)

