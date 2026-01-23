---
description: "Learn more about: Type Name (Schema Item Property)"
title: Type Name (Schema Item Property)
TOCTitle: Type Name (Schema Item Property)
ms:assetid: f8a7d4d5-52c6-4df9-820b-b81358b412ab
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562018(v=BTS.80)
ms:contentKeyID: 51533547
ms.date: 08/30/2017
ms.topic: reference
mtps_version: v=BTS.80
---

# Type Name (Schema Item Property)

 

Use the **Type Name** property to examine and set the name of the managed type associated with the selected schema file.

## Category

Advanced

## Allowed Values

Any valid .NET class name string that is not reserved in C\# or by BizTalk Server and is different than the value you have set for the **Namespace** property.

## Default Value

The name of the schema file when the schema was first created, without the .xsd extension and with space characters replaced by underscore (\_) characters.

## Remarks

You can examine and set this property in the Visual Studio Properties window when you select a schema file in Solution Explorer.

To avoid compilation errors, you ensure sure that the value of the [Fully Qualified Name](fully-qualified-name-schema-item-property.md) property (created by concatenating the value of the [Namespace](namespace-schema-item-property.md) property, a period (.) character, and the value of this property) is unique throughout the BizTalk project.

Because the period (.) character has a special meaning in C\#, avoid using it in type name values. For additional information about restrictions that apply to the values you can set for this property, see the remarks section of [Namespace (Schema Item Property)](namespace-schema-item-property.md).

## See Also

[Namespace (Schema Item Property)](namespace-schema-item-property.md)  
[Fully Qualified Name (Schema Item Property)](fully-qualified-name-schema-item-property.md)

