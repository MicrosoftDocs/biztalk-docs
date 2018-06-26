---
title: "Message Schemas for tRFC Operations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tRFC operations, message structure for"
  - "tRFC operations, message schemas for"
  - "tRFC operations, message actions for"
ms.assetid: 0e269555-f0a1-40ae-a1b5-d8c4981e730f
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for tRFC Operations
Transactiostructnal Remote Function Calls (tRFCs) are used to execute RFC calls in a logical unit of work (LUW). The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports multiple tRFCs per LUW for inbound tRFC calls. For outbound (client) tRFC calls, the adapter can support only a single tRFC in an LUW; it therefore for creates an LUW on SAP for each client tRFC call. For more information about how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports tRFC operations, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md). This section describes the message schemas and actions for tRFC operations.  

## Message Structure for tRFC Operations  
 Each tRFC operation consists of a request message and a reply (response) message. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] associates a GUID with the SAP system transaction ID (TID) that identifies the LUW on the SAP system. This GUID can be present in both the tRFC request and response messages in the \<TransactionalRfcOperationIdentifier\> element.  

-   For outbound tRFC calls, you can pass a GUID to the adapter in the tRFC request message. If you do not supply a GUID, the adapter generates one for you. The adapter always returns the GUID in the tRFC response message. You pass this GUID in the RfcConfirmTransID operation to confirm the TID on the SAP system.  

-   For inbound tRFC calls, the adapter passes a GUID that it has generated and mapped to the SAP TID in the tRFC request message. You can optionally return this GUID in the response message.  

> [!IMPORTANT]
>  In some scenarios, for example to troubleshoot an issue on the SAP system, you may need the actual value of the SAP TID that identifies the tRFC on the SAP system. You can get the value of the SAP TID that is associated with a GUID by calling the **ConvertGuidToTid** method. For more information about **ConvertGuidToTid**, see [Special Operations](../../adapters-and-accelerators/adapter-sap/special-operations.md).  

 The following table shows the message schemas used for tRFC operations and for the RfcConfirmTransID operation. The RfcConfirmTransID operation is surfaced by the adapter so that you can confirm the SAP TID in client tRFC calls.  


|                             Operation                             |                                                                                                                                                                                                                                                                         XML Structure                                                                                                                                                                                                                                                                         |                                                                                                                                                                                                                                                                                                                                                                                                                             Description                                                                                                                                                                                                                                                                                                                                                                                                                              |
|-------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                   tRFC<br /><br /> ([RFC_NAME])                   | `<[RFC_NAME] xmlns="[VERSION]/Trfc/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Trfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   …   <TransactionalRfcOperationIdentifier>GUID   </TransactionalRfcOperationIdentifier> </[RFC_NAME]>` | Invokes a tRFC on the SAP system.<br /><br /> - Import, changing, and table parameters are supported.<br /><br /> - Import and changing parameters can be of SAP STRUCTURE TYPES, SAP TABLE TYPES or SAP simple data types.<br /><br /> - tRFC client calls do not have values returned in the output side. SAP asynchronously executes them with only input-side values.<br /><br /> The \<TransactionalRfcOperationIdentifier\> element:<br /><br /> - For outbound tRFC calls, you can optionally specify a GUID that should be mapped to the SAP TID by the adapter in this element. If a GUID is not specified, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] generates one and maps it to the SAP TID for the tRFC.<br /><br /> - For inbound tRFC calls, the adapter passes the GUID that is mapped to the SAP TID in this element. |
|          tRFC Response<br /><br /> ([RFC_NAME]Response)           |                                                                                                                                                                                                   `<[RFC_NAME]Response xmlns="[VERSION]/Trfc/">   <TransactionalRfcOperationIdentifier>GUID   </TransactionalRfcOperationIdentifier> </[RFC_NAME]Response>`                                                                                                                                                                                                   |                                                                                                                                                                   Indicates that the RFC has been sent to the SAP system.<br /><br /> - tRFC client calls do not have values returned in the output side. SAP asynchronously executes them with only input-side values.<br /><br /> The \<TransactionalRfcOperationIdentifier\> element:<br /><br /> - For outbound tRFC calls, the adapter sends the GUID associated with the SAP TID for the tRFC in this element.<br /><br /> - For inbound tRFC calls you can optionally return the GUID that was sent by the adapter in the request message.                                                                                                                                                                    |
|         RfcConfirmTransID<br /><br /> (RfcConfirmTransID)         |                                                                                                                                                                                                    `<RfcConfirmTransID xmlns="[VERSION]/Trfc/">   <TransactionalRfcOperationIdentifier>GUID   </TransactionalRfcOperationIdentifier> </RfcConfirmTransID>`                                                                                                                                                                                                    |                                                                                                                                                             The RfcConfirmTransID operation confirms the TID used in an outbound tRFC operation on the SAP system.<br /><br /> The \<TransactionalRfcOperationIdentifier\> element contains the GUID that is mapped to the TID associated with the outbound tRFC call. You should set this to the value of the GUID that was returned by the adapter in the tRFC response message.<br /><br /> For more information about the RfcConfirmTransID operation, see [Special Operations](../../adapters-and-accelerators/adapter-sap/special-operations.md).                                                                                                                                                              |
| RfcConfirmTransIDResponse<br /><br /> (RfcConfirmTransIDResponse) |                                                                                                                                                                                                                                      `<RfcConfirmTransIDResponse xmlns="[VERSION]/Trfc/"> </RfcConfirmTransIDResponse>`                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                   Indicates that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] has confirmed the TID on the SAP system.                                                                                                                                                                                                                                                                                                                                                                    |

 [VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.  

 [RFC_NAME] = Name of the RFC; for example, RFC_CUSTOMER_GET.  

 [IN_PARAM_NAME] = The name of the RFC Import parameter.  

 [INOUT_PARAM_NAME] = The name of an RFC Changing parameter.  

 [TABLE_PARAM_NAME] = The name of an RFC Table parameter.  

 [STRUCT_PARAM_NAME] = The name of an RFC Structure parameter.  

 GUID = A GUID that identifies the SAP TID associated with the tRFC.  

## Message Actions for tRFC Operations  
 The following table shows the message actions that are used for tRFC operations.  


|         Operation          |              Message Action              |                                 Example                                  |
|----------------------------|------------------------------------------|--------------------------------------------------------------------------|
|         [RFC_NAME]         |        [VERSION]/Trfc/[RFC_NAME]         |      http://Microsoft.LobServices.Sap/2007/03/Trfc/RFC_CUSTOMER_GET      |
|    [RFC_NAME] Response     |    [VERSION]/Trfc/[RFC_NAME]/response    | http://Microsoft.LobServices.Sap/2007/03/Trfc/RFC_CUSTOMER_GET/response  |
|     RfcConfirmTransID      |     [VERSION]/Trfc/RfcConfirmTransID     |     http://Microsoft.LobServices.Sap/2007/03/Trfc/RfcConfirmTransID      |
| RfcConfirmTransID Response | [VERSION/Trfc/RfcConfirmTransID/response | http://Microsoft.LobServices.Sap/2007/03/Trfc/RfcConfirmTransID/response |

 [VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.  

 [RFC_NAME] = The name of the RFC to be invoked; for example, RFC_CUSTOMER_GET.  

## See Also  
 [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)