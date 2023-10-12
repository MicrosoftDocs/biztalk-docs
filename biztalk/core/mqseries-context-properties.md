---
description: "Learn more about: MQSeries Context Properties"
title: "MQSeries Context Properties"
ms.custom: "devx-track-javaee-websphere"
ms.date: "12/30/2022"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# MQSeries Context Properties
The MQSeries adapter provides a set of context properties, specific to MQSeries, for use in your applications. You can use these properties in filter expressions and in your orchestrations.  
  
 To assign MQSeries context properties to a message destined to a send port that is bound to the MQSeries adapter, use the message assignment operator and specify one of the available context properties in the MQSeries namespace.  
  
 The following is an example of setting the MQSeries **MQMD_UserIdentifier** property:  
  
```  
Message_2(MQSeries.MQMD_UserIdentifier) = "MeMyselfAndI";  
```  
  
 You must obtain enumerated values from the C programming language header files included with the IBM MQSeries SDK. You can find these files in the Program Files\IBM\WebSphere MQ\Tools\c\include folder. These files define the values to use when setting or reading MQSeries context property values.  
  
 Hexadecimal string values are character strings representing binary values. They do not have a prefix such as 0x. They contain digits from 0 through 9 and letters from "a" through "f" or "A" through "F". The adapter ignores white space in them.  
  
 For more information about these properties, see the IBM WebSphere MQ documentation.  
  
 The following table shows the complete set of available Message Descriptor (MQMD structure) properties and their corresponding types and values.  
  
|Name|Type|Length|Value|  
|----------|----------|------------|-----------|  
|**MQMD_AccountingToken**|string|64|Hexadecimal string|  
|**MQMD_ApplIdentityData**|string|32|Hexadecimal string|  
|**MQMD_ApplOriginData**|string|4|String<br /><br /> **Default:** space|  
|**MQMD_BackoutCount**|unsigned int|4|Number<br /><br /> Read only<br /><br /> **Default:** 0|  
|**MQMD_CodedCharSetId**|unsigned int|4|Number<br /><br /> **Default:** 0|  
|**MQMD_CorrelId**|string|48|Hexadecimal string|  
|**MQMD_Encoding**|unsigned int|4|Number<br /><br /> Use header file value. **Default:** 0|  
|**MQMD_Expiry**|unsigned int|4|Number|  
|**MQMD_Feedback**|unsigned int|4|Number<br /><br /> Use header file value. **Default:** 0|  
|**MQMD_Format**|string|8|String<br /><br /> If set to MQXMIT, makes sure that the MQXQH properties have values.|  
|**MQMD_GroupID**|string|48|Hexadecimal string|  
|**MQMD_MsgFlags**|unsigned int|4|Number<br /><br /> Use header file value. **Default:** 0|  
|**MQMD_MsgId**|string|48|Hexadecimal string|  
|**MQMD_MsgSeqNumber**|unsigned int|4||  
|**MQMD_MsgType**|unsigned int|4|Number<br /><br /> Use header file value.|  
|**MQMD_Offset**|unsigned int|4||  
|**MQMD_OriginalLength**|unsigned int|4||  
|**MQMD_Persistence**|unsigned int|4|Number<br /><br /> Use header file value.|  
|**MQMD_Priority**|unsigned int|4|Number|  
|**MQMD_PutApplName**|string|28|String<br /><br /> **Default:** space|  
|**MQMD_PutApplType**|unsigned int|4|Number<br /><br /> Use header file value. **Default:** 0|  
|**MQMD_PutDate**|string|8|Date|  
|**MQMD_PutTime**|string|8|Time|  
|**MQMD_ReplyToQ**|string|48|String<br /><br /> **Default:** space|  
|**MQMD_ReplyToQMgr**|string|48|String<br /><br /> **Default:** space|  
|**MQMD_Report**|unsigned int|4|Number<br /><br /> Use header file value.|  
|**MQMD_UserIdentifier**|string|12|String<br /><br /> Contains the user identifier when you use the **SSOAffiliateApplication** property.|  
  
 When receiving messages directly from MQSeries transmission queues, the MQSeries adapter formats the transmission queue header properties (the MQXQH data structure) and places them in their corresponding context properties. When sending messages directly to MQSeries transmission queues, the header properties are formatted and assigned values from the corresponding context properties only if the **MQMD_Format** property has a value of MQXMIT. The following table describes the properties.  
  
