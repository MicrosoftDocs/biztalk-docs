---
description: "Learn more about: IPipelineContext Members (COM)"
title: IPipelineContext Members (COM)
TOCTitle: IPipelineContext Members (COM)
ms:assetid: d6a57420-85e9-43fe-8fd2-4a2aabe54c0a
ms:mtpsurl: https://msdn.microsoft.com/library/Aa578647(v=BTS.80)
ms:contentKeyID: 51531680
ms.date: 08/30/2017
mtps_version: v=BTS.80
ms.topic: reference
---

# IPipelineContext Members (COM)


[IPipelineContext Interface (COM)](ipipelinecontext-interface-com.md)

## Public Properties

<table>
<tbody>
<tr class="odd">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" alt="Icon that represents the ComponentIndex property."/> <a href="ipipelinecontext-componentindex-property-com.md">ComponentIndex</a></td>
<td>Gets the index of the current component in the stage.</td>
</tr>
<tr class="even">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" alt="Icon that represents the PipelineID property."/> <a href="ipipelinecontext-pipelineid-property-com.md">PipelineID</a></td>
<td>Gets the ID of the pipeline to which this component belongs.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" alt="Icon that represents the PipelineName property."/> <a href="ipipelinecontext-pipelinename-property-com.md">PipelineName</a></td>
<td>Gets the name of the pipeline.</td>
</tr>
<tr class="even">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" alt="Icon that represents the ResourceTracker property."/> <strong>ResourceTracker</strong></td>
<td>Reports the objects used during execution.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" alt="Icon that represents the StageID property."/> <a href="ipipelinecontext-stageid-property-com.md">StageID</a></td>
<td>Gets the ID of the stage in the pipeline.</td>
</tr>
<tr class="even">
<td><img src="images/Aa559521.43dc4f45-81a9-4bc9-ac9f-c6f88d5f9a89(BTS.80).jpeg" alt="Icon that represents the StageIndex property."/> <a href="ipipelinecontext-stageindex-property-com.md">StageIndex</a></td>
<td>Gets the index of the pipeline stage where the current component is located.</td>
</tr>
</tbody>
</table>


## Public Methods

<table>
<tbody>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" alt="Icon that represents the GetDocumentSpecByName method."/> <a href="ipipelinecontext-getdocumentspecbyname-method-com.md">GetDocumentSpecByName</a></td>
<td>Gets an <a href="idocumentspec-interface-com.md">IDocumentSpec</a> object for the specified document name.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" alt="Icon that represents the GetDocumentSpecByType method."/>Â <a href="ipipelinecontext-getdocumentspecbytype-method-com.md">GetDocumentSpecByType</a></td>
<td>Gets an <a href="idocumentspec-interface-com.md">IDocumentSpec</a> object for the specified document type.</td>
</tr>
<tr class="odd">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" alt="Icon that represents the GetGroupSigningCertificate method."/>Â <a href="ipipelinecontext-getgroupsigningcertificate-method-com.md">GetGroupSigningCertificate</a></td>
<td>Gets the signing certificate for the group.</td>
</tr>
<tr class="even">
<td><img src="images/Aa562050.7398304a-180c-45ff-98a9-894581a54aa5(BTS.80).jpeg" alt="Icon that represents the GetMessageFactory method."/>Â <a href="ipipelinecontext-getmessagefactory-method-com.md">GetMessageFactory</a></td>
<td>Get access to the helper interface to work with BizTalk Server message objects.</td>
</tr>
</tbody>
</table>


## See Also

[IPipelineContext Interface (COM)](ipipelinecontext-interface-com.md)


