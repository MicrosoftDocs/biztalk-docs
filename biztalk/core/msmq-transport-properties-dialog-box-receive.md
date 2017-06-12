---
title: "MSMQ Transport Properties Dialog Box, Receive | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.msmq.transport.receive"
helpviewer_keywords: 
  - "MSMQ adapters, receive locations"
  - "properties, MSMQ adapters"
  - "MSMQ adapters, properties"
  - "receive locations, MSMQ adapters"
ms.assetid: 890a00b2-deca-412f-853e-85816c3f0c0d
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSMQ Transport Properties Dialog Box, Receive
Use the **MSMQ Transport Properties** dialog box to configure the receive location properties for the MSMQ adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Password**|Set a password to use for a remote queue.|  
|**User Name**|Determine the user name to use, in combination with the password, for access to a remote queue. You cannot use the local user of the remote computer for the user name.|  
|**Batch Size**|Configure the batch size using this property. BizTalk 2006 Adapter for MSMQ submits messages to the MessageBox database in batches. The default batch size is 0, and the minimum batch size is 1. **Note:**  If the **Transactional** property for the receive location is set to **True**; each message batch is submitted to the MessageBox database under the context of a Microsoft Distributed Transaction Coordinator (MSDTC) transaction. The MSDTC transaction that is created for a message batch remains open until every message in the batch has been persisted to the MessageBox and placed in the appropriate subscriber queue. Therefore the duration of this MSDTC transaction is increased as the **Batch Size** parameter is increased. Since having a large number of MSDTC transactions open simultaneously can negatively impact overall performance, the **Batch Size** parameter should not be set to a very large value when transaction support is enabled.|  
|**Queue**|Type a valid queue path. Depending on the queue path you specify, the system performs the appropriate validations.|  
|**On Failure**|Specify how the adapter should respond to an error. Set this property to one of the following values:<br /><br /> Stop. Stop receiving messages through this receive location if an error condition occurs.<br /><br /> Suspend(non-resumable). Suspend messages and mark as non-resumable.<br /><br /> Suspend(resumable). Suspend messages and mark as resumable. **Important:**  If the True option for Ordered Processing property, the Stop option for the On Failure property, and the False option for the Transactional property are applied at the same time, then any messages that fail delivery will not be suspended or left in the source queue. In this scenario, message loss can occur. To prevent data loss, when using the Ordered Processing feature, the Stop option for the On Failure property should only be applied if the True option for the Transactional property is applied. Then, if a message delivery failure occurs, the original message will be left in the source MSMQ queue. If the Ordered Processing property is set to a value of False then the On Failure property will not take effect and if a message delivery failure occurs the message will be suspended with a status of Suspended (resumable).|  
|**Ordered processing**|Set this property to True or False. This indicates whether to process messages serially. Setting the property to True will accommodate ordered message delivery when used in conjunction with a BizTalk Messaging or Orchestration Send Port that has the Ordered Delivery option set to True. For more information about the Ordered Delivery option, see the appropriate topics in See Also.<br /><br /> Setting this property to True also optimizes resource usage when handling large messages by making the adapter single-threaded. For more information about sending and receiving large messages, see the appropriate topics in See Also.|  
|**Transactional**|Set this property to True or False. **Note:**  The adapter does not support transactional reads on remote queues. <br /><br /> For more information about configuring the MSMQ adapter properties and running adapters within a clustered host, see the appropriate topics in See Also.|  
  
## See Also  
 [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md)   
 [Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md)   
 [Sending and Receiving Large Messages Using the MSMQ Adapter](../core/sending-and-receiving-large-messages-using-the-msmq-adapter.md)   
 [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)