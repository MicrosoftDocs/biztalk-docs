---
title: "MQSeries Transport Properties Dialog Box, Send | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.adaptors.mqseries.transport.send"
helpviewer_keywords: 
  - "MQSeries adapters, send ports"
  - "properties, MQSeries adapters"
  - "send ports, MQSeries adapters"
  - "MQSeries adapters, properties"
ms.assetid: 5a9ae8e2-9d5c-411e-b9b6-7f625c26a082
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSeries Transport Properties Dialog Box, Send
Use the **MQSeries Transport Properties** dialog box to configure send port for the MQSeries adapter.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Fragmentation Size**|Sets the message chunk size in KB for messages as they are sent between the adapter and MQSAgent.|  
|**SSO Affiliate Application**|Sets the Single Sign-On (SSO) affiliate application. The user ID and password from SSO are used for the MQMD_UserIdentifier, and the MQIIH_Authenticator (or MQCIH_Authenticator) property, respectively.<br /><br /> Default: Blank|  
|**Data Conversion**|Converts the message to the ANSI code page of MQSeries for Windows Server.<br /><br /> Select Yes to perform this conversion from Unicode to ANSI.<br /><br /> Default: No|  
|**Ordered**|Sets MQSeries to maintain the order of messages as they are sent to the MQSeries queue.<br /><br /> Select Yes to maintain message order. **Note:**  You must set the Delivery Notification property in your orchestration to Transmitted for the send port. <br /><br /> Default: No|  
|**Queue Definition**|Populated with information from the Queue Definition dialog box or directly in the field.|  
|**Segmentation Allowed**|Uses MQSeries Queue Manager segmentation if an individual message exceeds the MQSeries queue maximum message length. If you select Yes, MQSeries puts segmented messages into the queue.<br /><br /> Default: No|  
|**Transaction Supported**|The adapter begins a Distributed Transaction Coordinator (DTC) transaction between BizTalk Server and MQSeries server. When set to No, there is no guarantee of message delivery.<br /><br /> Default: Yes|  
  
## See Also  
 [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)