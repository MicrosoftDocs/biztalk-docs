---
title: "Creating and Configuring LUs1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea83b5c4-8691-4455-964d-4f91b941f3b4
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Creating and Configuring LUs
After you configure the connection, you can create the 3270 LUs. The LUs can be display LUs (terminal emulation), printer LUs, application LUs (LUAs), or downstream LUs.  
  
 Each 3270 LU is configured based on the type of connection used. If the connection is channel, 802.2, X.25, or Synchronous Data Link Control (SDLC), the LUs need an LU number, which identifies the LU on its connection. This number should match the LOCADDR= parameter of the LU definition in Virtual Telecommunications Access Method (VTAM) or in the Network Control Program (NET) Gen. Up to 254 LUs can be configured for each connection, and they can be consecutively configured as a range of LUs.  
  
 You can create LUs one at a time or in a consecutively numbered range. When you create a range of LUs, all the LUs are given the same properties. You can modify individual LUs after creating them.  
  
 For information about the new IP-DLC Link Service, see [IP-DLC Link Service](./ip-dlc-link-service2.md).  
  
 For procedures about creating LUs, see the following:  
  
- [How to Create LU Pools](../core/how-to-create-lu-pools1.md)  
  
  For procedures about configuring LUs, see the following:  
  
- [How to Configure a Range of 3270 LUs](../core/how-to-configure-a-range-of-3270-lus2.md)  
  
- [How to Assign LUs to Workstations](../core/how-to-assign-lus-to-workstations1.md)  
  
- [How to Associate 3270 Printer LUs with 3270 Display LUs](../core/how-to-associate-3270-printer-lus-with-3270-display-lus2.md)  
  
- [How to Configure Downstream Connections](../core/how-to-configure-downstream-connections1.md)  
  
- [How to Reorder Downstream Connections](../core/how-to-reorder-downstream-lus1.md)  
  
- [How to Configure APPC LUs for TPs or 5250 Emulation](../core/how-to-configure-appc-lus-for-tps-or-5250-emulation2.md)  
  
- [Precedence of Accounts in Determining Default LUs](../core/precedence-of-accounts-in-determining-default-lus2.md)  
  
### To modify a 3270 LU  
  
1.  In SNA Manager, ensure that the appropriate service is inactive by right-clicking **SNA service**, and then click **Stop**.  
  
2.  Double-click **Connections**, and then double-click the connection that contains the LU you want to view.  
  
3.  Right-click the LU whose properties you want to view, and then click **Properties**. Click the appropriate tab to view or modify the LU properties.  
  
4.  Click **Save Configuration** on the **Action** menu if you made changes, and then restart the affected service.  
  
> [!NOTE]
>  Restarting the server disconnects all users. Try to schedule configuration changes when they least affect users.  
  
## See Also  
 [Configuring Your Enterprise](../core/configuring-your-enterprise1.md)