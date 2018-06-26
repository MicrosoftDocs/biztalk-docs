---
title: "Message Schemas for RFC Operations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RFC operations, message structure for"
  - "RFC operations, message actions for"
ms.assetid: 50cd9b28-2e66-4c76-9d19-f0da6e7b8e10
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for RFC Operations
The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces SAP Remote Function Calls (RFC) as operations. This topic contains information about the message schemas and message actions used for RFC operations. The message structure is the same for inbound and outbound RFC operations. For an overview of the RFC operations that the adapter supports, see [Operations on RFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md).  

 You can also invoke BAPIs as RFC operations on the adapter. An example of the message structure for such an invocation is included in this topic.  

## Message Structure for RFC Operations  
 The following table shows the RFC message schemas. Each RFC operation consists of a request message and a reply (response) message.  


|                             Message                              |                                                                                                                                                                                                                         XML Message Structure                                                                                                                                                                                                                          |                                                                                                                                                                                                     Description                                                                                                                                                                                                      |
|------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                   RFC<br /><br /> ([RFC_NAME])                   | `<[RFC_NAME] xmlns="[VERSION]/Rfc/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]>` |                                                                                              Invoke an RFC on the SAP system.<br /><br /> - Import, changing, and table parameters are supported.<br /><br /> - Import and changing parameters can be of SAP STRUCTURE TYPES, SAP TABLE TYPES or SAP simple data types.                                                                                              |
|                RFC Response ([RFC_NAME]Response)                 |     `<[RFC_NAME]Response xmlns="[VERSION]/Rfc/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME>     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]Response>`      | RFC return.<br /><br /> - Export, changing, and table parameters are supported.<br /><br /> **Note:** By default, table parameters are not surfaced in the response message. If you require table parameters in response message, you must pass empty table parameters in the request message.<br /><br /> - Import and changing parameters can be of SAP STRUCTURE TYPES, SAP TABLE TYPES or SAP simple data types. |
|         RfcGetAttributes<br /><br /> (RfcGetAttributes)          |                                                                                                                                                                                                                `<RfcGetAttributes> </RfcGetAttributes>`                                                                                                                                                                                                                |                                                  RfcGetAttributes is an RFC SDK API operation that is surfaced by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. The RfcGetAttributes operation enables a client program to retrieve the language, the system ID, and the partner code page that are associated with the RFC connection.                                                   |
| RfcGetAttributes Response<br /><br /> (RfcGetAttributesResponse) |                                                                                                                                                          `<RfcGetAttributesResponse>   <Language>lang</Language>   <SysId>id</SysId>   <PartnerCodePage>pnrcp</PartnerCodePage> </RfcGetAttributesResponse>`                                                                                                                                                           |                                                                                                                              The response to the RfcGetAttributes operation returns the language, the system ID, and the partner code page that are associated with the RFC connection.                                                                                                                              |

 [VERSION] = The message version string; for example, http://Microsoft.LobServices.SAP/2007/03.  

 [RFC_NAME] = Name of the RFC; for example, RFC_CUSTOMER_GET.  

 [IN_PARAM_NAME] = The name of an RFC Import parameter.  

 [OUT_PARAM_NAME] = The name of an RFC Export parameter.  

 [INOUT_PARAM_NAME] = The name of an RFC Changing parameter.  

 [TABLE_PARAM_NAME] = The name of an RFC Table parameter.  

 [STRUCT_PARAM_NAME] = The name of an RFC Structure parameter.  

## Message Actions for RFC Operations  
 The following table shows the message actions for RFC operations.  


|         Operation         |           Message Action           |                                Example                                 |
|---------------------------|------------------------------------|------------------------------------------------------------------------|
|        [RFC_NAME]         |      [VERSION]/Rfc/[RFC_NAME]      |     http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET      |
|    [RFC_NAME] Response    | [VERSION]/Rfc/[RFC_NAME]/response  | http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET/response |
|     RfcGetAttributes      |     [VERSION]/RfcGetAttributes     |       http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes        |
| RfcGetAttributes Response | [VERSION/RfcGetAttributes/response |   http://Microsoft.LobServices.Sap/2007/03/RfcGetAttributes/response   |

 [VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.  

 [RFC_NAME] = The name of the RFC to be invoked; for example, RFC_CUSTOMER_GET.  

## Invoking a BAPI as an RFC Operation  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces BAPIs both as RFC operations and as methods of business objects. As RFC operations, BAPIs are surfaced by name. For more information about invoking BAPIs by using the business object interface, see [Operations on BAPIs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).  

 The following XML shows the message structure for a BAPI (BAPI_CUSTOMER_GETDETAIL2) that is invoked as an RFC. The message action for this operation is: http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_CUSTOMER_GETDETAIL2.  

```  
<BAPI_CUSTOMER_GETDETAIL2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <COMPANYCODE>1001</COMPANYCODE>  
  <CUSTOMERNO>0000001001</CUSTOMERNO>  
  <CUSTOMERBANKDETAIL>  
    <BAPICUSTOMER_02 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <CUSTOMER />  
      <BANK_CTRY />  
      <BANK_KEY />  
      <BANK_ACCT />  
      <CTRL_KEY />  
      <PARTNER_BK />  
      <COLL_AUTH />  
      <BANK_REF />  
    </BAPICUSTOMER_02>  
  </CUSTOMERBANKDETAIL>  
</BAPI_CUSTOMER_GETDETAIL2>  
```  

## See Also  
 [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)