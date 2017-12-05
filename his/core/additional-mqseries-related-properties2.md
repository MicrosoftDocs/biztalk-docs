---
title: "Additional MQSeries Related Properties2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76088d0a-863d-48a6-a311-f5e6d71ca55d
caps.latest.revision: 3
---
# Additional MQSeries Related Properties
There are additional MQSeries-related properties included in the property schema and available for use within your BizTalk Server application. These are applicable when dealing with CICS or IMS applications. The following table lists these properties.  
  
|Name|Type|Length|Value|  
|----------|----------|------------|-----------|  
|MQCIH_AbendCode|String|4||  
|MQCIH_ADSDescriptor|unsigned int|4||  
|MQCIH_AttentionId|string|4||  
|MQCIH_Authenticator|string|8|Set to the SSO password when you use the SSOAffiliateApplication property.|  
|MQCIH_CancelCode|string|4||  
|MQCIH_CompCode|unsigned int|4||  
|MQCIH_ConversationalTask|unsigned int|4||  
|MQCIH_CursorPosition|unsigned int|4||  
|MQCIH_ErrorOffset|unsigned int|4||  
|MQCIH_Facility|string|16|Hexadecimal string|  
|MQCIH_FacilityKeepTime|unsigned int|4||  
|MQCIH_FacilityLike|String|4||  
|MQCIH_Flags|unsigned int|4||  
|MQCIH_Format|String|||  
|MQCIH_Function|String|4||  
|MQCIH_GetWaitInterval|unsigned int|4||  
|MQCIH_LinkType|unsigned int|4||  
|MQCIH_NextTransactionId|String|4||  
|MQCIH_OutputDataLength|unsigned int|4||  
|MQCIH_Reason|unsigned int|4||  
|MQCIH_ReplyToFormat|String|||  
|MQCIH_ReturnCode|unsigned int|4||  
|MQCIH_StartCode|String|4||  
|MQCIH_TaskEndStatus|unsigned int|4||  
|MQCIH_TransactionId|String|4||  
|MQCIH_UOWControl|unsigned int|4||  
|MQIIH_Authenticator|String|8|Set to the SSO password when you use the SSOAffiliateApplication property.|  
|MQIIH_CommitMode|String|||  
|MQIIH_Flags|unsigned int|4||  
|MQIIH_Format|String|||  
|MQIIH_LTermOverride|String|8||  
|MQIIH_MFSMapName|String|8||  
|MQIIH_ReplyToFormat|String|||  
|MQIIH_SecurityScope|String|||  
|MQIIH_TranInstanceId|String|32|Hexadecimal string|  
|MQIIH_TranState|String|||