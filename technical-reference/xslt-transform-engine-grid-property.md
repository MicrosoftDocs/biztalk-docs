---
# required metadata

title: XSLT Transform Engine (Grid Property)
description: XSLT Transform Engine (Grid Property).
author: Elvis-Shi
ms.author: elsh
manager: mijacobs
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

# XSLT Transform Engine (Grid Property)

**Starting with BizTalk Server 2020**, user can choose Saxon:registered: as XSLT transform engine. It is also possible to plug-in your own XSLT transform engine. Use **XSLT Transform Engine** property to specify the XSLT transform engine you wish to use.

BizTalk's default XSL transform engine implementation is based on .Net Framework [XSLT Transformations](/dotnet/standard/data/xml/xslt-transformations). This support is limited to XSLT 1.0. Use this property to configure other XSL transform engines at map level. This makes it possible for BizTalk server maps to support newer versions of XSLT. Using Saxon:registered: one can readily use XSLT3.0.

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
<td>Use global XSLT transform engine setting. No map specific override is applied.</td>
</tr>
<tr class="even">
<td>.Net Framework</td>
<td>Use ".Net Framework" XSLT transform engine for this map. Property "Use XSL Transform" will be applied in this case.</td>
</tr>
<tr class="odd">
<td>Saxon 9 HE</td>
<td>Use "Saxon-HE 9" XSLT transform engine. Visit www.saxonica.com for more information. </td>
</tr>
<tr class="odd">
<td>Other custom XSLT transform</td>
<td>Use custom XSLT transform engine. More information on how to implement and use custom XSLT transform engine follows. </td>
</tr>
</tbody>
</table>

## Default Value

Undefined

## Create custom XSLT transform

### Steps for plugging in a custom XSL transform engine:

1. Implement abstract class `Microsoft.XLANGs.BaseTypes.ITransform2` in your code. For a sample implementation, please see [Custom XSLT transform implementation](xslt-custom-transform-implementation.md)
2. Copy the compiled DLL file to the "Transform Components" folder (e.g. "\Program Files (x86)\Microsoft BizTalk Server\Transform Components\") on every BizTalk runtime machine.
3. Optional. To use this custom transform engine in the Visual Studio developer tools, update the "CustomTransform.xml" file in the "Developer Tools" folder (e.g. "\Program Files (x86)\Microsoft BizTalk Server\Developer Tools\CustomTransform.xml") as below, and restart Visual Studio:
    - Add a new "Transform" node 
    - Add sub node "DisplayName" with text to be displayed in the drop-down list for "XSLT transform engine" property
    - Add sub node "TypeAssemblyQualifiedName" with details of class that implements your custom transform engine
    For example: 

```xml
<Transform
  DisplayName="Saxon 9 HE"
  TypeAssemblyQualifiedName="Microsoft.XLANGs.BaseTypes.SaxonHEXsltTransform, Microsoft.XLANGs.BaseTypes, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
/>
```

Your custom transform engine will show up in the **XSLT transform engine** drop-down list after Visual Studio restart.

## Global XSLT transform engine

When the map-level XSLT tranform engine is set to "Undefined", the global XSLT transform engine is used. 

By default BizTalk uses ".Net Framework" as the global engine. To override this value, specify the AssemblyQualifiedName of the class implementing the transformation engine as a string value "XsltEngine" in the BizTalk Server registry:

- 64 bit host instances: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration`
- 32 bit host instances: `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\BizTalk Server\3.0\Configuration`

## Saxon:registered: 9 transform engine

>[!IMPORTANT]
>Saxon:registered: 9 doesn't support embedded scripting . As a result, functoids shipped as part of BizTalk may not function well with Saxon 9. 

You must refer to Saxon:registered: documentation for scope of XSLT and Xpath support. If you wish to use other editions, create custom XSLT transform based on these editions. 

**Custom Extension XML** is still a supported way for creating your custom extension for Saxon 9 HE transform engine. Create custom .Net extension functions by implementing interface `ExtensionFunction` or `ExtensionFunctionDefinition`, and add your implementations into **Custom Extension XML**.  Saxon 9 HE transform engine will register extension functions defined in **Custom Extension XML**, and transform processor can then recognize and invoke any call from XSLT.

## Remarks

> [!NOTE]
> You cannot undo or redo the <STRONG>XSLT transform engine</STRONG> property.

## See Also

[Grid Properties](grid-properties.md)

[Custom Extension XML](custom-extension-xml-grid-property.md)