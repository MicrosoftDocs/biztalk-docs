---
title: "Sending a Preserved Batch with an XML Send Pipeline | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6765576a-134f-4856-911c-2f603b6479bd
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Sending a Preserved Batch with an XML Send Pipeline
Normally, a preserved batch is sent using an EDI send pipeline. However, you can also use an XML send pipeline to send a preserved batch. Since the preserved batch that is generated and dropped in the MessageBox by the EDI receive pipeline is in the XML format, the XML send pipeline would pass along the batch in XML format.  
  
 To send a preserved batch using the XML send pipeline, you have to deploy a project with the applicable batch schema and the document schemas for each message type in the interchange. In addition, you also have to change the namespace for the batch schema that you deploy in the project. If you do not do so, the namespace in the preserved batch XML file would not correspond to the namespace for the batch schema. You have to change the namespace for the batch schema as shown in the following table:  
  
|For this encoding type:|Change this namespace in the batch schema:|To the following namespace:|  
|-----------------------------|------------------------------------------------|---------------------------------|  
|EDIFACT|`http://schemas.microsoft.com/Edi/Edifact`|`http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006/InterchangeXML`|  
|X12|`http://schemas.microsoft.com/Edi/X12_BatchSchema`|`http://schemas.microsoft.com/BizTalk/EDI/X12/2006/InterchangeXML`|  
  
 This is not an issue with the EDI Assembler.  
  
## See Also  
 [Configuring EDI Batches](../core/configuring-edi-batches.md)