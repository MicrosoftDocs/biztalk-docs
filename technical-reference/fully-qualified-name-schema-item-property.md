---
description: "Learn more about: Fully Qualified Name (Schema Item Property)"
title: Fully Qualified Name (Schema Item Property)
TOCTitle: Fully Qualified Name (Schema Item Property)
ms:assetid: 193a0312-661d-4cef-bd23-4aab346542ef
ms:mtpsurl: https://msdn.microsoft.com/library/Aa559007(v=BTS.80)
ms:contentKeyID: 51526498
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# Fully Qualified Name (Schema Item Property)

 

Use the **Fully Qualified Name** property to examine the compiler-generated fully qualified name of the managed type of the selected schema file.

## Category

Advanced

## Read-Only Value

The compiler-generated fully qualified name of the managed type associated with the selected schema file, produced by combining the [Namespace](namespace-schema-item-property.md) and [Type Name](type-name-schema-item-property.md) properties, separated by a period (.).

## Remarks

You can examine this property in the Visual Studio Properties window when you select a schema file in Solution Explorer.

This property is read-only.

To avoid compilation errors, all items in a BizTalk project must have a unique value for their **Fully Qualified Name** property. Because you create the value of this property by concatenating the **Namespace** property, a period (.), and the **Type Name** property, you must make sure that the values you provide for these two properties, when combined, are unique within the BizTalk project.

## See Also

[Namespace (Schema Item Property)](namespace-schema-item-property.md)  
[Type Name (Schema Item Property)](type-name-schema-item-property.md)

