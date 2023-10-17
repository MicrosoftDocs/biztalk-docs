---
title: "Create and use Schemas in TIBCO | Microsoft Docs"
description: Use BizTalk Editor to create a schema for the BizTalk Adapter for TIBCO Enterprise Message Service, and set the target namespace in your schema for BizTalk Server
ms.custom: ""
ms.date: "10/23/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3927b0b3-db3b-4494-b003-d930af734e58
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create and use TIBCO schemas

## Overview
Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) uses schemas that you create using an XML editor or the BizTalk Server Editor in Visual Studio (only when you use the adapter in an orchestration). The schema describes the type of information that you expect. This topic contains information for both a send and a receive handler.  
  
The schemas you create for use with BizTalk Adapter for TIBCO Enterprise Message Service must have a target namespace. BizTalk Server requires the target namespace because it is the key that associates a given message instance with a given orchestration. In other words, an orchestration subscribes to any message that has a specific target namespace, and an incoming XML message that has that target namespace is given to every orchestration that subscribed to the message. If an XML document schema does not have a target namespace, BizTalk Server uses the name of the root element as a key.  

The following steps show how to generate a schema, and how to set the target namespace.  
  
## Generate a Schema    
 
1.  In the BizTalk Editor, open your project.  
  
2.  Under Solution Explorer in the upper-right, select **Add**, and then select **Add Generated Items**.  
  
3.  In the **Templates** pane, select **Generate Schemas**, and then click **Add**.  
  
4.  In the **Generate Schemas** dialog box, in the **Document type** list, select **Well-Formed XML**.  
  
5.  Click **Browse** to locate the input file for which you want to generate a schema, and then click **OK**.  
  
Next, set the target namespace.  
  
## Set the target namespace  
  
1. In BizTalk Editor, open your schema file, right-click **\<schema\>**, and then select **Properties**.  
  
2. In the **Properties** pane, locate the **Namespace** field and type a name, for example, `testNameSpace`.  
  
   You can then continue with your orchestration using messages. When a message is picked up, BizTalk Server finds an orchestration that uses a schema with a set target namespace, and the orchestration process is followed.  
  
## See Also  
 [Developing Applications](../core/developing-applications5.md)