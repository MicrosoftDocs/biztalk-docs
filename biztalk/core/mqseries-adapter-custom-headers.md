---
description: "Learn more about: MQSeries Adapter Custom Headers"
title: "MQSeries Adapter Custom Headers | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MQSeries adapters, custom headers"
ms.assetid: b0e18203-a33f-4d50-8483-396699cdff23
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSeries Adapter Custom Headers
Because of the header structures used in MQSeries messages, you must manage any custom headers you want to use. Custom headers must be part of the message body to avoid interfering with the processing of the MQSeries headers. Make sure that you avoid demoting any one of the automatically promoted properties. For more information about automatically promoted properties, see [MQSeries Adapter Properties](../core/mqseries-adapter-properties.md).  
  
 In turn, the incorporation of custom headers in the message body requires additional processing. One solution is to handle the custom headers in the pipelines of the application. A receive pipeline extracts the custom header information and promotes the information as context properties. Similarly, the send pipeline takes the context properties corresponding to the custom header and demotes the properties in the body of the message.  
  
 For an example of using custom headers in a pipeline component, see [MQSSendPipelineComponent (BizTalk Server Sample)](../core/mqssendpipelinecomponent-biztalk-server-sample.md).  
  
## See Also  
 [MQSeries Adapter Properties](../core/mqseries-adapter-properties.md)
