---
description: "Learn more about: Message Descriptor Properties"
title: "Message Descriptor Properties2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bc785b73-64a5-470d-971c-c60bf82492a3
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Message Descriptor Properties
The following table shows the complete set of available Message Descriptor (MQMD structure) properties and their corresponding types and values. These are part of the MQSeries.dll assembly that is deployed with the server-based MQSeries Adapter. The same assembly is used by the MQSC Adapter.  
  
|Name|Type|Length|Value|  
|----------|----------|------------|-----------|  
|MQMD_AccountingToken|String|64|Hexadecimal string|  
|MQMD_ApplIdentityData|String|32|Hexadecimal string|  
|MQMD_ApplOriginData|String|4|String<br />Default: space|  
|MQMD_BackoutCount|unsigned int|4|Number<br />Read only<br />Default: 0|  
|MQMD_CodedCharSetId|unsigned int|4|Number<br />Default: 0|  
|MQMD_CorrelId|String|48|Hexadecimal string|  
|MQMD_Encoding|unsigned int|4|Number<br />Use header file value. Default: 0|  
|MQMD_Expiry|unsigned int|4|Number|  
|MQMD_Feedback|unsigned int|4|Number<br />Use header file value. Default: 0|  
|MQMD_Format|String|8|String<br />If set to MQXMIT, makes sure that the MQXQH properties have values.|  
|MQMD_GroupID|String|48|Hexadecimal string|  
|MQMD_MsgFlags|unsigned int|4|Number<br />Use header file value. Default: 0|  
|MQMD_MsgId|String|48|Hexadecimal string|  
|MQMD_MsgSeqNumber|unsigned int|4||  
|MQMD_MsgType|unsigned int|4|Number<br />Use header file value.|  
|MQMD_Offset|unsigned int|4||  
|MQMD_OriginalLength|unsigned int|4||  
|MQMD_Persistence|unsigned int|4|Number<br />Use header file value.|  
|MQMD_Priority|unsigned int|4|Number|  
|MQMD_PutApplName|string|28|String<br />Default: space|  
|MQMD_PutApplType|unsigned int|4|Number<br />Use header file value. Default: 0|  
|MQMD_PutDate|string|8|Date|  
|MQMD_PutTime|string|8|Time|  
|MQMD_ReplyToQ|string|48|String<br />Default: space|  
|MQMD_ReplyToQMgr|string|48|String<br />Default: space|  
|MQMD_Report|unsigned int|4|Number<br />Use header file value.|  
|MQMD_UserIdentifier|string|12|String<br /><br /> Contains the user identifier when you use the SSOAffiliateApplication property.|  
  
 When receiving messages directly from MQSeries transmission queues, BizTalk Adapter for MQSeries formats the transmission queue header properties (the MQXQH data structure) and places them in their corresponding context properties. When sending messages directly to MQSeries transmission queues, the header properties are formatted and assigned values from the corresponding context properties only if the MQMD_Format property has a value of MQXMIT. The following table describes the properties.  
  
|Name|Type|Length|Value|  
|----------|----------|------------|-----------|  
|MQXQH_RemoteQMgrName|String|48|string|  
|MQXQH_RemoteQName|String|48|string|  
  
 Together with the properties listed earlier in this topic, the adapter populates the following Message Descriptor values following the same rules. The adapter prefixes these property names with MQXQH_ instead of MQMD_, but otherwise they map directly to those properties defined in the Message Descriptor table:  
  
-   MQXQH_MsgDesc_AccountingToken  
  
-   MQXQH_MsgDesc_ApplIdentityData  
  
-   MQXQH_MsgDesc_ApplOriginData  
  
-   MQXQH_MsgDesc_BackoutCount  
  
-   MQXQH_MsgDesc_CodedCharSetId  
  
-   MQXQH_MsgDesc_CorrelId  
  
-   MQXQH_MsgDesc_Encoding  
  
-   MQXQH_MsgDesc_Expiry  
  
-   MQXQH_MsgDesc_Feedback  
  
-   MQXQH_MsgDesc_Format  
  
-   MQXQH_MsgDesc_MsgId  
  
-   MQXQH_MsgDesc_MsgType  
  
-   MQXQH_MsgDesc_Persistence  
  
-   MQXQH_MsgDesc_Priority  
  
-   MQXQH_MsgDesc_PutApplName  
  
-   MQXQH_MsgDesc_PutApplType  
  
-   MQXQH_MsgDesc_PutDate  
  
-   MQXQH_MsgDesc_PutTime  
  
-   MQXQH_MsgDesc_ReplyToQ  
  
-   MQXQH_MsgDesc_ReplyToQMgr  
  
-   MQXQH_MsgDesc_Report  
  
-   MQXQH_MsgDesc_UserIdentifier
