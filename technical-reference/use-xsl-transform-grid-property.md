---
# required metadata

title: Use XSL Transform (Grid Property)
description: Use XSL Transform (Grid Property)
author: Elvis-Shi
ms.author: elsh
manager: dougeby
ms.date: 01/06/2029
ms.topic: conceptual
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

**Start from BizTalk Server 2020**, user can use **Use XSL Transform** property to specify whether [XslTransform](https://docs.microsoft.com/en-us/dotnet/api/system.xml.xsl.xsltransform) (or [XslCompiledTransform](https://docs.microsoft.com/en-us/dotnet/api/system.xml.xsl.xslcompiledtransform)) will be used for XSLT transform. This property will only be used when ".Net Framework" is selected for [XSLT transform engine](xslt-transform-engine-grid-property.md) property.

## Category

Compiler

## Allowed Values

<table>
<thead>
<tr class="header">
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Undefined</td>
<td>Global level "Use XSL Transform" will be used if "Undefined" is selected.</td>
</tr>
<tr class="even">
<td>Yes</td>
<td><a href="https://docs.microsoft.com/en-us/dotnet/api/system.xml.xsl.xsltransform">XslTransform</a> will be used for XSLT transform.</td>
</tr>
<tr class="odd">
<td>No</td>
<td><a href="https://docs.microsoft.com/en-us/dotnet/api/system.xml.xsl.xslcompiledtransform">XslCompiledTransform</a> will be used for XSLT transform.</td>
</tr>
</tbody>
</table>

## Default Value

Undefined

## Remarks

Global level "Use XSL Transform" will be used if "Undefined" is selected for map level property. 
Find HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration hive in BizTalk Server registry, add new "DWORD Value" with name "UseXslTransform", value "1" means XslTransform will be used, otherwise "XslCompiedTransform" will be used. Default global "Use XSL Transform" is "0"(means XslCompiledTransform will be used) if this registry entry not exists.


> [!NOTE]
> <P>You cannot undo or redo the <STRONG>Use XSL Transform</STRONG> property.</P>



## See Also

[Grid Properties](grid-properties.md)

