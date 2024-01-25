---
description: "Learn more about: Step 5: Configuring the BizTalk Messaging Servers"
title: "Step 5: Configuring the BizTalk Messaging Servers"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 5: Configuring the BizTalk Messaging Servers
This section provides guidelines on configuring the BizTalk Messaging servers.

### To configure the BizTalk Messaging servers

1. Enable Network Distributed Transaction Coordinator (DTC) access by selecting it from the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under the Application Server category. Network DTC client access was enabled on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer in an earlier step. See the following Knowledge Base articles on the Microsoft Help and Support Web site for information about troubleshooting DTC issues:

   - How To Troubleshoot MS DTC Firewall Issues, located at [https://go.microsoft.com/fwlink/?linkid=48870](https://go.microsoft.com/fwlink/?linkid=48870).

   - How To Use DTCTester Tool, located at [https://go.microsoft.com/fwlink/?linkid=48871](https://go.microsoft.com/fwlink/?linkid=48871).

   - If DTC is behind a firewall, see "Configuring Microsoft Distributed Transaction Coordinator (DTC) to Work Through a Firewall", located at [https://go.microsoft.com/fwlink/?linkid=48872](/troubleshoot/windows-server/application-management/configure-dtc-to-work-through-firewalls).

2. Configure and verify Network Load Balancing on the BizTalk receive servers as described in [Step 2: Configuring NLB on the Servers](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md).

3. Install and configure [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as described in [Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).

   This section contains:

-   [Installing and Configuring BizTalk Server on the Messaging Server](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-messaging-server.md)

-   [Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)