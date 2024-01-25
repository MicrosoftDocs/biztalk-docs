---
description: "Learn more about: Troubleshoot Performance Issues with the Siebel adapter"
title: "Troubleshoot Performance Issues with the Siebel adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Troubleshoot Performance Issues with the Siebel adapter
This section discusses using troubleshooting techniques to resolve performance issues that you might encounter when using [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  
  
## Known Issues  
  
###  Slowdown or stall in throughput when using the adapter with BizTalk Server  
 **Problem**  
  
 When using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the number of messages sent or received by the adapter slows down or comes to a stall.  
  
 **Cause**  
  
 The **EnableBizTalkCompatibilityMode** binding property is not set on the WCF-Custom send or receive port in BizTalk Server Administration console.  
  
 **Resolution**  
  
 Set the **EnableBizTalkCompatibilityMode** binding property to True. For more information about this property, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md). For instructions on how to set a binding property, see [Configure the binding properties for Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md).  
  
## See Also  
[Troubleshoot the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)
