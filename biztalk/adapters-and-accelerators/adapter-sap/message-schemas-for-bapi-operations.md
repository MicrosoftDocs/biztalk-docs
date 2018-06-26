---
title: "Message Schemas for BAPI Operations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAPI operations, message schemas for"
  - "BAPI operations, message structure for"
  - "BAPI operations, message actions for"
ms.assetid: ef4d88e8-f31a-4b68-a303-6885b6f8c083
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for BAPI Operations
The following sections describe the message schemas and message actions used to invoke BAPIs on the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] as methods of business objects. You can also invoke BAPIs as RFC operations on the adapter. For more information about the messages used to invoke RFCs, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md). Regardless of how you invoke a BAPI on the adapter, the adapter always invokes the BAPI as an RFC on the SAP system. For an overview of how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports BAPIs, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).  

## Message Structure for Business Object Operations  
 The following table shows the message schemas used to invoke a BAPI as a business object method.  

|Operation|XML Structure|Description|  
|---------------|-------------------|-----------------|  
|[BUSOBJ_METHOD]|`<[BUSOBJ_METHOD] xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]>`|Invoke a business object method on an SAP system.<br /><br /> Import, changing, and table parameters are supported.|  
|[BUSOBJ_METHOD] Response|`<[BUSOBJ_METHOD]Response xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]Response>`|Business object method response.<br /><br /> Export, changing, and table parameters are supported.<br /><br /> **Note** By default, table parameters are not surfaced in the response message. If you require table parameters in response message, you must pass empty table parameters in the request message.|  

 [VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.  

 [BUSOBJ_METHOD] = The name of a business object method; for example, CREATEFROMDAT2.  

 [IN_PARAM_NAME] =The name of a BAPI import parameter.  

 [OUT_PARAM_NAME] = The name of a BAPI export parameter.  

 [INOUT_PARAM_NAME] = The name of a BAPI changing parameter.  

 [TABLE_PARAM_NAME] = The name of a BAPI table parameter.  

 [STRUCT_PARAM_NAME] = The name of a BAPI structure parameter.  

## Message Actions for Business Object Operations  
 The following table shows the message actions that are used to invoke BAPIs as business object methods.  


|        Operation         |                            Message Action                             |                                                   Example                                                    |
|--------------------------|-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|     [BUSOBJ_METHOD]      |     [VERSION]/Bapi/[BUSOBJ_NAME]/[BUSOBJ_METHOD]/[BAPI_RFC_NAME]      |     http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2      |
| [BUSOBJ_METHOD] Response | [VERSION]/Bapi/[BUSOBJ_NAME]/[BUSOBJ_METHOD]/[BAPI_RFC_NAME]/response | http://Microsoft.LobServices.Sap/2007/03/Bapi/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2/response |

 [VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.  

 [BUSOBJ_NAME] = The name of the business object; for example, BUS2032.  

 [BUSOBJ_METHOD] = The method of the business object; for example, CREATEFROMDAT2.  

 [BAPI_RFC_NAME] = The RFC name for the BAPI; for example, BAPI_SALESORDER_CREATEFROMDAT2.  

## See Also  
 [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)