---
title: "Considerations While Using BizTalk Server on a 64-bit Windows Operating System | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac630f55-7ebe-4b93-bf98-70b00788520f
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Considerations While Using BizTalk Server on a 64-bit Windows Operating System
When using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a 64-bit Windows operating system, make sure you consider the issues described in this topic. For frequently asked questions related to 64-bit support for Microsoft BizTalk Server, see [BizTalk Server 64-bit Support](http://go.microsoft.com/fwlink/?LinkID=155306) (<http://go.microsoft.com/fwlink/?LinkID=155306>).  
  
## Modify the Process Memory Usage Throttling Threshold  
 By default, the **Process memory usage** host throttling threshold is set to 25. If this value is exceeded and the BizTalk process memory usage is more than 300 MB, a throttling condition may occur. On a 64-bit server, you can increase this value to 100. This allows for more memory consumption by the BizTalk process before throttling occurs. For instructions on how to modify the process memory usage host throttling threshold, see [How to Modify the Default Host Throttling Settings](http://go.microsoft.com/fwlink/?LinkId=157210) (http://go.microsoft.com/fwlink/?LinkId=157210).  
  
> [!NOTE]  
>  The maximum available process memory is capped at an address space size of 2 GB for purposes of this calculation, even if the system has more than 2 GB of physical memory. A 2 GB process memory upper limit is used for purposes of this calculation on both 32 bit and 64 bit systems. In order to prevent out of memory errors, it is recommended that you do not specify a value that will allow host instance memory to exceed 1.54 GB when running a 32 bit version of BizTalk Server, regardless of if BizTalk Server is installed on a 32 bit or 64 bit operating system. For example, if you specify a value from 1 through 100 for this setting to initiate throttling based upon the percentage of process memory used, do not enter a value greater than 75 (.75 * 2GB = 1.54 GB). If you specify a value greater than 100 for this setting to initiate throttling based upon the specified number in MB, do not enter a value greater than 1536.If you are running a 64 bit version of BizTalk Server, specify a value or either 100 (100%) or 2048 (2GB) to initiate throttling when the maximum available process memory of 2 GB is used.  
  
## Adapters That Do Not Support 64-bit Hosts  
 The following adapters are not supported to run on 64-bit host instances:  
  
- FTP adapter  
  
- POP3 adapter  
  
  Make sure you run these adapters in a 32-bit host instance.  
  
## Configure the MIME/SMIME Encoder to run in 32-bit mode  
 In BizTalk Server, the MIME/SMIME encoder pipeline component dies not have native 64-bit support. This means that this component must be run in a 32-bit emulation mode process (WOW64). This implies that the host instance in which this encoder component (or the send pipeline of which it is a part) runs must be running in 32-bit emulation mode. Be aware of the performance (and other) implications of this restriction for other elements of BizTalk running in this same host instance.