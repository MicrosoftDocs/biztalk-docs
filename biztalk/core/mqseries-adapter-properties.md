---
description: "Learn more about: MQSeries Adapter Properties"
title: "MQSeries Adapter Properties"
ms.custom: "devx-track-javaee-websphere"
ms.date: "12/30/2022"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
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
