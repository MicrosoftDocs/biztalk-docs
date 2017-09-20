---
title: "How to Create Send Ports for JD Edwards EnterpriseOne | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JD Edwards EnterpriseOne adapters, send ports"
  - "send ports, creating [JD Edwards EnterpriseOne adapters]"
  - "adapters [JD Edwards EnterpriseOne adapters], send ports"
  - "send ports, JD Edwards EnterpriseOne adapters"
  - "creating, send ports [JD Edwards EnterpriseOne adapters]"
ms.assetid: 687f9207-ad3e-41ea-8640-5b9b6efbc14e
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Create Send Ports for JD Edwards EnterpriseOne
Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create a send port.  
  
### To create a send port  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration**.  
  
2.  In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, and expand **Applications**, and then expand the application for which you want to create a send port.  
  
3.  Right-click **Send Ports** and click **New**, and then click **Static Solicit-Response Port**.  
  
4.  In the **Send Port Properties** dialog box, do the following:  
  
    -   In the **Name** box, type a send port name (for example, `SendToJDE`).  
  
    -   From the **Type** drop-down list, select **JDEdwards**.  
  
    -   From the **Send handler** drop-down list, select the send handler address.  
  
5.  Click **OK**.  
  
## See Also  
 [Creating JD Edwards EnterpriseOne Send Handlers](../core/creating-jd-edwards-enterpriseone-send-handlers.md)