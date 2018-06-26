---
title: "Sending a Preserved Batch Interchange | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9bc2207-e34d-4d06-a224-bd7f8e498c27
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sending a Preserved Batch Interchange
When the EDI send pipeline processes an outbound preserved batch interchange, it processes the batched interchange as a whole. It normally reuses the existing envelope (control) segments in creating the EDI interchange, rather than applying an envelope based upon the agreement. This occurs when the **Inbound batch processing option** property is set to **Preserve Interchange - suspend Interchange on Error** or **Preserve Interchange - suspend Transaction Sets on Error**.  
  
## Schema Validation  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] validates the envelope of a preserved batch using the batch schemas and the service schemas. The batch schema is used to validate the root node of the preserved message; the service schemas are used to validate the interchange, group, and transaction set headers and trailers. For more information about the batch schemas, see [EDI Batch Schemas](../core/edi-batch-schemas.md). For more information on the service schemas, see [EDI Service and Control Schemas](../core/edi-service-and-control-schemas.md).  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] validates the documents in a batched interchange using the document schemas in your project.  
  
## Send-Side Processing  
 When the EDI Assembler processes a preserved interchange, it normally uses the same interchange, group, and transaction-set headers that existed in the batched interchange when it was received.  
  
- For X12 interchanges, the property settings on different pages in the one-way agreement tab in the **Agreement Properties** dialog box (which determine how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will create the ISA, GS, and ST headers of an outgoing interchange) do not normally apply.  
  
- For EDIFACT interchanges, the UNA settings in the agreement properties are normally used. The UNA segment is optional in an EDIFACT-encoded message, but it is required for serializing a preserved batch interchange. If there is no value for the UNA segment in the XML instance, the default property values for the send pipeline component will be used. If the send pipeline component properties are not valued, then the preserved batch intermediate XML message will be suspended.  
  
- If you promote the `EDI.PopulateInterchangeValues` context property to "True" on the interchange being preserved (in a custom component), the EdiAssembler in the send port will populate all of the interchange, group, and transaction-set headers to the values set in the agreement properties.  
  
- If you promote the `EDIOverride.OverrideEdiHeader` context property to “True” on the interchange before it is processed by the send pipeline, you can override the envelope values for the outbound document by setting the appropriate `EDIOverride` context property values. For more information, see [Overriding EDI Headers](../core/overriding-edi-headers.md).  
  
  For a preserved interchange that has no errors, the Assembler will preserve the sequence of transaction sets in a group of the interchange and the sequence of groups in the interchange.  
  
> [!NOTE]
>  You can send a preserved batch with an XML send pipeline. However, to do so requires that you change the namespace for the batch schema. For more information, see [Sending a Preserved Batch with an XML Send Pipeline](../core/sending-a-preserved-batch-with-an-xml-send-pipeline.md).  
  
## Error Processing  
 The EDI send pipeline recognizes a batched EDI interchange as a preserved batch because of a reserved tag in the XML. This tag, either \<X12InterchangeXml\> or \<EdifactInterchangeXml\>, is applied to the XML by the EDI receive pipeline.  
  
 The following special cases apply to suspending transaction sets on error:  
  
-   If all transaction sets in a group are invalid, then the EDI send pipeline will include group control segments in the generated EDI, but the group will not contain any transaction sets (because they will have been dropped). The group footer totals are updated to zero. The interchange control segments remain unchanged.  
  
-   If all transaction sets in an interchange are invalid, then the interchange control segments will still be included in the generated EDI interchange, but the interchange will not contain any transaction sets (because they will have been dropped). This would constitute an empty interchange.  
  
-   If the group control segments or the interchange control segments are invalid, an EDI-encoded interchange will not be generated. A log will be created in the event viewer indicating that the interchange was rejected.  
  
## See Also  
 [Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md)