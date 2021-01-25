---
description: "Learn more about: Creating LUs"
title: "Creating LUs2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98a8d190-4bfe-4d19-8c59-aa395b307221
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Creating LUs
After configuring the connection, you can create the 3270 LUs. The LUs can be display (terminal emulation) LUs, printer LUs, application LUs (LUAs), or downstream LUs.  
  
 Each 3270 LU is configured based on the type of connection used. If the connection is channel, 802.2, X.25, or SDLC, the LUs need an LU number, which identifies the LU on its connection. This number should match the LOCADDR= parameter of the LU definition in Virtual Telecommunications Access Method (VTAM) or in the Network Control Program (NCP) GEN. Up to 254 LUs can be configured for each connection, and they can be consecutively configured as a range of LUs.  
  
 You can create LUs one at a time or in a consecutively numbered range. When creating a range of LUs, all the LUs are given the same properties. You can modify individual LUs after creating them.  
  
## In This Section  
 [How to Create a 3270 Display LU](../core/how-to-create-a-3270-display-lu1.md)  
  
 [How to Create a 3270 Printer LU](../core/how-to-create-a-3270-printer-lu1.md)  
  
 [How to Create a 3270 Application LU (LUA)](../core/how-to-create-a-3270-application-lu-lua-2.md)  
  
 [How to Create a 3270 Downstream LU](../core/how-to-create-a-3270-downstream-lu2.md)  
  
 [How to Create a Local APPC LU](../core/how-to-create-a-local-appc-lu1.md)  
  
 [How to Create a Remote APPC LU](../core/how-to-create-a-remote-appc-lu2.md)  
  
## See Also  
 [Step 3 (LU) Creating and Configuring 3270 LUs](../core/step-3-lu-creating-and-configuring-3270-lus1.md)
