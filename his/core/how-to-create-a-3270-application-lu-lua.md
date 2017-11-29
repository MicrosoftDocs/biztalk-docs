---
title: "How to Create a 3270 Application LU (LUA)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8aa90bcb-f0bf-45e0-8907-babc7aebb33c
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# How to Create a 3270 Application LU (LUA)
The following procedure details how to create an application LU (LUA).  
  
### To create a 3270 application LU (LUA)  
  
1.  In SNA Manager, expand **Servers**, expand **SNA Service**, and then expand **Connections**.  
  
2.  Right-click the appropriate connection, **DM3270**, point to **New**, and then click **Application LU (LUA)**.  
  
     You can define LUs in this **Properties** dialog box. Keep the default for the **LU Number** box as 4. Four is the next available number, because two and three were used in the previous examples, and one is reserved for the host.  
  
     The LU number is meaningful to the connection. You can add a user-friendly name in the **LU Name** box.  
  
3.  Type the LU Name, **LU 5**. Leave the other boxes as they are.  
  
4.  Type a comment (optional).  
  
5.  If you are using compression, select the **Use Compression** box.  
  
6.  If the workstation is secured, select the **User Workstation Secured** box.  
  
7.  If you require high priority mode, select the **High Priority Mode** box.  
  
8.  Click **OK**.  
  
## See Also  
 [IP-DLC Link Service](../Topic/IP-DLC%20Link%20Service1.md)   
 [How to Create a 3270 Display LU](../core/how-to-create-a-3270-display-lu.md)   
 [How to Create a 3270 Printer LU](../core/how-to-create-a-3270-printer-lu.md)   
 [How to Create a 3270 Downstream LU](../core/how-to-create-a-3270-downstream-lu.md)   
 [How to Create a Local APPC LU](../core/how-to-create-a-local-appc-lu.md)   
 [How to Create a Remote APPC LU](../core/how-to-create-a-remote-appc-lu.md)   
 [Creating LUs](../core/creating-lus.md)