|Name|Type|Length|Value|  
|----------|----------|------------|-----------|  
|**MQXQH_RemoteQMgrName**|string|48|string|  
|**MQXQH_RemoteQName**|string|48|string|  
  
 Together with the properties listed earlier in this topic, the adapter populates the following Message Descriptor values following the same rules. The adapter prefixes these property names with MQXQH_ instead of MQMD_, but otherwise they map directly to those properties defined in the Message Descriptor table:  
  
- **MQXQH_MsgDesc_AccountingToken**  
  
- **MQXQH_MsgDesc_ApplIdentityData**  
  
- **MQXQH_MsgDesc_ApplOriginData**  
  
- **MQXQH_MsgDesc_BackoutCount**  
  
- **MQXQH_MsgDesc_CodedCharSetId**  
  
- **MQXQH_MsgDesc_CorrelId**  
  
- **MQXQH_MsgDesc_Encoding**  
  
- **MQXQH_MsgDesc_Expiry**  
  
- **MQXQH_MsgDesc_Feedback**  
  
- **MQXQH_MsgDesc_Format**  
  
- **MQXQH_MsgDesc_MsgId**  
  
- **MQXQH_MsgDesc_MsgType**  
  
- **MQXQH_MsgDesc_Persistence**  
  
- **MQXQH_MsgDesc_Priority**  
  
- **MQXQH_MsgDesc_PutApplName**  
  
- **MQXQH_MsgDesc_PutApplType**  
  
- **MQXQH_MsgDesc_PutDate**  
  
- **MQXQH_MsgDesc_PutTime**  
  
- **MQXQH_MsgDesc_ReplyToQ**  
  
- **MQXQH_MsgDesc_ReplyToQMgr**  
  
- **MQXQH_MsgDesc_Report**  
  
- **MQXQH_MsgDesc_UserIdentifier**  
  
  There are additional MQSeries-related properties included in the property schema and available for use in filtering expressions. The following table lists these properties.  
  
|Name|Type|Length|Value|  
|----------|----------|------------|-----------|  
|**MQCIH_AbendCode**|string|4||  
|**MQCIH_ADSDescriptor**|unsigned int|4||  
|**MQCIH_AttentionId**|string|4||  
|**MQCIH_Authenticator**|string|8|Set to the SSO password when you use the **SSOAffiliateApplication** property. **Note:**  This value will be set to blank by the MQSeries adapter if length of the SSO password exceeds 8 characters.|  
|**MQCIH_CancelCode**|string|4||  
|**MQCIH_CompCode**|unsigned int|4||  
|**MQCIH_ConversationalTask**|unsigned int|4||  
|**MQCIH_CursorPosition**|unsigned int|4||  
|**MQCIH_ErrorOffset**|unsigned int|4||  
|**MQCIH_Facility**|string|16|Hexadecimal string|  
|**MQCIH_FacilityKeepTime**|unsigned int|4||  
|**MQCIH_FacilityLike**|string|4||  
|**MQCIH_Flags**|unsigned int|4||  
|**MQCIH_Format**|string|||  
|**MQCIH_Function**|string|4||  
|**MQCIH_GetWaitInterval**|unsigned int|4||  
|**MQCIH_LinkType**|unsigned int|4||  
|**MQCIH_NextTransactionId**|string|4||  
|**MQCIH_OutputDataLength**|unsigned int|4||  
|**MQCIH_Reason**|unsigned int|4||  
|**MQCIH_ReplyToFormat**|string|||  
|**MQCIH_ReturnCode**|unsigned int|4||  
|**MQCIH_StartCode**|string|4||  
|**MQCIH_TaskEndStatus**|unsigned int|4||  
|**MQCIH_TransactionId**|string|4||  
|**MQCIH_UOWControl**|unsigned int|4||  
|**MQIIH_Authenticator**|string|8|Set to the SSO password when you use the **SSOAffiliateApplication** property. **Note:**  This value will be set to blank by the MQSeries adapter if length of the SSO password exceeds 8 characters.|  
|**MQIIH_CommitMode**|string|||  
|**MQIIH_Flags**|unsigned int|4||  
|**MQIIH_Format**|string|||  
|**MQIIH_LTermOverride**|string|8||  
|**MQIIH_MFSMapName**|string|8||  
|**MQIIH_ReplyToFormat**|string|||  
|**MQIIH_SecurityScope**|string|||  
|**MQIIH_TranInstanceId**|string|32|Hexadecimal string|  
|**MQIIH_TranState**|string|||  
  
## See Also  
 [MQSeries Adapter Properties](../core/mqseries-adapter-properties.md)   
 [Properties Related to BizTalk Server](../core/properties-related-to-biztalk-server.md)   
 [Data Type Conversion of Properties](../core/data-type-conversion-of-properties.md)
