---
title: "Preserving a Received Batched EDI Interchange | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10d21b9b-9684-422a-8948-8bd71a4d5a10
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Preserving a Received Batched EDI Interchange
> [!NOTE]
>  All the user interface options mentioned in this topic are available in the **Local Host Settings** page (**Receiver’s Settings** section) of the bi-directional agreement tabs in the **Agreement Properties** dialog box.  

 When the EDI receive pipeline preserves an inbound batched EDI interchange, the normal parsing of each transaction set/message into separate intermediate XML files is not performed. The EDI receive pipeline processes the interchange as one document without splitting the transaction sets/messages. This occurs when the **Inbound batch processing option** property is set to **Preserve Interchange - suspend Interchange on Error** or **Preserve Interchange - suspend Transaction Sets on Error**.  

 **Schema Validation**  

 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] validates the envelope of a preserved batch using the batch schemas and the service schemas. The batch schema is used to validate the root node of the preserved message; the service schemas are used to validate the interchange, group, and transaction set headers and trailers. For more information about the batch schemas, see [EDI Batch Schemas](../core/edi-batch-schemas.md). For more information on the service schemas, see [EDI Service and Control Schemas](../core/edi-service-and-control-schemas.md).  

 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] validates the documents in a batched interchange using the document schemas in your project.  

 **Receive-Side Processing**  

 The EDI Disassembler processes preserved batches as follows:  

- When the EDI Disassembler processes a batch to be preserved, it converts the flat file format to XML and adds the X12InterchangeXML or EdifactInterchangeXML as the XML root node. This indicates to the send pipeline that the batched interchange should be preserved, and indicates that the Edifact_BatchSchema schema or X12_BatchSchema schema should be used to validate the root node.  

- The Disassembler adds the DelimiterSetSerializedData attribute to the root node of a batched XML message to indicate the separators to be used by the send pipeline when generating a batched EDI interchange from the XML message. When the XML message is a preserved batch, the attribute is populated by the receive pipeline from the separators used in the incoming message. When the batched XML is produced by the batching orchestration, the attribute is populated from the value specified in agreement properties.  

- The Disassembler uses one of the following namespaces when it creates an XML-encoded preserved interchange: `http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006/InterchangeXML` or `http://schemas.microsoft.com/BizTalk/EDI/X12/2006/InterchangeXML`.  

- The Disassembler promotes the context property `EDI.ReuseEnvelope == True` to identify the interchange as preserved. This enables you to create a send port that subscribes to all batched interchanges that are preserved.  

  > [!NOTE]
  >  A HIPAA document will not be split into subdocuments if the **Inbound batch processing option** is set to **Preserve Interchange**. This will be the case even if the subdocument creation break annotation within the HIPAA schema is set to "Yes".  

  **Error Processing**  

  If you have selected **Preserve Interchange - suspend Interchange on Error** for the **Inbound batch processing option**, the entire interchange will be suspended as a result of any error. If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] suspends the entire preserved interchange, the interchange structure and the ordering of the transaction sets within the interchange will be preserved. In the event of an error, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will post one consolidated error entry in the event log. This entry will include any errors in the interchange, functional group, and transaction set levels.  

  If you have selected **Preserve Interchange - suspend Transaction Sets on Error** for the inbound batch processing option, the EDI receive pipeline will drop any invalid transaction set from the interchange and proceed with the creation of the interchange XML. The resulting interchange XML is required to reuse the existing control segment envelopes (ISA, GS, GE, and IEA for X12-encoded interchanges or UNA, UNB, UNG, UNE, and UNZ for EDIFACT-encoded interchanges). The interchange will be considered a successfully processed document; however, the error will be reported in the event viewer and if a functional acknowledgment is generated, it will report the error. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will create a separate entry in the event log for each transaction set that is in error. If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] drops an erroneous transaction set from the interchange, the interchange structure and ordering may not be preserved. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will update the number of transaction sets in the interchange.  

  The following special cases apply to suspending transaction sets on error:  

- If all transaction sets in a group are invalid, then each transaction set is suspended individually; however, the group control segments (with no transaction sets, because they have been dropped) will be included in the generated interchange XML.  

- If all transaction sets in an interchange are invalid, then each transaction set is suspended individually; however, the interchange control segments (with no transaction sets, because they have been dropped) will be included in the generated interchange XML.  

- If the group control segments are invalid, all transaction sets in the group will be suspended individually.  

- If the interchange control segments are invalid, all transaction sets in the interchange will be suspended individually, and the interchange XML will not be generated. A log in the event viewer will be created for the rejected interchange.
