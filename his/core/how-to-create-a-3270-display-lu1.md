---
description: "Learn more about: How to Create a 3270 Display LU"
title: "How to Create a 3270 Display LU1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e763444-a7e5-4826-b90c-b334795f0294
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# How to Create a 3270 Display LU
The following procedure details how to create a display LU.  
  
### To create a 3270 display LU  
  
1.  In SNA Manager, expand **Servers**, expand **SNA Service**, and then expand **Connections**.  
  
2.  Right-click the appropriate connection, **DM3270**, point to **New**, and then click **Display LU**.  
  
     You can define LUs in this **Properties** dialog box. Keep the default for the **LU Number** box as 2. Two is the first available number, because one is reserved for the host.  
  
     The LU number is meaningful to the connection. You can add a user-friendly name in the **LU Name** box.  
  
3.  Type the LU Name, **LU 2**. Leave the other boxes as they are.  
  
4.  Click the **Display Model** tab and choose **2 (24 X 80)** as the display station model. Because models can change without notification, click **Model can be overridden**.  
  
5.  Click the **Associated Printer** tab. When configuring an LU, these boxes are generally left blank.  
  
6.  Click **OK**.  
  
## See Also  
 [IP-DLC Link Service](./ip-dlc-link-service2.md)   
 [How to Create a 3270 Printer LU](../core/how-to-create-a-3270-printer-lu1.md)   
 [How to Create a 3270 Application LU (LUA)](../core/how-to-create-a-3270-application-lu-lua-2.md)   
 [How to Create a 3270 Downstream LU](../core/how-to-create-a-3270-downstream-lu2.md)   
 [How to Create a Local APPC LU](../core/how-to-create-a-local-appc-lu1.md)   
 [How to Create a Remote APPC LU](../core/how-to-create-a-remote-appc-lu2.md)   
 [Creating LUs](../core/creating-lus2.md)
