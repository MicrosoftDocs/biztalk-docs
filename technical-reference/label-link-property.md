---
description: "Learn more about: Label (Link Property)"
title: Label (Link Property)
TOCTitle: Label (Link Property)
ms:assetid: 1565c75f-fea9-48ec-b8f3-cb903929937a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa558714(v=BTS.80)
ms:contentKeyID: 51526421
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# Label (Link Property)

 

Use the **Label** property to provide a name for the selected link that makes sense to you in the context of its use.

## Category

General

## Allowed Values

Any string. The string should describe this link, generally based on where it originates in the source schema or from another functoid.

## Default Value

None.

## Remarks

The maximum number of characters allowed is 256.

Configuring this property is helpful when the link is used as an input other than the first or second input to the **Table Looping** functoid. This is because the descriptive value you provide for the **Label** property of the link is shown in the table cell drop-down lists in the **Table Looping Configuration** dialog box. If you do not provide a value for the **Label** property of such links, the value of the **Link Source** property for the link is shown; when this value is an XPath value, as opposed to a functoid type, it is more difficult to determine the source of the link when choosing a link value for the table cell.

For more information about table-driven looping, see [Table Looping and Table Extractor Functoids](https://msdn.microsoft.com/library/aa559310\(v=bts.80\)).

## See Also

[Link Properties](link-properties.md)

