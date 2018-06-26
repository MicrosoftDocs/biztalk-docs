---
title: "BizTalk Framework Schema and Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8986e4a7-0c0a-415f-8a74-4fca71d3f1b5
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BizTalk Framework Schema and Properties
The **http://schemas.microsoft.com/BizTalk/2003/btf2-properties** namespace contains properties you can use to set message and part context properties for the BizTalk Framework Disassembler pipeline component. The BizTalk Framework Disassembler pipeline component uses these properties to generate the appropriate headers in the message that is created. The following table describes the BizTalk Framework properties.  

## Properties list  

|Name|Type|Description|  
|----------|----------|-----------------|  
|**IsReliable**|xs:boolean|Indicates whether the BizTalk Framework message should be resent until an acknowledgment is received from a destination. This property is set internally by BizTalk Framework components and used by the engine. Do not change the value in this property from your code.|  
|**PassAckThrough**|xs:boolean|Indicates whether an acknowledgement message should be passed through a BizTalk Framework Dissembler pipeline component instead of being consumed.|  
|**eps_to_address**|xs:string|Specifies the destination address.|  
|**eps_to_address_type**|xs:string|Specifies the destination address type.|  
|**eps_from_address**|xs:string|Specifies the source address.|  
|**eps_from_address_type**|xs:string|Specifies the source address type.|  
|**prop_identity**|xs:string|A URI reference that uniquely identifies the BizTalk Framework document for purposes of logging, tracking, error handling, or other document processing and correlation requirements.|  
|**prop_sentAt**|xs:string|The send timestamp of the BizTalk Framework document.|  
|**prop_topic**|xs:string|A URI reference that uniquely identifies the overall purpose of the BizTalk Framework document.|  
|**svc_deliveryRctRqt_sendTo_address**|xs:string|Specifies the address to which the delivery receipt for the BizTalk Framework document should be sent.|  
|**svc_deliveryRctRqt_sendTo_address_type**|xs:string|Specifies the type of address to which the delivery receipt for the BizTalk Framework document should be sent.|  
|**svc_deliveryRctRqt_sendBy**|xs:dateTime|Specifies the time (in minutes) by which the delivery receipt for the BizTalk Framework document must be received.|  
|**svc_commitmentRctRqt_sendTo_address**|xs:string|Specifies the address where the notification of the recipient's decision about processing of the sender's request should be sent to.|  
|**svc_commitmentRctRqt_sendTo_address_type**|xs:string|Specifies the type of address where the notification of the recipient's decision about processing of the sender's request should be sent to.|  
|**svc_commitmentRctRqt_sendBy**|xs:dateTime|Specifies the time (in minutes) by which the commitment receipt for the BizTalk Framework document must be received by the sender.|  
|**prc_type**|xs:string|Provides a URI reference that specifies the type of business process involved in the processing of BizTalk Framework messages.|  
|**prc_instance**|xs:string|Provides URI reference that uniquely identifies a specific instance of the business process that the BizTalk Framework document is associated with.|  
|**deliveryRct_receivedAt**|xs:dateTime|Specifies the receiving timestamp for the document acknowledged by this receipt. The receiving timestamp may reflect either the time when the first copy was received or the time at which the copy being acknowledged was received.|  
|**deliveryRct_identity**|xs:string|Specifies an identity of the BizTalk Framework document acknowledged by the delivery receipt.|  
|**commitmentRct_identity**|xs:string|Specifies the identity of a BizTalk Framework document acknowledged by the commitment receipt.|  
|**commitmentRct_decidedAt**|xs:string|Specifies the processing decision timestamp for the document acknowledged by this receipt.|  
|**commitmentRct_decision**|xs:string|Specifies the actual decision, with possible values of positive or negative.|  
|**commitmentRct_commitmentCode**|xs:QName|Specifies the qualified name (in XSD) that specifies a more specific status regarding the processing decision.|  

## See Also  
- **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
- [Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md)
