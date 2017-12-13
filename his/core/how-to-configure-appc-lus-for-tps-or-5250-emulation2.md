---
title: "How to Configure APPC LUs for TPs or 5250 Emulation2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b99f7e8-15e3-4629-a7ab-2a6aba28f397
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure APPC LUs for TPs or 5250 Emulation
The following is an overview of the procedures to add and configure APPC LUs:  
  
1.  Assign the local APPC LU to a server.  
  
2.  Configure the local APPC LUs:  
  
    -   For an independent LU, specify the LU Alias, Network Name, and LU Name. Depending on system configuration, you may need to specify other information.  
  
    -   For a dependent LU, specify LU Alias, LU Number, and LU Name. Depending on system configuration, you may need to specify other information.  
  
3.  Create a remote APPC LU on a connection and configure the remote APPC LU:  
  
    -   For a remote LU to be used with an independent local LU, specify the LU Alias, Network Name, and LU Name. Depending on system configuration, you may need to specify other information. For communication with an AS/400 computer, make the remote LU name the same as the name of the AS/400 computer.  
  
    -   For a remote LU to be used with a dependent local LU, specify the LU Alias, Network Name, LU Name, and Uninterpreted LU Name. Depending on system configuration, you may need to specify other information.  
  
4.  Optionally, configure session security for the remote LU.  
  
5.  You must configure an appropriate mode if it has not already been done.  
  
6.  Optionally, assign a default local APPC LU and a default remote APPC LU to users and groups.  
  
7.  If you are using Common Programming Interface for Communications (CPI-C), configure one or more CPI-C symbolic destination names.  
  
8.  If you are using the display verb, you may want to change the default connection that Host Integration Server uses for the verb. To ensure that all changes take effect, restart the server.  
  
> [!NOTE]
>  APPC LUs are used for transaction programs (TPs) or for 5250 emulation. APPC LUs used with TPs are generally for communication between TPs on different systems, not communication between TPs on a single system.  
  
### To add local and remote APPC LUs  
  
1.  In the Host Integration Server console tree, double-click **SNA service**, and then click **Local APPC LUs**.  
  
2.  On the **Action** menu, point to **New**, and click **Local LU**.  
  
3.  Configure the properties for the local LU, and then click **OK**.  
  
4.  To add the remote LU, click **Remote APPC LUs**.  
  
5.  On the **Action** menu, point to **New**, and click **Remote LU**.  
  
6.  Configure the properties for the remote LU, and click **OK**.  
  
7.  On the **Action** menu, click **Save Configuration**.  
  
> [!NOTE]
>  APPC uses both local and remote LUs. These LUs need to be properly configured before Host Integration Server can communicate with the AS/400 computer.  
  
> [!NOTE]
>  The option, **Member of Outgoing Local APPC LU Pool**, differs from other types of LU pools, such as the 3270, LUA, and downstream LU pools.  
  
> [!NOTE]
>  Configuring session security for remote LUs is optional.  
  
#### To configure incoming APPC sessions  
  
1.  Verify that you have configured a remote LU to represent the incoming host or that you have configured one remote LU for each host.  
  
2.  In the Host Integration Server console tree, double-click **Local APPC LUs**, and then click the local LU that you want to configure.  
  
3.  On the **Action** menu, click **Properties**.  
  
4.  Click the **Advanced** tab, specify the **Implicit Incoming Remote LU**, which is the name of the incoming host, and then click **OK**.  
  
5.  Repeat steps 2–4 for each local APPC LU that you want to configure.  
  
6.  On the **Action** menu, click **Save Configuration**.  
  
> [!NOTE]
>  All incoming requests must specify a local LU name that is recognized by Host Integration Server, even when using an Implicit Incoming Remote LU and Implicit Incoming Mode.  
  
#### To assign default APPC LUs to users or groups  
  
1.  In the Host Integration Server console tree, double-click **Configured Users**, and click the user or group that you want to configure.  
  
2.  On the **Action** menu, click **Properties**.  
  
3.  Click the **APPC Defaults** tab.  
  
4.  In the **Local APPC LU** box, select a default local APPC LU.  
  
5.  In the **Remote APPC LU** box, select a default remote APPC LU, and then click **OK**.  
  
6.  On the **Action** menu, click **Save Configuration**.  
  
## See Also  
 [Creating and Configuring LUs](../core/creating-and-configuring-lus1.md)