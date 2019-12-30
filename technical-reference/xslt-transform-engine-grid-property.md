---
title: XSLT Transform Engine (Grid Property)
TOCTitle: XSLT Transform Engine (Grid Property)
ms:assetid: 9e206d6d-55f4-41bf-a46a-29e33fe324fd
ms:mtpsurl: https://msdn.microsoft.com/library/Aa577606(v=BTS.80)
ms:contentKeyID: 51530003
ms.date: 08/30/2017
mtps_version: v=BTS.80
---

# XSLT Transform Engine (Grid Property)

 
**Start from BizTalk Server 2020**, user can choose Saxon as XSLT transform engine, or even create their own XSLT transform engine, use the **XSLT Transform Engine** property to specify XSLT transform engine will be used.

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
<td>User can implement custom XSLT transform. Read more in below sections about how to implement and how to use custom XSLT transform. </td>
</tr>
</tbody>
</table>


## Default Value

Undefined

## Create custom XSLT transform

User can define custom XSL transformer by implement abstract class Microsoft.XLANGs.BaseTypes.ITransform2. And drop the implementation dll file into directory "[BizTalkInstallationDir]\Transform Components\" in the runtime server. 

- [Custom XSLT transform implementation](xslt-custom-transform-implementation.md)

To use this custom transformer in Visual Studio during design time, "[BizTalkInstallationDir]\Developer Tools\CustomTransform.xml" should updated,
a new "Transform" node like below should be added. "DisplayName" will be the item text display in the drop-down list of "XSLT transform engine", and "TypeAssemblyQualifiedName" will indicate the custom transform class. 

```xml
	<Transform 
		DisplayName="Saxon 9 HE"
		TypeAssemblyQualifiedName="Microsoft.XLANGs.BaseTypes.SaxonHEXsltTransform, Microsoft.XLANGs.BaseTypes, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"/>
 ```

User will see their custom transformer show up in "XSLT transform engine" drop-down list after Visual Studio restart. Choose it to start use it in BizTalk Server.

## Global XSLT transform engine

Global level XSLT transform engine will be used if "Undefined" is selected for map level XSLT transform engine. Find HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk Server\3.0\Configuration hive in BizTalk Server registry, add new "String Value" with name "XsltEngine", and provide the global XSLT transform engine, allowed value are ".Net Framework", or AssemblyQualifiedName of other transformer including custom transformer class. Default global XSLT transform engine is ".Net Framework" if this registry entry not exists.



> [!NOTE]
> <P>You cannot undo or redo the <STRONG>XSLT transform engine</STRONG> property.</P>



## See Also

[Grid Properties](grid-properties.md)

