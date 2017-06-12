---
title: "IBTTransportBatch Members (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59bb0b1f-6599-426b-858b-ddf2bd733d26
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransportBatch Members (COM)
[IBTTransportBatch overview](../core/ibttransportbatch-interface-com.md)  
  
## Public Properties  
  
|||  
|-|-|  
|![](../core/media/pubproperty.gif "pubproperty") [ResourceTracker](../core/ibttransportbatch-resourcetracker-property-com.md)|This property is not supported and returns a value of E_NOTIMPL.|  
  
## Public Methods  
  
|||  
|-|-|  
|![](../core/media/pubmethod.gif "pubmethod") [CancelResponseMessage](../core/ibttransportbatch-cancelresponsemessage-method-com.md)|Adds a cancellation request to the batch to cancel a request for a response message.|  
|![](../core/media/pubmethod.gif "pubmethod") [Clear](../core/ibttransportbatch-clear-method-com.md)|Clears the batch.|  
|![](../core/media/pubmethod.gif "pubmethod") [DeleteMessage](../core/ibttransportbatch-deletemessage-method-com.md)|Adds a message to the batch to be deleted.|  
|![](../core/media/pubmethod.gif "pubmethod") [Done](../core/ibttransportbatch-done-method-com.md)|Posts the batch of work to the thread pool for the BizTalk Server Messaging Engine where it will be processed asynchronously.|  
|![](../core/media/pubmethod.gif "pubmethod") [MoveToNextTransport](../core/ibttransportbatch-movetonexttransport-method-com.md)|Adds a message to the batch to be moved to the backup transport.|  
|![](../core/media/pubmethod.gif "pubmethod") [MoveToSuspendQ](../core/ibttransportbatch-movetosuspendq-method-com.md)|Adds a message to the batch to be suspended.|  
|![](../core/media/pubmethod.gif "pubmethod") [Resubmit](../core/ibttransportbatch-resubmit-method-com.md)|Adds a message to the batch to be resubmitted.|  
|![](../core/media/pubmethod.gif "pubmethod") [SubmitMessage](../core/ibttransportbatch-submitmessage-method-com.md)|Adds a message to the batch to be processed by the BizTalk Server Messaging Engine.|  
|![](../core/media/pubmethod.gif "pubmethod") [SubmitRequestMessage](../core/ibttransportbatch-submitrequestmessage-method-com.md)|Submits a request message for a request-response pair.|  
|![](../core/media/pubmethod.gif "pubmethod") [SubmitResponseMessage](../core/ibttransportbatch-submitresponsemessage-method-com.md)|Submits the response message for a solicit-response pair.|  
  
## See Also  
 [IBTTransportBatch Interface (COM)](../core/ibttransportbatch-interface-com.md)