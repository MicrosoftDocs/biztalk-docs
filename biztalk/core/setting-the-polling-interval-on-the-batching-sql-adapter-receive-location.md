---
title: "Setting the Polling Interval on the Batching SQL Adapter Receive Location | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "polling interval [receive adapters]"
  - "SQL adapters, polling interval"
  - "receive locations, polling interval"
  - "SQL adapters, receive locations"
  - "receive locations, SQL adapters"
ms.assetid: 9053b20d-145a-4445-b414-c0482cf975a0
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Setting the Polling Interval on the Batching SQL Adapter Receive Location
You can set the polling interval on the batching SQL adapter receive location (**BatchControlMessageRecvLoc**) differently on development and production computers. On a development server, Microsoft recommends that you keep the polling interval at the default of 30 seconds, for quick activation of the batching orchestration for an agreement. However, on a production server, a setting of 30 seconds may affect performance. Once you have activated a batch, you may want to set the polling interval to a higher value, such as five minutes.  
  
 For more information about parties, see [Managing Parties](../core/managing-parties.md).  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To set the Polling Interval on the Batching SQL Adapter Receive Location  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **BizTalk EDI Application**, and then click **Receive Locations**. Right-click **BatchControlMessageRecvLoc**, and click **Properties**.  
  
2. In the **Receive Location Properties** dialog box, in the **Transport** section, click **Configure**.  
  
3. In the **SQL Transport Properties** dialog box, change the value for **Polling Interval** from the default value of "30" to the desired value. The recommended value for a production server is "5".  
  
4. Change the value of **Polling Unit of Measure** from the default value of **Seconds** to **Minutes**.  
  
5. Click **OK**, and then click **OK** again  
  
## See Also  
 [Managing EDI and AS2 Solutions](../core/managing-edi-and-as2-solutions.md)