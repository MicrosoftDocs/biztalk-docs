---
title: "Configuring and Controlling TPs (CPI-C)2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97cbd297-b0d7-4c57-8030-c92a42e56dca
caps.latest.revision: 3
---
# Configuring and Controlling TPs (CPI-C)
The following table shows how the characteristics of the transaction programs (TPs) and selection of the logical units (LUs) for a conversation are controlled.  
  
|Characteristic|How controlled|  
|--------------------|--------------------|  
|Type of conversation:  basic or mapped.|Written into the code. For two TPs to communicate successfully, both must use the same type of conversation, basic or mapped. The default for conversation type is mapped. The type can be changed with the [Set_Conversation_Type](../Topic/Set_Conversation_Type%20\(CPI-C\)2.md) call. For more information, see [Basic and Mapped Conversations Compared](../core/basic-and-mapped-conversations-compared-cpi-c.md).|  
|Type of TP:  invoking or invokable.|Written into the code. Invoking TPs start with [Initialize_Conversation](../Topic/Initialize_Conversation%20\(CPI-C\)2.md) and [Allocate](../Topic/Allocate%20\(CPI-C\)1.md). Invokable TPs start with [Accept_Conversation](../Topic/Accept_Conversation%20\(CPI-C\)1.md). For more information, see [Invoking TPs](../core/invoking-tps-cpi-c.md) and [Invokable TPs](../core/invokable-tps-cpi-c.md).|  
|The local LU alias to be used by an invoking TP.|Three options:<br /><br /> -   Configured with a registry or environment variable.<br />-   Configured (using SNA Manager) as the default local APPC LU for the user who starts the invoking TP.<br />-   Configured (using SNA Manager) as a member of the default outgoing local APPC LU pool.<br /><br /> For more information, see [Invoking TPs and SNA Service Configuration](../core/invoking-tps-and-sna-service-configuration-cpi-c.md).|  
|The symbolic destination name used by an invoking TP.|Written into the code, in [Initialize_Conversation](../Topic/Initialize_Conversation%20\(CPI-C\)2.md).|  
|The invokable (partner) TP requested by an invoking TP.|Specified within the symbolic destination name, which can be configured using SNA Manager.|  
|The LU alias to be used by an invokable TP (the partner LU alias from the point of view of the invoking TP).|Specified within the symbolic destination name, which can be configured through SNA Management using SNA Manager. For more information, see [Invoking TPs and SNA Service Configuration](../core/invoking-tps-and-sna-service-configuration-cpi-c.md) and [Matching Invoking and Invokable TPs](../core/matching-invoking-and-invokable-tps-cpi-c.md).|  
|Type of autostarted invokable TP: queued or nonqueued.|Configured with registry or environment variables. For more information, see [Configuring Invokable TPs](../core/configuring-invokable-tps-cpi-c.md).|  
|Local LU and remote LU aliases.|Configured using SNA Manager.|  
|The pairing of local and remote LUs, and the mode used for each LU-LU pair.|Configured using SNA Manager.|