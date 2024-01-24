---
description: "Learn more about: MQSC Adapter Schema"
title: "MQSC Adapter Schema2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MQSC Adapter Schema
The BizTalk Adapter for WebSphere MQ uses the same property schema assembly (MQSeries.dll) that is available with the server-based MQSeries Adapter. Because the server-based MQSeries Adapter is available with BizTalk Server 2006, this assembly should be already deployed in the BizTalk Management Database.  
  
 In addition, an extension schema assembly is available with the MQSC Adapter. This property schema assembly is called MQSeriesEx.dll, and it contains properties that are valid only to the Client-Based MQSeries Adapter. The assembly is deployed into the BizTalk Management Database as part of the adapter installation.  
  
 For information about these context properties in both property schema assemblies (MQSeries.dll and MQSeriesEx.dll), refer to the Programming Guide section.  
  
 If these assemblies are not deployed, you can deploy them by using the btsdeploy command-line utility.  
  
 At the command prompt, type the following:  
  
 **btsdeploy DEPLOY assembly=\<** *Path to MQSeries.dll or MQSeriesEx.dll* **>**  
  
 Both assemblies can be found in the MQSC Adapter installation location.  
  
## See Also  
 [BizTalk Adapter for WebSphere MQ](../core/biztalk-adapter-for-websphere-mq2.md)
