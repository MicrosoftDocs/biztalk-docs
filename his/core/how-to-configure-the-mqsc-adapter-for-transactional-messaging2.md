---
title: "How to Configure the MQSC Adapter for Transactional Messaging2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: affc5625-3c1e-4045-ab5a-d2b65f5c0d06
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Configure the MQSC Adapter for Transactional Messaging
After you install the IBM WebSphere MQ Extended Transactional Client on your BizTalk Server computer, the following additional configuration steps are necessary before you can implement transactional messaging with the BizTalk Adapter for WebSphere MQ.  
  
- In the WebSphere MQ Server environment, give your Network Service account appropriate permissions, as described in the IBM Technote article 1223479. For security reasons, it is strongly recommended that you use the “Security Exit” so that you do not have to add “Network Service” account into the MQM group.  
  
- On your BizTalk Server computer, add the MQSeries XA dll to the MSDTC registry. To the registry key **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTC\XADLL**, add the string value `amqmtsxatmc.dll` in the **Name** column and add its path to the **Data** column. Provide the path in the form `<WebSphere MQ Client installation folder>\bin\amqmtsxatmc.dll`; for example, `C:\Program Files\IBM\WebSphere MQ\bin\amqmtsxatmc.dll`.  
  
- On your BizTalk Server computer, if you are using WebSphere MQ 5.3, give your Network Service account read/write access to the @SYSTEM folder, contained in \<WebSphere MQ Client installation folder>\qmgrs\\@SYSTEM. (You do not have to do this if you are using WebSphere MQ 6.0.)  
  
- Make sure that MSDTC is enabled on the computer on which BizTalk Server is installed and that security is configured as described in the following procedure:  
  
### To enable MSDTC and configure security  
  
1.  Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Component Services**.  
  
2.  In the Console Root of the Component Services Console, expand **Component Services**.  
  
3.  Expand **Computers**.  
  
4.  Right-click **My Computer**, and then click **Start MSDTC**.  
  
5.  Right-click **My Computer**, and then click **Properties**.  
  
6.  Click the **MSDTC** tab.  
  
7.  Under **Transaction Configuration**, click **Security Configuration**.  
  
8.  Under **Security Settings**, select the **Network DTC Access** and **Enable XA Transactions** check boxes.  
  
9. Click **OK**.  
  
## See Also  
 [BizTalk Adapter for WebSphere MQ](../core/biztalk-adapter-for-websphere-mq2.md)