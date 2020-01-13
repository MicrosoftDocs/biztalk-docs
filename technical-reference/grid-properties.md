---
title: Grid Properties
TOCTitle: Grid Properties
ms:assetid: 0478cd4a-3786-4b90-9e37-6dc64797e018
ms:mtpsurl: https://msdn.microsoft.com/library/Aa546825(v=BTS.80)
ms:contentKeyID: 51525949
ms.date: 12/27/2019
ms.custom: biztalk-2020
mtps_version: v=BTS.80
---

# Grid Properties

 

Grid properties are displayed in the Microsoft® Visual Studio Properties window when you click in the background of a grid page. These properties control global aspects of how a map is created and compiled. Many of these properties, specifically those in the Custom Header category, correspond to attributes of the XSL **output** element, allowing you to specify options for use in serializing the transformation output.


> [!NOTE]
> <P>Grid properties apply to the grid as a whole, and not to the individual pages in the grid. In other words, if you set a grid property on one grid page, and then set the same property when a different grid page is showing, you are setting the same single property, and not two different instances of the same property.</P>



The following table describes grid properties.

<table>
<thead>
<tr class="header">
<th>Property name</th>
<th>Category</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><a href="cdata-section-elements-grid-property.md">CDATA Section Elements</a></td>
<td>Custom Header</td>
<td>Specifies a list of elements whose text node children should be output by using CDATA sections.<br />
<br />
Provides a value for the <strong>cdata-section-elements</strong> attribute of the XSL <strong>output</strong> element.</td>
</tr>
<tr class="odd">
<td><a href="copy-processing-instructions-pis-grid-property.md">Copy Processing Instructions (PIs)</a></td>
<td>Custom Header</td>
<td>Specifies whether any processing instructions found in the source instance message should be copied to the destination instance message during transformation.</td>
</tr>
<tr class="even">
<td><a href="custom-extension-xml-grid-property.md">Custom Extension XML</a></td>
<td>Compiler</td>
<td>Specifies the custom extension XML file, if any.</td>
</tr>
<tr class="odd">
<td><a href="custom-xslt-path-grid-property.md">Custom XSLT Path</a></td>
<td>Compiler</td>
<td>Specifies the custom XSLT file, if any.</td>
</tr>
<tr class="even">
<td><a href="doctype-public-grid-property.md">Doctype Public</a></td>
<td>Custom Header</td>
<td>Specifies the public identifier to be used in the DTD.<br />
<br />
Provides a value for the <strong>doctype-public</strong> attribute of the XSL <strong>output</strong> element.</td>
</tr>
<tr class="odd">
<td><a href="doctype-system-grid-property.md">Doctype System</a></td>
<td>Custom Header</td>
<td>Specifies the system identifier to be used in the DTD.<br />
<br />
Provides a value for the <strong>doctype-system</strong> attribute of the XSL <strong>output</strong> element.</td>
</tr>
<tr class="even">
<td><a href="ignore-namespaces-for-links-grid-property.md">Ignore Namespaces for Links</a></td>
<td>General</td>
<td>Specifies whether the links stored in the map contain any references to the namespaces used in the schemas.</td>
</tr>
<tr class="odd">
<td><a href="indent-grid-property.md">Indent</a></td>
<td>Custom Header</td>
<td>Specifies whether the XML in destination instance messages produced by using this map will be indented for improved readability.<br />
<br />
Provides a value for the <strong>indent</strong> attribute of the XSL <strong>output</strong> element.</td>
</tr>
<tr class="even">
<td><a href="media-type-grid-property.md">Media-Type</a></td>
<td>Custom Header</td>
<td>Specifies the media type (Multipurpose Internet Mail Extensions (MIME) content type) of the data in the output of the transformation.<br />
<br />
Provides a value for the <strong>media-type</strong> attribute of the XSL <strong>output</strong> element.</td>
</tr>
<tr class="odd">
<td><a href="method-grid-property.md">Method</a></td>
<td>Custom Header</td>
<td>Specifies the overall method for producing the result tree.</td>
</tr>
<tr class="even">
<td><a href="omit-xml-declaration-grid-property.md">Omit XML Declaration</a></td>
<td>Custom Header</td>
<td>Specifies whether the transformation output should include an XML declaration.<br />
<br />
Provides a value for the <strong>omit-xml-declaration</strong> attribute of the XSL <strong>output</strong> element.</td>
</tr>
<tr class="odd">
<td><a href="script-type-precedence-grid-property.md">Script Type Precedence</a></td>
<td>Compiler</td>
<td>Opens the <strong>Script Type Precedence</strong> dialog box, in which you can configure the relative precedence of the various types of script.</td>
</tr>
<tr class="even">
<td><a href="source-schema-grid-property.md">Source Schema</a></td>
<td>General</td>
<td>Shows the relative path to the chosen source schema.</td>
</tr>
<tr class="odd">
<td><a href="standalone-grid-property.md">Standalone</a></td>
<td>Custom Header</td>
<td>Specifies whether the XSLT processor should output a stand-alone document declaration.<br />
<br />
Provides a value for the <strong>standalone</strong> attribute of the XSL <strong>output</strong> element.</td>
</tr>
<tr class="even">
<td><a href="target-schema-grid-property.md">Target Schema</a></td>
<td>General</td>
<td>Shows the relative path to the chosen destination schema.<br />
<br />
 <strong>Note:</strong> In Microsoft BizTalk® Server, &quot;target&quot; and &quot;destination&quot; are used interchangeably with respect to schemas and instance messages.</td>
</tr>
<tr class="odd">
<td><a href="use-xsl-transform-grid-property.md">Use XSL Transform</a></td>
<td>Compiler</td>
<td>Indicates whether to use legacy .Net <a href="https://docs.microsoft.com/en-us/dotnet/api/system.xml.xsl.xsltransform">XslTransform</a> to achieve XSLT transformation, otherwise <a href="https://docs.microsoft.com/en-us/dotnet/api/system.xml.xsl.xslcompiledtransform">XslCompiledTransform</a> will be used if "False" is selected.<br />
<br />
This option will only be used when ".Net Framework" is selected as "XSLT transform engine".</td>
</tr>
<tr class="even">
<td><a href="version-grid-property.md">Version</a></td>
<td>Custom Header</td>
<td>Specifies version &quot;1.0&quot; in relation to the &quot;xml&quot; output method, which appears in the output XML declaration as:<br />
<br />
 <code>&lt;?xml version='1.0' ?&gt;</code><br />
<br />
Provides a value for the <strong>version</strong> attribute of the XSL <strong>output</strong> element.</td>
</tr>
<tr class="odd">
<td><a href="xslt-encoding-grid-property.md">XSLT Encoding</a></td>
<td>Custom Header</td>
<td>Specifies the preferred character encoding that the parser should use to encode sequences of characters as sequences of bytes.<br />
<br />
Provides a value for the <strong>encoding</strong> attribute of the XSL <strong>output</strong> element.</td>
</tr>
<tr class="even">
<td><a href="xslt-transform-engine-grid-property.md">XSLT transform engine</a></td>
<td>Compiler</td>
<td>Indicates XSLT transform engine to be used in runtime transformation.<br />
</td>
</tr>
</tbody>
</table>

