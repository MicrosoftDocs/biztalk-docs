---
title: "Setting Time-Outs for a Public-Process Orchestration and an HTTP Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "public processes, HTTP adapters"
  - "public processes, orchestrations"
  - "orchestrations, time-outs"
  - "public processes, time-outs"
  - "orchestrations, public-process orchestrations"
  - "HTTP adapters, public processes"
  - "HTTP adapters, time-outs"
ms.assetid: 82fd64ac-6191-410c-94b3-8a3d1ff2611f
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Setting Time-Outs for a Public-Process Orchestration and an HTTP Adapter
When you use a public-process orchestration with an HTTP adapter in a synchronous scenario, you must set the time-outs for each appropriately. The time-out setting for the orchestration (Time to Perform) must be smaller than the time-out for the HTTP adapter (Request Timeout). This is because if the setting for the HTTP adapter is smaller, the adapter could time out before the orchestration. This gives the adapter control of the process. The orchestration must be in control of the process; therefore, its time-out setting must be smaller.  
  
### To set the time-out setting for the HTTP adapter  
  
1.  In BizTalk Explorer, expand **Send ports**, and then double-click the HTTP send port used with the public-process orchestration.  
  
2.  In the Send Port Properties window, click the ellipsis button (**...**) for **Address (URI)**.  
  
3.  In the HTTP Transport Properties window, in the General pane, in the **Request timeout (sec.)** box, type an appropriate value for the time-out. This value must be larger than the **Time to Perform** setting for the relevant Partner Interface Process (PIP).  
  
4.  Click **OK**, and then click **OK** again.  
  
### To set the time-out setting for the public-process orchestration  
  
1. Click **Start**, point to **All Programs**, point to **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, and then click  **BizTalk Accelerator for RosettaNet Management Console**.  
  
2. Expand [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click **Process Configuration Settings**.  
  
3. Right-click the PIP that you want to set the time-out setting for, and then click **Properties**.  
  
4. In theProperties dialog box, on the **Activity** tab, in the **Time to Perform** box, type an appropriate value that is smaller than the HTTP adapter time-out setting, and then click **OK**.  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)