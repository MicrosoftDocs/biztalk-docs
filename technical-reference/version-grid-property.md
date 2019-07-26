---
title: Version (Grid Property)
TOCTitle: Version (Grid Property)
ms:assetid: c19cde4b-1483-4acd-9079-6417bdd48e18
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578466(v=BTS.80)
ms:contentKeyID: 51531061
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Version (Grid Property)

 

Use the **Version** property to specify version "1.0" in relation to the "xml" output method, which appears in the output XML declaration as:

```C#
<?xml version='1.0' ?>  
```

## Category

Custom Header

## Allowed Values

Any string, unenforced by BizTalk Mapper. However, version 1.0 is the only supported version at this time.

## Default Value

1.0

## Remarks

This property provides a value for the **version** attribute of the XSL **output** element. For more information about this attribute, refer to the .NET Framework documentation.


> [!NOTE]
> <P>You cannot undo or redo the <STRONG>Version</STRONG> property.</P>



## See Also

[Grid Properties](grid-properties.md)

