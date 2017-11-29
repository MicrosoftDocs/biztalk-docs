---
title: "How to Create a Local APPC LU1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dadae4a3-1b5b-4b77-b6ad-0bb0a3917e17
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Create a Local APPC LU
The following procedure details how to create a local APPC LU.  
  
### To create a local APPC LU  
  
1.  In SNA Manager, expand **Servers**, expand **SNA Service**, and then expand **Local APPC LUs**.  
  
2.  Right-click **Local APPC LUs**, point to **New**, and then click **Local LU**.  
  
3.  On the **General** tab:  
  
    -   Type the LU Alias.  
  
    -   Type the Network Name.  
  
    -   Type the LU Name.  
  
    -   Type a comment (optional).  
  
4.  On the **Advanced** tab:  
  
    -   If you are a member of the local APPC LU pool, select the **Member of Default Outgoing Local APPC LU Pool** box.  
  
    -   Type the amount of time in seconds for **Timeout for Staring Invokable TPs**.  
  
    -   Select the **Implicit Incoming Remote LU**.  
  
    -   Select the **LU 6.2 Type (Independent or Dependent)**.  
  
    -   Select **SyncPoint Support** if required.  
  
5.  Click **OK**.  
  
## See Also  
 [IP-DLC Link Service](../Topic/IP-DLC%20Link%20Service1.md)   
 [How to Create a 3270 Display LU](../core/how-to-create-a-3270-display-lu.md)   
 [How to Create a 3270 Printer LU](../core/how-to-create-a-3270-printer-lu.md)   
 [How to Create a 3270 Application LU (LUA)](../core/how-to-create-a-3270-application-lu-lua.md)   
 [How to Create a 3270 Downstream LU](../core/how-to-create-a-3270-downstream-lu.md)   
 [How to Create a Remote APPC LU](../core/how-to-create-a-remote-appc-lu.md)   
 [Creating LUs](../core/creating-lus.md)