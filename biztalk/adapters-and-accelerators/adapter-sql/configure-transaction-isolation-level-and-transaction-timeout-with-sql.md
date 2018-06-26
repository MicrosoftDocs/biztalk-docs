---
title: "Configure Transaction Isolation Level and Transaction Timeout with SQL | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 55355272-60c0-49e4-b37e-9198458ab305
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure Transaction Isolation Level and Transaction Timeout with SQL
While performing inbound operations (Polling and Notification) using the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], you should appropriately configure the transaction isolation level and the transaction timeout values. To do this:  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. In the console tree, expand the **BizTalk Group**, and then expand **Applications**.  

3. Expand the application under which you want to deploy the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

4. Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.  

5. In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.  

6. In the left pane of the **Receive Port Properties** dialog box, click **Receive Locations**, and then click **New** in the right pane to define a new receive location.  

7. In the **Receive Location Properties** dialog box, click **WCF-Custom** in the **Type** list.  

8. Click **Configure** adjacent to the **Type** list.  

9. In the **WCF-Custom Transport Properties** dialog box, click the **Behavior** tab.  

10. In the **Behavior** list, right-click **ServiceBehavior**, and click **Add extension**.  

11. In the **Select Behavior Extension** dialog box, select **sqlAdapterInboundTransactionBehavior**, and click **OK**.  

12. In the left pane of the **WCF-Custom Transport Properties**, select the **sqlAdapterInboundTransactionBehavior** service under **ServiceBehavior**. For receive (Inbound operation message), one can use the sqlAdapterInboundTransactionBehavior to control the isolation level and the default value is **ReadCommitted**.  

13. In the right pane of the **WCF-Custom Transport Properties**, specify appropriate values for the **transactionIsolationLevel** and **transactionTimeout** parameters. You can select any of the following transaction isolation levels: **Serializable**, **RepeatableRead**, **ReadCommitted**, **ReadUncommitted**, **Snapshot**, **Chaos**, and **Unspecified**.  

    > [!NOTE]
    >  The default value of Transaction Isolation Level is **Serializable** for the WCF-SQL adapter for both inbound and outbound operations. For information about these transaction isolation levels, see the **Members** section at [Isolation Level Enumeration](http://go.microsoft.com/fwlink/?LinkId=126983) (http://go.microsoft.com/fwlink/?LinkId=126983).  

     ![Setting Transaction Isolation Level](../../adapters-and-accelerators/adapter-sql/media/b39c180e-ca9f-48ca-9550-f4837826d00e.gif "b39c180e-ca9f-48ca-9550-f4837826d00e")  

14. Click **OK** in the **WCF-Custom Transport Properties** dialog box.  

15. Click **OK** in the open dialog boxes to save the changes.
