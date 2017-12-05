---
title: "Connection Properties: Channel2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SNA_PU_CHANNEL"
ms.assetid: 3c368eac-1724-4ca7-a33d-22bf77bbd734
caps.latest.revision: 4
---
# Connection Properties: Channel
The following tabs are available on the Channel Connection Properties sheet:  
  
## Connection Properties: Address  
 **Channel Address**  
 Type a two-digit hexadecimal number identifying the channel. The range is from 00 through FF; the default is **FF**.  
  
 **Control Unit Image Number**  
 Type a value for the control unit image number. The range is 0 through F; the default is **0**.  
  
 **Affiliate Application**  
 If you selected Single Sign-On, choose an Affiliate Application from the list. The Enterprise Single Sign-On (SSO) Affiliate applications are logical entities that represent a system or sub-system such as a host, back-end system, or line of business application to which you are connecting using SSO. An affiliate application can represent a back-end system such as a mainframe or UNIX computer. It can also represent an application such as SAP, or a subdivision of the system, such as the "Benefits" or "Pay stub" sub-systems.  
  
## Connection Properties: Channel  
 **Max BTU Length**  
 Specify the Maximum Basic Transmission Unit (BTU) Length.  
  
 The range is from 265 through 16393; the default is **265**.  
  
 With an IBM SDLC adapter, set the Max BTU Length to 521 or less.  
  
 This is the maximum number of bytes that can be transmitted in a single data-link information frame. A BTU is sometimes called an I-frame.  
  
 For downstream connections, specify a Max BTU Length less than or equal to the maximum value supported by software on the downstream system.  
  
 For host connections, specify a Max BTU Length less than or equal to the VTAM PU definition for the MAXDATA= parameter.  
  
 **Connection Retry Limits**  
 Supply activation limits for the connection.  
  
 **Maximum Retries**  
 Select the number of attempts for [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] to make when trying to establish the connection. After making this number of attempts, Host Integration Server makes an entry in the event log and stops trying. The range is from 1 through No Limit; the default is **No Limit**.  
  
 **Delay After Failure**  
 Select the length of time for Host Integration Server to wait between attempts to establish the connection. The range is from 5 seconds through 255 seconds; the default is **10** seconds.  
  
## See Also  
 [SNA Manager Help](../core/sna-manager-help2.md)