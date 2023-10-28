---
title: Creating and Configuring LUs
description: Learn about creating and configuring logical units (LUs).
ms.prod: host-integration-server
ms.topic: how-to
ms.date: 11/30/2017
---

# Creating and Configuring LUs

After you configure the connection, you can create the 3270 logical units (LUs). These LUs can be display LUs (terminal emulation), printer LUs, application LUs (LUAs), or downstream LUs. You can create LUs one at a time or in a consecutively numbered range. When you create a range of LUs, all the LUs are given the same properties. You can modify individual LUs after creating them.

- For information about the new IP-DLC Link Service, see [IP-DLC Link Service](./ip-dlc-link-service2.md).  

- For procedures about creating LUs, see [Create LU Pools](how-to-create-lu-pools1.md).

- For procedures about configuring LUs, see the following documentation:

  - [Configure a Range of 3270 LUs](../core/how-to-configure-a-range-of-3270-lus2.md)
  - [Assign LUs to Workstations](../core/how-to-assign-lus-to-workstations1.md)
  - [Associate 3270 Printer LUs with 3270 Display LUs](../core/how-to-associate-3270-printer-lus-with-3270-display-lus2.md)
  - [Configure APPC LUs for TPs or 5250 Emulation](../core/how-to-configure-appc-lus-for-tps-or-5250-emulation2.md)
  - [Precedence of Accounts in Determining Default LUs](../core/precedence-of-accounts-in-determining-default-lus2.md)

### Modify a 3270 LU

1.  In SNA Manager, make sure that the appropriate service is inactive by opening the **SNA service** shortcut menu, and then select **Stop**.  
  
1.  Expand **Connections**, and then expand the connection that contains the LU you want to view.

1.  Open the shortcut menu for the LU with the properties that you want to view, and select **Properties**.

1.  Select the tab to view or modify the LU properties.

1.  If you made changes, on the **Action** menu, select **Save Configuration**, and restart the affected service.

    > [!NOTE]
    >
    > Restarting the server disconnects all users. Try to schedule configuration changes when they least affect users.  
  
## See also

[Configuring Your Enterprise](../core/configuring-your-enterprise1.md)
