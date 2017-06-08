---
title: "_BatchOperationType Enumeration (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b12c20fd-9f2b-4ba3-92b5-3e57d7eaaa07
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# _BatchOperationType Enumeration (COM)
Defines the types of operations that can occur within a batch.  
  
> [!NOTE]
>  For information on using this interface within managed code, see the `BatchOperationType Enumeration`.  
  
## Members  
  
|Member name|Value|Description|  
|-----------------|-----------|-----------------|  
|**BT_CancelResponse**|6|Corresponds to the [CancelResponseMessage](../core/ibttransportbatch-cancelresponsemessage-method-com.md) method on [IBTTransportBatch](../core/ibttransportbatch-interface-com.md).<br /><br /> A request for a response message was canceled.|  
|**BT_Delete**|1|Corresponds to the [DeleteMessage](../core/ibttransportbatch-deletemessage-method-com.md) method on [IBTTransportBatch](../core/ibttransportbatch-interface-com.md).<br /><br /> A message to be deleted was added to the batch.|  
|**BT_MoveToNextTransport**|4|Corresponds to the `MoveToNextTransport` method on [IBTTransportBatch](../core/ibttransportbatch-interface-com.md).<br /><br /> A message to be moved to the backup adapter was added to the batch.|  
|**BT_MoveToSuspendQ**|2|Corresponds to the [MoveToSuspendQ](../core/ibttransportbatch-movetosuspendq-method-com.md) method on [IBTTransportBatch](../core/ibttransportbatch-interface-com.md).<br /><br /> A message to be suspended was added to the batch.|  
|**BT_Resubmit**|3|Corresponds to the [Resubmit](../core/ibttransportbatch-resubmit-method-com.md) method on [IBTTransportBatch](../core/ibttransportbatch-interface-com.md).<br /><br /> A message to be resubmitted was added to the batch.|  
|**BT_Submit**|0|Corresponds to the [SubmitMessage](../core/ibttransportbatch-submitmessage-method-com.md) method on [IBTTransportBatch](../core/ibttransportbatch-interface-com.md).<br /><br /> A message to be submitted was added to the batch.|  
|**BT_SubmitRequest**|5|Corresponds to the [SubmitRequestMessage](../core/ibttransportbatch-submitrequestmessage-method-com.md) method on [IBTTransportBatch](../core/ibttransportbatch-interface-com.md).<br /><br /> A request message for a request-response message exchange was added to the batch.|  
