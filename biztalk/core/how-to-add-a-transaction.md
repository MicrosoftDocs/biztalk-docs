---
title: "How to Add a Transaction | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adding, transactions"
  - "transactions, adding"
ms.assetid: 25385c20-3025-4cf1-bc1f-ef266e081bad
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add a Transaction
Follow these steps to add a transaction.  
  
### To add a transaction  
  
1. Click the **Transactions** tab.  
  
2. Click **Add Transaction**.  
  
3. Click **Add a New Value**. Enter the following information, and then click **Add**.  
  
   1. **Node Name:** Verify that this is **MSEXTERNAL**.  
  
   2. **Transaction Type:** Verify that this is **Outbound Asynchronous**.  
  
   3. **Request Message:** Enter `LOCATION_SYNC`.  
  
   4. **Request Message Version:** Enter `VERSION_1`.  
  
      ![](../core/media/psadapter-38-task-gatewayaddtransaction.gif "PSAdapter_38_Task_GatewayAddTransaction")  
  
4. On the **Transaction Detail** tab, verify the following settings:  
  
   1. **Status:** Active.  
  
   2. **Routing:** Implicit.  
  
      ![](../core/media/psadapter-39-task-gatewaytransdetail.gif "PSAdapter_39_Task_GatewayTransDetail")  
  
5. Click **Save**.  
  
6. Click the **Return to Transaction List** link.  
  
    The transaction appears in the list of transactions.  
  
## See Also  
 [Creating a PeopleSoft HTTP Host and Port](../core/creating-a-peoplesoft-http-host-and-port.md)