---
title: "MSMQ Transport Properties Dialog Box, Send | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.msmq.transport.send"
helpviewer_keywords: 
  - "MSMQ adapters, send ports"
  - "send ports, MSMQ adapters"
  - "properties, MSMQ adapters"
  - "MSMQ adapters, properties"
ms.assetid: bd8061c0-ee26-4ccb-9862-274abf6f10f5
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSMQ Transport Properties Dialog Box, Send
Use the **MSMQ Transport Properties** dialog box to configure the send port properties for the MSMQ adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Password**|Specify the password for a remote queue. Use with User Name.|  
|**User Name**|Specify the user name for a remote queue. Use with Password. You cannot use the local user of the remote computer for the user name.|  
|**Acknowledgement Type**|Specify the type of acknowledgement message for Message Queuing to return to the sending application. You can check more than one acknowledgment type. Any of the acknowledgement types in the System.Messaging.AcknowledgeTypes enumeration are available.|  
|**Administration Queue**|Specify the queue name that receives the acknowledgement message. You must specify a value for the Administration Queue if you specify a value for the Acknowledgement Type.|  
|**Body Type**|Specify the message body type in MSMQ. Valid values are members of the .NET VarEnum enumeration.|  
|**Certificate Thumbprint**|Specify the thumbprint of the certificate to use for message authentication. Use this property in combination with the Use Authentication property to verify the message. Use the User Name and Password properties to gain access to queues.|  
|**Destination Queue**|Specify the destination queue. For more information about queues, see the appropriate topics in See Also.|  
|**Encryption Algorithm**|Select RC2, RC4, or None for the encryption algorithm.|  
|**Maximum Message Size (in kilobytes)**|Specify the maximum message size for messages that you send to the specified queue.|  
|**Message Priority**|Set the message priority.|  
|**Recoverable**|Specify whether to guarantee if a message is recoverable.|  
|**Support Segmentation**|Set this Boolean property value to True to segment messages larger than 4 MB.|  
|**Timeout**|Specify the maximum time to wait for the messages to reach the destination queue. Applies only when you use transactions.|  
|**Timeout Unit**|Set the unit to use for the Timeout property.<br /><br /> Select Days, Hours, Minutes, or Seconds.|  
|**Transactional**|Set this value to True to send messages if you use transactions.|  
|**Use Authentication**|Set this Boolean property value to True to control authentication. Use this property in combination with the Certificate Thumbprint property to verify the message. Use the User Name and Password properties to gain access to queues.|  
|**Use Dead Letter Queue**|Set this value to True to send messages to the dead letter queue if a failure occurs.|  
|**Use Journal Queue**|Set this value to True to save a copy of the message whenever the message is processed.|  
  
## See Also  
 [How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md)   
 [Message Queuing Queues](../core/message-queuing-queues.md)