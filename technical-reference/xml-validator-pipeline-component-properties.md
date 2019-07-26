---
title: XML Validator Pipeline Component Properties
TOCTitle: XML Validator Pipeline Component Properties
ms:assetid: fc10c053-9878-4a66-aa89-b21a81068adc
ms:mtpsurl: https://msdn.microsoft.com/library/Aa562097(v=BTS.80)
ms:contentKeyID: 51533643
ms.date: 08/30/2017
mtps_version: v=BTS.80
f1_keywords:
- Microsoft.BizTalk.Component.XmlValidator
- Microsoft.BizTalk.PipelineComponents.XmlValidator
---

# XML Validator Pipeline Component Properties

 

Use the XML validator pipeline component to verify the message against the specified schema or schemas. If the message does not conform to these schemas, the component raises an error and the message is placed in the suspended queue by the messaging engine.

The XML validator pipeline component is intended for use in any stage (except disassemble or assemble) in a Send or Receive pipeline.

The properties of the XML validator pipeline component can be set in the Properties window of Microsoft Visual Studio. To display the Properties window, select the component, right-click and select **Properties**, or press F4. The following table contains the configurable XML validator pipeline component properties.

<table>
<thead>
<tr class="header">
<th>Use this</th>
<th>To do this</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Document schemas</strong></td>
<td>Indicate the namespace and typename of the schema or schemas to be applied to the document. For more information, see <a href="https://msdn.microsoft.com/library/aa559127(v=bts.80)">How to Use the Schema Collection Property Editor</a>. If no schemas are specified, the runtime schema discovery will use the message's target namespace and root element name information.<br />
<br />
Default value: Empty collection (Collection)</td>
</tr>
<tr class="even">
<td><strong>Recoverable interchange processing</strong></td>
<td>Indicate whether to process messages within an interchange individually. For more information, see <a href="https://msdn.microsoft.com/library/aa578714(v=bts.80)">Recoverable Interchange Processing</a><br />
<br />
Default Value: False</td>
</tr>
</tbody>
</table>


## See Also

[Using Pipeline Designer](https://msdn.microsoft.com/library/aa578392\(v=bts.80\))  
[How to Configure the XML Validator Pipeline Component](https://msdn.microsoft.com/library/aa559670\(v=bts.80\))  
[XML Validator Pipeline Component](https://msdn.microsoft.com/library/aa578187\(v=bts.80\))

