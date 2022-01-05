---
# required metadata

title: Use XSL Transform (Grid Property)
description: Use XSL Transform (Grid Property)
author: Elvis-Shi
ms.author: elsh
manager: dougeby
ms.date: 01/14/2020
ms.topic: reference
ms.prod: biztalk-server
# optional metadata

#ROBOTS:

ms.reviewer: 
ms.suite:
ms.tgt_pltfrm:
ms.assetid: 
ms.custom: biztalk-2020
---

# Use XSL Transform (Grid Property)

**Starting with BizTalk Server 2013 R2**, use the **Use XSL Transform** property to specify whether [XslTransform](/dotnet/api/system.xml.xsl.xsltransform) or [XslCompiledTransform](/dotnet/api/system.xml.xsl.xslcompiledtransform)) is used for XSLT transform. This property is only used when **.Net Framework** is selected for [XSLT transform engine](xslt-transform-engine-grid-property.md) property.

## Category

Compiler

## Allowed Values

| Value | Description |
| --- | --- |
|Undefined | If **Undefined** is selected, **Use XSL Transform** is used at the global level. |
| Yes | [XslTransform](/dotnet/api/system.xml.xsl.xsltransform) is used for XSLT transform. |
| No | [XslCompiledTransform](/dotnet/api/system.xml.xsl.xslcompiledtransform) is used for XSLT transform. |

## Default Value

Undefined

## Remarks

- If **Undefined** is selected for the map level property, then **Use XSL Transform** is used at the global level.
- On the BizTalk Server, open the registry editor app (`regedit`), and go to `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`. Add a new **DWORD Value** with the following properties:

  **Name**: UseXslTransform  
  **Value data**: 1

  `1` means XslTransform is used. Otherwise, XslCompiledTransform is used. If this registry entry doesn't exist, then **Use XSL Transform** is `0`, which means XslCompiledTransform is used.

> [!NOTE]
> You can't undo or redo the **Use XSL Transform** property.

## See Also

[Grid Properties](grid-properties.md)
