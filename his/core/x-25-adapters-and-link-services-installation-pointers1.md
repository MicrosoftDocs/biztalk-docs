---
description: "Learn more about: X.25 Adapters and Link Services: Installation Pointers"
title: "X.25 Adapters and Link Services: Installation Pointers1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3c27094-b567-4737-85ba-fe4dd41baaa5
caps.latest.revision: 4
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# X.25 Adapters and Link Services: Installation Pointers
An X.25 link service enables the [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] software to communicate with the X.25 adapter. The following pointers highlight important steps for installing an X.25 adapter and link service:  
  
-   When choosing an X.25 adapter, pay close attention to the speed capabilities. Greater speed allows an adapter to carry greater loads. Note that an adapter that lacks a coprocessor cannot handle high-speed transmission with full duplexing; the duplexing type used by Host Integration Server X.25 connections. (Examples of adapters lacking a coprocessor are the IBM SDLC and IBM MPCA adapters. For these adapters, the transmission speed must be 9600 baud or less.)  
  
-   Contact your X.25 carrier or network administrator for information needed for your X.25 link service. The following table lists some important parameters you will need to know:  
  
    |Parameters from X.25 carrier|Corresponding parameter in Connection Properties|Typical value(s)|  
    |----------------------------------|------------------------------------------------------|------------------------|  
    |Local X.25 address|Local NUA Address|Varies|  
    |Level 3 window size|Default L3 Window Size|2|  
    |Level 3 packet size|Default L3 Packet Size|512|  
    |Level 2 window size|L2 Window Size|7|  
    |Channel ranges (Outgoing SVC, Two-Way SVC, Incoming SVC, and/or PVC)|Channel Ranges (Outgoing SVC, Two-Way SVC, Incoming SVC, and/or PVC)|Vary|  
  
     Note that the encoding setting (NRZ or NRZI) is almost always NRZ on X.25 networks. This setting must match the equivalent setting on the host. For connections to mainframes, the NRZI setting is found in the LINE/GROUP definition in VTAM or NCP. If VTAM does not specify the NRZI setting, it defaults to NRZI=YES. For connections to AS/400 computers, the NRZI setting is in the Line Description.  
  
-   When you install a new adapter, check the interrupt, port address, and direct memory access (DMA) settings, to avoid conflicts with other adapters in the computer. The normal method for adjusting the settings among your adapters is through EISA configuration programs, jumpers on the motherboard, or configuration utilities. Windows provides the Device Manager. You may also use configuration utilities supplied with your adapters.  
  
     One way of viewing the settings used by various adapters in your computer is to start WINMSD.EXE, the Windows Diagnostics utility, which includes an IRQ/Port Status button and a DMA/Memory button.  
  
-   Device drivers provided by Host Integration Server report any interrupt, port address, or DMA conflicts that they detect to the Windows System Event Log. The events are listed under a Source of Service Control Manager or a driver name.  
  
-   Ignore the option labeled "Switched: Server-Stored Number" in the **X.25 Link Service Properties** dialog box. This option does not match capabilities currently available with X.25 link services. If chosen, the option behaves the same way as "Switched: Modem-Stored Number."  
  
-   With X.25 link services, you can also adjust the T1 timeout and N2 retry limit. However, the defaults for these are appropriate for most networks. Therefore, it is recommended that you do not adjust them unless you have a specific reason for doing so, and that you understand the characteristics of your network as well as the way that the timeout works.
