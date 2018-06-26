---
title: "BizTalk Message Queuing Large Message Extension | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BizTalk Message Queuing Large Message Extension"
  - "utilities, BizTalk Message Queuing Large Message Extension"
ms.assetid: 5d6892d3-fda8-41a3-8111-d28c11bd71fb
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Message Queuing Large Message Extension
Native message queuing cannot process a message with a body larger than 4megabytes (MB). However, Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes an add-on for native message queuing that permits processing messages larger than 4 MB. This add-on is delivered as the Mqrtlarge.dll file, and exposes the **MQSendLargeMessage** and **MQReceiveLargeMessage** application programming interfaces (APIs), and the analogous COM model. These functions are implemented as standard message queuing APIs, **MQSendMessage** and **MQReceiveMessage** respectively.  

 To participate in large message exchanges, the message queuing computer must have the Mqrtlarge.dll file installed, and the message queuing application should use the add-on APIs. Otherwise, complete messages will be fragmented.  

 **Location in SDK**  

 \<*Installation Path*\>\SDK\ Mqrtlarge.dll  

 **File Inventory**  

 The following table shows the file this utility uses and describes its purpose.  


|    File(s)    |                                                                                                                                                                                              Description                                                                                                                                                                                               |
|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Mqrtlarge.dll | A Win32 dynamic-link library that exposes **MQSendLargeMessage** and **MQReceiveLargeMessage**.<br /><br /> The header files are located in the *\<Installation Path\>*\SDK\Include directory. **Note:**  You must install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] onto a 64 bit version of Windows in order to access the 64 bit version of Mqrtlarge.dll. |

 **Using This Utility**  

 Use the following procedure to run the Mqrtlarge.dll file.  

### To use the Mqrtlarge.dll file  

1. > [!NOTE]
   >  For an MSMQ solution without BizTalk Server, the MQRTLarge.dll may still function correctly. However, this is not a recommended configuration that Microsoft supports, and unexpected results may occur if used outside of the BizTalk Server environment.  

    Add the file Mqrtlarge.dll to the computer that does not contain an installation of BizTalk Server. Message Queuing uses Mqrtlarge.dll to send or receive messages to or from BizTalk Server.  

2. To access the APIs in the Mqrtlarge.dll file, add a reference to the Mqrtlarge.dll file in the applications that send or receive messages to or from other computers to the BizTalk Message Queuing endpoint.  

   **Remarks**  

   Large messages are sent to standard Message Queuing (also known as MSMQ) queues. You should use only the large message APIs on such queues, although this is not enforced.  

   You can still use **MQSendMessage** to send messages to a queue to which you sent large messages. Likewise, you can use **MQReceiveMessage** to receive messages from such queues, although it is not recommended because it may impact the performance of the **MQReceiveLargeMessage** API.  

   For recovery purposes, it is recommended that you use **DEAD_LETTER** journaling.  

   **Fragmentation**  

   In general, a large message will be fragmented into numerous messages, each smaller than 4 MB. It is important to understand that only the body is fragmented. The rest of the properties are sent with each fragment.  

   The number of fragments is defined by the size of the message and the size of the fragments. The fragment size may be automatically determined by the file Mqrtlarge.dll or the appropriate part of BizTalk Message Queuing. Applications can also explicitly specify the fragment size.  

   Note that the large message extension requires extending the message by adding additional internal data of a constant size.  

   **PROPID_M_EXTENSION**  

   You can use the **PROPID_M_EXTENSION/PROPID_M_EXTENSION_LEN** properties to sign the message. The signature comprises 40 bytes (B). The following table shows signature fragments.  

|Description|Size|  
|-----------------|----------|  
|Globally unique identifier (GUID) denoting that this message was sent using **MQSendLargeMessage**|16 B|  
|GUID for the message: unique per-large message ID that is common to all parts of the message|16 B|  
|Total size of the large message|4 B|  
|Part number|2 B|  
|Number of message parts|2 B|  

 The decision to use **PROPID_M_EXTENSION** has an additional implication. The Microsoft Host Integration Server MSMQ-MQSeries Bridge uses this property to pass a structure that contains properties that are not mapped directly between MQSeries and Message Queuing messages. Applications that send messages to and from MQSeries explicitly or implicitly use this structure. Message Queuing can generate acknowledgments when a message has been received from a queue by a receiving application. The acknowledgments are sent to a queue specified by the sending application. In the case of large messages, you send this acknowledgment only for the last part of the large message.  

## See Also  
 [Utilities in the SDK](../core/utilities-in-the-sdk.md)