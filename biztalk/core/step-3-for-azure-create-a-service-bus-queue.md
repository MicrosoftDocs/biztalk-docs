---
title: "Step 3 (For Azure): Create a Service Bus Queue | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7192c3c-4ebf-49c4-b8ce-46a6e9fb5f4a
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 3 (For Azure): Create a Service Bus Queue
In this topic, you create a Service Bus Queue to which the X12 sales order is sent after it is processed and transformed using the EDI agreement.  
  
### To create a Service Bus Queue  
  
1.  Log in to the [Windows Azure CTP Management Portal](http://go.microsoft.com/fwlink/p/?LinkId=202886) using your Microsoft account.  
  
2.  On the lower left-hand side of the page, click **AppFabric**.  
  
3.  Expand Services in the tree on the left-hand side, expand your subscription, and click a namespace that you must have already created. If you don’t have a namespace already, see [How to: Create or Modify a Windows Azure CTP Service Namespace](http://msdn.microsoft.com/library/windowsazure/hh697699.aspx).  
  
4.  To create a Queue click **New Queue** from the **Manage Entities** category from the toolbar at the top of the page.  
  
5.  In the **New Queue** dialog box, enter a name for the Queue. For this tutorial, enter the name as `queueordersedi`, and then click **OK**. You specified this name as part of the EDI agreement you created in [Step 2 (For Azure): Create an EDI Agreement](../core/step-2-for-azure-create-an-edi-agreement.md).  
  
## See Also  
 [Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)