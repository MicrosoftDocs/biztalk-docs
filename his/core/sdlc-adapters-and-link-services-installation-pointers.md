---
title: "SDLC Adapters and Link Services: Installation Pointers2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d01dc25c-7aed-466a-a514-8f15320009e4
caps.latest.revision: 4
---
# SDLC Adapters and Link Services: Installation Pointers
An SDLC link service enables the [!INCLUDE[hisHostIntServNoVersion](../core/includes/hishostintservnoversion-md.md)] software to communicate with the SDLC adapter. For detailed information about using a particular SDLC adapter or a particular modem (or DCE), see the adapter, modem, or DCE documentation.  
  
 The following pointers highlight important steps for installing an SDLC adapter and link service:  
  
-   Selecting the Constant RTS option in the **IBM SDLC Link Service Properties** dialog box equates to the NCP LINE macro:  
  
    ```  
    DUPLEX=FULL  
  
    ```  
  
     This configuration is recommended for all SDLC connections except tributary connections on multidrop SDLC lines. This configuration improves performance by eliminating several seconds of line turnaround delay after each transmission.  
  
     The Constant RTS option is mandatory if the line is used for full duplex, but it can also enhance performance on a half-duplex line.  
  
-   When choosing an SDLC adapter, pay close attention to the speed and duplexing capabilities. Greater speed and/or full-duplexing capabilities allow an adapter to carry greater loads. Note that an adapter that lacks a coprocessor cannot handle  
  
     full-duplex transmission at high transmission speeds, that is, greater than 9600 baud. (Examples of adapters lacking a coprocessor are the IBM SDLC, IBM MPCA, and MicroGate adapters. For these adapters, half-duplex transmission is recommended.)  
  
-   Configuring adapters that lack a coprocessor to half duplexing, although slower, has the advantage of requiring substantially less central processing unit (CPU) time. The device driver via DMA will process transmitted information as frames. In contrast, if you use full duplexing with such adapters, the device driver must handle interrupts as characters, placing more load on the CPU. However, if the CPU can handle the load, full duplex provides substantially faster throughput, if the host VTAM configuration also specifies full duplex (DATMODE=FULL in the PU definition).  
  
-   After installation of the adapter and link service, you will need to configure the connection with the correct duplex setting. For details, see the next section, X.25 Adapters and Link Services: Installation Pointers.  
  
-   Stop all existing services that use the SDLC adapter before attempting to configure the link service properties. For example, stop the Remote Access Service if it uses the SDLC adapter. Only when these services are stopped can SNA Manager successfully autodetect the adapter.  
  
-   If you attempt to install an SDLC link service for an adapter that you know is physically installed in the computer, and a pop-up message appears saying that SNA Manager cannot detect the adapter, click **Cancel**. The message indicates that a service is currently using the SDLC adapter. Find out which service it is, stop the service, and then try to install the link service again.  
  
     SNA Manager can detect the adapter only if no other service is using that adapter. If you do not click **Cancel** when the pop-up message appears, SNA Manager continues the installation process using default values (not values attuned to that adapter, since SNA Manager cannot detect it). As described in the preceding paragraph, to correct this situation, stop the service using the SDLC adapter and then reinstall the link service.  
  
     When you install a new adapter, check the interrupt, port address, and direct memory access (DMA) settings, to avoid conflicts with other adapters in the computer. The normal method for adjusting the settings among your adapters is through EISA configuration programs, jumpers on the motherboard, or configuration utilities. Windows provides the Device Manager. You may also use configuration utilities supplied with your adapters.  
  
     One way of viewing the settings used by various adapters in your computer is to start WINMSD.EXE, the Windows Diagnostics utility, which includes an IRQ/Port Status button and a DMA/Memory button.  
  
-   Device drivers provided by Host Integration Server report any interrupt, port address, or DMA conflicts they detect to the Windows System Event Log. The events are listed under a Source of Service Control Manager or a driver name.  
  
-   To ensure that the line speed is set correctly through hardware or software settings, study the documentation for the modem or DCE. (Do not confuse setting the line speed with selecting the Data Rate, configurable through the **SDLC Connection Properties** dialog box, on the **SDLC** tab, in SNA Manager. The Data Rate setting controls the speed of transmissions between the SDLC adapter and the modem only.)  
  
-   If you want to use a server-stored number, check that both the link service and the modem are configured correctly. This applies to MicroGate adapters, or any adapter that can handle a server-stored number. On the modem, it may be necessary to override the setting that causes the modem to autodial from its own stored number. (In modem terminology, when Data Terminal Ready — DTR — is raised, the modem must wait, not dial.) To find out how to override modem autodialing, see your modem or DCE documentation.