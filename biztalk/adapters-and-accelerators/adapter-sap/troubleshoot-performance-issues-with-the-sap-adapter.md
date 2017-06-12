---
title: "Troubleshoot Performance Issues with the SAP adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "troubleshooting, performance"
  - "performance, troubleshooting"
ms.assetid: 7e8e9fec-0edf-4c67-837c-0e271b2ffe68
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshoot Performance Issues with the SAP adapter
This section discusses using troubleshooting techniques to resolve performance issues that you might encounter when using [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].  
  
##  <a name="BKMK_SAPSlowdown"></a> Slowdown or stall in throughput when using the adapter with BizTalk Server  
 **Problem**  
  
 When using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the number of messages sent or received by the adapter slows down or comes to a stall.  
  
 **Cause**  
  
 The **EnableBizTalkCompatibilityMode** binding property is not set on the WCF-Custom send or receive port in BizTalk Server Administration Console.  
  
 **Resolution**  
  
 Set the **EnableBizTalkCompatibilityMode** binding property to True. For more information about this property, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md). For instructions on how to set a binding property, see [Configure the binding properties for the SAP adapter](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).  
  
##  <a name="BKMK_SAPMemLeak"></a> Possible memory leak when using NULL values for parameters  
 **Problem**  
  
 You may observe memory leak if you do not specify values for input or table parameters while invoking artifacts in the SAP system.  
  
 **Resolution**  
  
 Make sure you specify values for all the input and table parameters while invoking an artifact in the SAP system.  
  
## See Also  
[Troubleshoot the SAP adapter](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)