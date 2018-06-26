---
title: "Configuring AS2 Pipeline Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.edir2.AS2.pipeline.properties"
ms.assetid: 7faf6b05-710a-4d00-8c77-590ce9d9f962
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring AS2 Pipeline Properties
Pipeline properties are used in processing an incoming or outgoing AS2 message when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has not been able to determine the agreement that resolves to the sent or received interchange.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.  
  
## AS2 Pipeline Properties  
 The following property can be set in AS2 pipelines:  
  
|Property|Use|Values|Pipeline/Stage|  
|--------------|---------|------------|---------------------|  
|ContentTransferEncoding|Indicates which method will be used for representing binary data in ASCII text format.|8bit (default)<br /><br /> 7bit<br /><br /> 8bit|AS2EdiSend/Encode<br /><br /> AS2Send/Encode|  
  
### To set a pipeline property  
  
1. In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the receive location or send port using the pipeline that you want to set properties for. Click **Properties**.  
  
2. Click the ellipsis button (…) next to the pipeline that you want to set properties for.  
  
3. Enter the value for the property, and then click **OK**.  
  
## See Also  
 [Developing and Configuring BizTalk Server AS2 Solutions](../core/developing-and-configuring-biztalk-server-as2-solutions.md)