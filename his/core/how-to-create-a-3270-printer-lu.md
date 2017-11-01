---
title: "How to Create a 3270 Printer LU1 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9ca80fb-c5bd-4dec-9e6c-362473f48e68
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Create a 3270 Printer LU
The following procedure details how to create a printer LU.  
  
### To create a 3270 printer LU  
  
1.  In SNA Manager, expand **Servers**, expand **SNA Service**, and then expand **Connections**.  
  
2.  Right-click the appropriate connection, **DM3270**, point to **New**, and then click **Printer LU**.  
  
     You can define LUs in this **Properties** dialog box. Keep the default for the **LU Number** box as 3. Three is the first available number, because two was used in the previous example and one is reserved for the host.  
  
     The LU number is meaningful to the connection. You can add a user-friendly name in the **LU Name** box.  
  
3.  Type the LU Name, **LU 4**. (You might have expected LU 3, but LU 3 is reserved for the LU3 demo.) Leave the other boxes as they are.  
  
4.  Type a comment (optional).  
  
5.  If you are using compression, select the **Use Compression** box.  
  
6.  If the workstation is secured, select the **User Workstation Secured** box.  
  
7.  Click **OK**.  
  
## See Also  
 [IP-DLC Link Service](../Topic/IP-DLC%20Link%20Service1.md)   
 [How to Create a 3270 Display LU](../core/how-to-create-a-3270-display-lu.md)   
 [How to Create a 3270 Application LU (LUA)](../core/how-to-create-a-3270-application-lu-lua.md)   
 [How to Create a 3270 Downstream LU](../core/how-to-create-a-3270-downstream-lu.md)   
 [How to Create a Local APPC LU](../core/how-to-create-a-local-appc-lu.md)   
 [How to Create a Remote APPC LU](../core/how-to-create-a-remote-appc-lu.md)   
 [Creating LUs](../core/creating-lus.md)