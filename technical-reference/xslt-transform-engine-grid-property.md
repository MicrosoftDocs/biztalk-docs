---
# required metadata

title: XSLT Transform Engine (Grid Property)
description: XSLT Transform Engine (Grid Property).
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

# XSLT Transform Engine (Grid Property)

**Start from BizTalk Server 2020**, user can choose Saxon as XSLT transform engine, or even create their own XSLT transform engine, use **XSLT Transform Engine** property to specify XSLT transform engine will be used.

BizTalk lower level XSL transformation was implemented on top of .Net Framework [XSLT Transformations](https://docs.microsoft.com/en-us/dotnet/standard/data/xml/xslt-transformations) before **BizTalk Server 2020**, which only support [XSLT 1.0](https://www.w3.org/TR/xslt-10/). With this property, BizTalk server map is able to support [XSLT 3.0](https://www.w3.org/TR/xslt-30/), and even further XSLT standard as user can always create custom XSL transform based on new technology to use in BizTalk runtime.

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
<td>Specifies that no map level XSLT transform engine defined, which means global XSLT transform engine which set in registry will be used .</td>
</tr>
<tr class="even">
<td>.Net Framework</td>
<td>Specifies that ".Net Framework" XSLT transformations will be used based on property "Use XSL Transform".</td>
</tr>
<tr class="odd">
<td>Saxon 9 HE</td>
<td>Specifies that "Saxon 9 HE" will be used as XSLT transform engine. Visit www.saxonica.com for more information about Saxon and its different editions. </td>
</tr>
<tr class="odd">
<td>Other custom XSLT transform</td>
<td>Specifies other custom XSLT transform. Read more in below sections about how to implement and how to use custom XSLT transform. </td>
</tr>
</tbody>
</table>


## Default Value

Undefined

## Create custom XSLT transform

Define custom XSL transformer by implementing abstract class Microsoft.XLANGs.BaseTypes.ITransform2. And drop the implementation dll file into directory "\Program Files (x86)\Microsoft BizTalk Server\Transform Components\" in the runtime server. 

- [Custom XSLT transform implementation](xslt-custom-transform-implementation.md)

To use this custom transformer in Visual Studio during design time, "\Program Files (x86)\Microsoft BizTalk Server\Developer Tools\CustomTransform.xml" should updated,
a new "Transform" node like below should be added. "DisplayName" will be the item text display in the drop-down list for "XSLT transform engine" property, and "TypeAssemblyQualifiedName" will indicate the custom transform class. 

```xml
	<Transform 
		DisplayName="Saxon 9 HE"
		TypeAssemblyQualifiedName="Microsoft.XLANGs.BaseTypes.SaxonHEXsltTransform, Microsoft.XLANGs.BaseTypes, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"/>
 ```

Your custom transformer will show up in "XSLT transform engine" drop-down list after Visual Studio restart.

## Global XSLT transform engine

Global level XSLT transform engine will be used if "Undefined" is selected for map level XSLT transform engine. Find HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration hive in BizTalk Server registry, add new "String Value" with name "XsltEngine", and provide the global XSLT transform engine, allowed value are ".Net Framework", or AssemblyQualifiedName of other transformer including custom transformer class. Default global XSLT transform engine is ".Net Framework" if this registry entry not exists.

## Saxon 9 transform engine
>[!IMPORTANT]
>Saxon 9 doesn't support embedded scripting, which means all BizTalk map functoids will not be supported in Saxon 9 HE(or any other Saxon editions), because BizTalk map functoids are implemented on top of embedded scripting. You probably have to update your map definition to using [Custom XSLT Path](custom-xslt-path-grid-property.md) if willing to switch from **.Net framework** transform engine to **Saxon 9 HE**.

Only standard XSLT and XPath instructions are supported in Saxon if claimed. Saxon also provides several different ways of extensions, most of which are only available in PE and EE, create custom XSLT transform based on these editions if you are willing to use Saxon PE and EE.

**Custom Extension XML** is still a supported way for creating your custom extension for Saxon 9 HE transform engine. Create custom .Net extension functions by implementing interface `ExtensionFunction` or `ExtensionFunctionDefinition`, and add your implementations into **Custom Extension XML**.  Saxon 9 HE transform engine will register extension functions defined in **Custom Extension XML**, and transform processor can then recognize and invoke any call from XSLT.



## Remark

> [!NOTE]
> <P>You cannot undo or redo the <STRONG>XSLT transform engine</STRONG> property.</P>



## See Also

[Grid Properties](grid-properties.md)

[Custom Extension XML](custom-extension-xml-grid-property.md)

