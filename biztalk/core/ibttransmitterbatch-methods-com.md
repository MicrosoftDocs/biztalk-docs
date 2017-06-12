---
title: "IBTTransmitterBatch Methods (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59f297d0-bc25-43cd-a92f-aecf9197c0f3
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTTransmitterBatch Methods (COM)
The methods of the **IBTTransmitterBatch** interface are listed here. For a complete list of **IBTTransmitterBatch** interface members, see the [IBTTransmitterBatch Members](../core/ibttransmitterbatch-members-com.md) topic.  
  
## Public Methods  
  
|||  
|-|-|  
|![](../core/media/pubmethod.gif "pubmethod") [BeginBatch](../core/ibttransmitterbatch-beginbatch-method-com.md)|Initializes the batch.|  
|![](../core/media/pubmethod.gif "pubmethod") [Clear](../core/ibttransmitterbatch-clear-method-com.md)|Clears the batch if one or more calls to the [TransmitMessage](../core/ibttransmitterbatch-transmitmessage-method-com.md) method failed.|  
|![](../core/media/pubmethod.gif "pubmethod") [Done](../core/ibttransmitterbatch-done-method-com.md)|Indicates that either the batch is full or the BizTalk Server Messaging Engine does not have any more messages for this batch.|  
|![](../core/media/pubmethod.gif "pubmethod") [TransmitMessage](../core/ibttransmitterbatch-transmitmessage-method-com.md)|Adds messages to the adapter batch that are ready to be transmitted.|  
  
## See Also  
 [IBTTransmitterBatch Interface (COM)](../core/ibttransmitterbatch-interface-com.md)