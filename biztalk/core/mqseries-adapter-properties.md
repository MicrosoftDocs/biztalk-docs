---
title: "MQSeries Adapter Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MQXQH_RemoteQName property [MQSeries adapters]"
  - "MQMD_ReplyToQ property [MQSeries adapters]"
  - "configuring [MQSeries adapters], properties"
  - "MQXQH_MsgDesc_ReplyToQMgr property [MQSeries adapters]"
  - "UserHttpHeaders property [MQSeries adapters]"
  - "MQMD_CorrelId property [MQSeries adapters]"
  - "MQXQH_MsgDesc_MsgId property [MQSeries adapters]"
  - "MQXQH_MsgDesc_ReplyToQ property [MQSeries adapters]"
  - "SubmissionHandle property [MQSeries adapters]"
  - "BizTalk_CorrelationID property [MQSeries adapters]"
  - "MQMD_ReplyToQMgr property [MQSeries adapters]"
  - "EnableChunkedEncoding property [MQSeries adapters]"
  - "MQSeries adapters, properties"
  - "MQXQH_MsgDesc_CorrelId property [MQSeries adapters]"
  - "MQXQH_RemoteQMgrName property [MQSeries adapters]"
  - "MQMD_MsgId property [MQSeries adapters]"
ms.assetid: c3cfbc8c-4c9b-431e-b0b6-4c065a69ce6b
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MQSeries Adapter Properties
To access MQSeries header properties from a BizTalk orchestration, you must add a reference to the MQSeries.dll assembly to your project. This assembly is located where you installed the MQSeries adapter, for example, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
 After you reference the MQSeries property schema, additional context properties are available to various BizTalk Server development tools (for example, the **Message Assignment** shape in Orchestration Designer).  
  
> [!NOTE]
>  Make sure that you follow the guidelines in the IBM WebSphere MQ documentation when you work with MQSeries header properties.  
  
 The adapter automatically promotes some MQSeries properties. Your applications and custom components must avoid demoting these properties. You can promote additional properties by using custom pipeline components. The automatically promoted properties are as follows:  
  
-   **BizTalk_CorrelationID**  
  
-   **MQMD_CorrelId**  
  
-   **MQMD_MsgId**  
  
-   **MQMD_ReplyToQ**  
  
-   **MQMD_ReplyToQMgr**  
  
-   **MQXQH_RemoteQMgrName**  
  
-   **MQXQH_RemoteQName**  
  
-   **MQXQH_MsgDesc_CorrelId**  
  
-   **MQXQH_MsgDesc_MsgId**  
  
-   **MQXQH_MsgDesc_ReplyToQ**  
  
-   **MQXQH_MsgDesc_ReplyToQMgr**  
  
## In This Section  
  
-   [Data Type Conversion of Properties](../core/data-type-conversion-of-properties.md)  
  
-   [Properties Related to BizTalk Server](../core/properties-related-to-biztalk-server.md)  
  
-   [MQSeries Context Properties](../core/mqseries-context-properties.md)  
  
## See Also  
 [Configuring the MQSeries Adapter](../core/configuring-the-mqseries-adapter.md)