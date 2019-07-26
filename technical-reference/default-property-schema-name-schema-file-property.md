---
title: Default Property Schema Name (Schema File Property)
TOCTitle: Default Property Schema Name (Schema File Property)
ms:assetid: e53b023e-c5de-450b-9b60-bda0ec5cf16b
ms:mtpsurl: https://msdn.microsoft.com/library/Aa561620(v=BTS.80)
ms:contentKeyID: 51532997
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Default Property Schema Name (Schema File Property)

 

Use the **Default Property Schema Name** property to specify the name of the property schema file used by the **Quick Promotion** feature.

## Category

Property Schema

## Allowed Values

A valid, pathless file name with an .xsd extension that identifies the file to use as the default property schema.

## Default Value

PropertySchema.xsd

## Remarks

You can examine and set this property in the **Property Pages** dialog box that appears when you right-click a schema file in Visual Studio Solution Explorer and then click **Properties** on the shortcut menu.

If the specified file does not exist, it will be created, added to the project, and persisted in the XSD representation of the schema when you use the **Quick Promotion** feature.

Do not specify a path; only specify a file name with the .xsd extension.

## See Also

[Schema File Properties](schema-file-properties.md)

