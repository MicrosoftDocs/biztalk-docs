---
title: "Batch Definition Tab | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "btahl7.configurationexplorer.tab.batchdefinition"
helpviewer_keywords: 
  - "Batch Definition tab [Configuration Explorer]"
  - "batching, configuring"
  - "configuring, batching"
ms.assetid: fe8685ef-5de5-4337-8691-8e4094056ace
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Batch Definition Tab
You use the **Batch Definition** tab to enable inbound batching, batch in/batch out batching, and select available schemas for outbound batching.  

 In the **BTAHL7 Configuration Explorer** dialog box, on the **Batch Definition** tab, do the following:  


|                   Use this                   |                                                                                                                                                            To do this                                                                                                                                                            |
|----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          **Fragmentation required**          |                                                           Select one of the following options:<br /><br /> -   **Yes**. To enable fragmentation.<br />-   **No**. To disable fragmentation. **Note:**  For a new party, **Fragmentation Required** defaults to **No**.                                                           |
| **Recoverable interchange support required** | Select one of the following options:<br /><br /> -   **True**. To enable recoverable interchange support.<br />-   **FALSE**. To disable recoverable interchange support. **Note:**  For a new party, **Fragmentation Required** defaults to **FALSE** and is enabled only if the value of **Fragmentation Required** is **No**. |
|             **Select Messages**              |                              Select the message types you want to send as a batch from the Available Messages window and then click the Move to right arrow (**>>**).<br /><br /> To batch incoming ACK messages, you must add the ACK message type. You do so by deploying the ACK message schema.                              |
|      **Select Message Acknowledgments**      |                               Select the message types for which you want [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] to send the acknowledgments as a batch from the Available Message Acks window, and then click the Move to right arrow (**>>**).                                |

