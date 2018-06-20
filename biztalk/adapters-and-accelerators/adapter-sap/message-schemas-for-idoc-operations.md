---
title: "Message Schemas for IDOC Operations in the my SAP adapter in BizTalk | Microsoft Docs"
description: Message operations, structures, and actions to send and receive IDOCs using the mySAP adapter - BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 601aa9f9-e42f-47aa-b020-7a1eed4f0780
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Message Schemas for IDOC Operations
Intermediate documents (IDOCS) are standardized EDI-like documents supported by SAP for asynchronously communicating with both SAP and non-SAP systems. IDOCS are used to send and receive business documents like sales orders to or from a trading partner’s SAP system or external program.  

 Although the SAP system supports a number of port types to send and receive IDOCS (for example, a file port or a CPIC port), the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports sending and receiving IDOCS by using a tRFC port.  

- For an outbound IDOC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] acts as a tRFC client and invokes an RFC to send the IDOC to SAP.  

- For an inbound IDOC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] acts as a tRFC server and accepts a tRFC client call from SAP to receive the IDOC.  

  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces four operations under the IDOC node that you can use to send and receive IDOCS with an SAP system.  

- **SendIdoc**. Sends an IDOC to the adapter as string data. This operation is surfaced directly under the IDOC root node. The same operation is used for all IDOCs.  

- **Send**. Sends an IDOC to the adapter as strongly-typed data. This operation is surfaced under a node specific to each IDOC.  

- **ReceiveIdoc**. Receives an IDOC from the adapter as string data. This operation is surfaced directly under the IDOC root node. The same operation is used for all IDOCs.  

- **Receive**. Receives an IDOC from the adapter as strongly-typed data. This operation is surfaced under a node specific to each IDOC.  

> [!NOTE]
>  These four operations provide different ways of exchanging IDOCs between your program and the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. The adapter always uses an RFC (as discussed in the next section) to send or receive IDOCs with the SAP system.  

 In addition to using one of the four IDOC operations, you can also send or receive an IDOC by using one of the RFCs that are used internally by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to exchange IDOCs with the SAP system. For an overview of how the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports IDOCs, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md).  

 This topic contains information about the message schemas and message actions used for IDOC operations.  

## RFCs Used by the SAP Adapter to Send and Receive IDOCs  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the following remote function calls (RFCs) internally to exchange IDOCS with the SAP system. On the outbound side (adapter to the SAP system), the adapter acts as a tRFC client to invoke the RFC. On the inbound side (SAP to adapter), SAP invokes the RFC on the adapter, which acts as a tRFC server.  

|RFC|Description|  
|---------|-----------------|  
|IDOC_INBOUND_ASYNCHRONOUS|This function module is used from release 4.0 and later. It processes IDOCS in record types that are valid for 4.x releases. This ensures that longer IDOC segment names are supported.<br /><br /> The parameters to this RFC include:<br /><br /> - idoc_control_rec_40 (SAP structure is EDI_DC40)<br /><br /> - idoc_data_rec_40 (SAP structure is EDI_DD40)<br /><br /> The IDOC control record consists of the following fields:<br /><br /> - **Mestyp**. The logical message type. Conveys the business meaning of the message. This is a mandatory field.<br /><br /> - **Idoctyp**. The basic structure of the IDOC. This field identifies the layout set that uses this message. This is a mandatory field.<br /><br /> -                      **Cimtyp**. The structure of customer extension. If an SAP basic structure is extended, the customer must give a name to the structure of the extension. This is a mandatory field if a customer has made an enhancement; otherwise initial.<br /><br /> - **Partner fields**. These are send side and receive side partner parameters such as partner type, partner number, partner function.<br /><br /> The IDOC data record consists of the following fields:<br /><br /> - **Header fields**. Segment header fields like table name, segment number, segment type. These are mandatory fields.<br /><br /> -                      **Sdata**. 1000-byte character field for the data used by the IDOC .This is a mandatory field.|  
|INBOUND_IDOC_PROCESS|This function module is used for releases up to 4.0. It processes IDOCS in record types that are valid for 3.x releases. It is also possible to use this function module in 4.x.<br /><br /> The parameters to this RFC include:<br /><br /> - idoc_control (SAP structure is EDI_DC)<br /><br /> - idoc_data (SAP structure is EDI_DD)|  

## Operations to Send IDOCs  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes the Send and SendIdoc operations for clients to send IDOCs to an SAP system. For the Send operation, the IDOC is represented as strongly-typed data; for the SendIdoc operation, the IDOC is represented as string data. These operations determine how the IDOC data is represented between the adapter and your application. The adapter always sends IDOCs to SAP by using either the IDOC_INBOUND_ASYNCHRONOUS or the IDOC_INBOUND_PROCESS (t)RFC. To send an IDOC to your SAP system, you can either use the Send or SendIdoc operation, or you can directly invoke the appropriate RFC.  

### Message Structures for IDOC Client Operations  
 The following table shows the message structures for the Send and SendIdoc operations.  


|     Operation     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   XML Structure                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                                   Description                                                                                                                                                                                                                                                                                                                                                                   |
|-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       Send        | `<Send xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/                    [CIMTYP]/[RELNO]/Send">   <idocData>     <[EDI_DC40/EDI_DC] xmlns="/Types/Idoc/      [VERSION]/[IDOCTYP]/[CIMTYP]/[RELNO]">       <EDIDC_FIELD1>value1</ EDIDC_FIELD1>       <EDIDC_FIELD2>value2</ EDIDC_FIELD2>       …     </EDI_DC40>     <[SEGMENT_DEFN]_1>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_1>     <[SEGMENT_DEFN]_2>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_2>     …     </[EDI_DC40/EDI_DC]>   </idocData>   <guid>guid</guid> </Send>` |                                               Sends a strongly-typed IDOC to SAP<br /><br /> - IDOC schema is strongly-typed.<br /><br /> - Exposes control record fields.<br /><br /> - Exposes data record fields including segment headers and segment fields.<br /><br /> The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] associates a GUID with the SAP transaction ID (TID) that it uses to send the IDOC. You can choose whether to specify a GUID in the request message. If a GUID is not included in the request message, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] generates one. The GUID is returned in the response message.                                                |
|   Send Response   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         `<SendResponse xmlns="[MSG_VERSION]/Idoc/[VERSION]/         [IDOCTYP]/[CIMTYP]/[RELNO]/Send">   <guid>guid</guid> </SendResponse>`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Indicates that the IDOC has been sent to the SAP system.<br /><br /> If the **AutoConfirmSentIdocs** binding property is **true**, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] automatically confirms the transaction on the SAP system, and you can ignore the GUID returned in the response. If the **AutoConfirmSentIdocs** binding property is **false**, you must invoke the **RfcConfirmTransID** operation with the GUID returned by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to complete the transaction on the SAP system.<br /><br /> You can invoke the **SapAdapterUtilities.ConvertGuidToTid** method to obtain the TID associated with the logical unit of work (LUW). |
|     SendIdoc      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    `<SendIdoc xmlns="[MSG_VERSION]/Idoc">   <idocData>docDataString</idocData>   <guid>guid</guid> </SendIdoc>`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                   Sends a weakly-typed IDOC to SAP.<br /><br /> - IDOC schema is weakly-typed.<br /><br /> - Exposes the IDOC as a single string field that consists of the control record and data record.<br /><br /> The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] associates a GUID with the SAP TID that it uses to send the IDOC. You can choose whether to specify a GUID in the request message. If a GUID is not included in the request message, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] will generate one. The GUID is returned in the response message                                                                    |
| SendIdoc Response |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              `<SendIdocResponse xmlns="[MSG_VERSION]/Idoc">   <guid>guid</guid> </SendIdocResponse>`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |             Indicates that the IDOC has been sent to the SAP system.<br /><br /> If the **AutoConfirmSentIdocs** binding property is **true**, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] automatically confirms the transaction on the SAP system, and you can ignore the GUID returned in the response. If the **AutoConfirmSentIdocs** binding property is **false**, you must invoke the **RfcConfirmTransID** operation with the GUID returned by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]to complete the transaction on the SAP system.<br /><br /> You can invoke the **SapAdapterUtilities.ConvertGuidToTid** method to obtain the TID associated with the LUW.             |

 [MSG_VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.  

 [VERSION] = IDOC release version (2 or 3).  

 [IDOCTYP] = IDOC type; for example, ORDERS05.  

 [CIMTYP] = Cimtype of the customized IDOC.  

 [RELNO] = Release number; for example, 620.  

 [EDI_DC40/EDI_DC]  = EDI_DC40 for release version 3 IDOCs and EDI_DC for release version2 IDOCs.  

 [EDIDC_FIELD] = Field constituting the EDI_DC40/EDI_DC control record structure.  

 [SEGMENT_DEFN] = Segment definition name (NOT segment type name); for example, E2EDK01005. Note that the segment definition node could also appear under a segment group node, based on the structure of the IDOC.  

 [DATAHEADERCOLUMN_(SEGHDR_FLD)] = Each segment has a segment header that consists of a standard set of header fields followed by the segment data. The segment data consists of all segment fields and data. This node represents the segment header fields; for example, DATAHEADERCOLUMN_SEGNAM.  

 [SEG_FIELD] = Segment field name constituting a particular segment definition [SEGMENT_DEFN].  

 [guid] = GUID parameter.  

### Message Actions for IDOC Client Operations  
 The following table shows the message actions for the Send and SendIdoc operations.  


|     Operation     |                                   Action                                   |                                   Example                                   |
|-------------------|----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
|       Send        |     [MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Send      |     http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Send      |
|   Send Response   | [MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Send/response | http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Send/response |
|     SendIdoc      |                      [MESSAGE_VERSION]/Idoc/SendIdoc                       |           http://Microsoft.LobServices.Sap/2007/03/Idoc/SendIdoc            |
| SendIdoc Response |                  [MESSAGE_VERSION]/Idoc/SendIdoc/response                  |       http://Microsoft.LobServices.Sap/2007/03/Idoc/SendIdoc/response       |

 [MESSAGE_VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.  

 [VERSION] = IDOC release version (2 or 3).  

 [IDOCTYP] = IDOC type; for example, ORDERS05.  

 [CIMTYP] = Cimtype of the customized IDOC.  

 [RELNO] = Release number; for example, 620.  

## Operations to Receive IDOCs  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes the Receive and ReceiveIdoc operations for applications to receive IDOCs from an SAP system. For the Receive operation, the IDOC is represented as strongly-typed data; for the ReceiveIdoc operation, the IDOC is represented as string data.  

 These operations determine how the IDOC data is emitted by the adapter to your application. The adapter always receives IDOCs from the SAP system as either an IDOC_INBOUND_ASYNCHRONOUS or IDOC_INBOUND_PROCESS tRFC. You can either use the Receive or ReceiveIdoc operation, or you can receive IDOC data in RFC format. You set the **ReceiveIdocFormat** binding property to specify the format in which the adapter emits the IDOC data to your application. For more information about the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  

### Message Structures for IDOC Receive Operations  
 The following table shows the message structures for the Receive and ReceiveIdoc operations.  

|Operation|XML Structure|Description|  
|---------------|-------------------|-----------------|  
|Receive|`<Receive xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/                 [CIMTYP]/[RELNO]/Receive">   <idocData>     <[EDI_DC40/EDI_DC] xmlns="/Types/Idoc/      [VERSION]/[IDOCTYP]/[CIMTYP]/[RELNO]">       <EDIDC_FIELD1>value1</ EDIDC_FIELD1>       <EDIDC_FIELD2>value2</ EDIDC_FIELD2>       …     </EDI_DC40>     <[SEGMENT_DEFN]_1>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_1>     <[SEGMENT_DEFN]_2>       <[DATAHEADERCOLUMN_[SEGHDR_FLD1]>         header_value_1       </[DATAHEADERCOLUMN_[SEGHDR_FLD1]>       <[DATAHEADERCOLUMN_[SEGHDR_FLD2]>         header_value_2       </[DATAHEADERCOLUMN_[SEGHDR_FLD2]>       …       <SEG_FIELD1>value1</SEG_FIELD1>       <SEG_FIELD2>value2</SEG_FIELD2>       …     </[SEGMENT_DEFN]_2>     …     </[EDI_DC40/EDI_DC]>   </idocData> </Receive>`|Receives a strongly-typed IDOC from SAP<br /><br /> - IDOC schema is strongly-typed.<br /><br /> - Exposes control record fields.<br /><br /> - Exposes data record fields including segment headers and segment fields.|  
|Receive Response|`<ReceiveResponse xmlns="[MSG_VERSION]/Idoc/[VERSION]/[IDOCTYP]/         [CIMTYP]/[RELNO]/Receive"> </ReceiveResponse>`|Indicates that the IDOC has been received from the SAP system.|  
|ReceiveIdoc|`<ReceiveIdoc xmlns="[MSG_VERSION]/Idoc">   <idocData>docDataString</idocData> </ReceiveIdoc>`|Receives a weakly-typed IDOC from SAP.<br /><br /> - IDOC schema is weakly-typed.<br /><br /> - Exposes the IDOC as a single string field that consists of the control record and data record.|  
|ReceiveIdoc Response|`<ReceiveIdocResponse xmlns="[MSG_VERSION]/Idoc"> </ReceiveIdocResponse>`|Indicates that the IDOC has been received from the SAP system.|  

 [MSG_VERSION] = The message version string; for example, http://Microsoft.LobServices.Sap/2007/03.  

 [VERSION] = IDOC release version (2 or 3).  

 [IDOCTYP] = IDOC type; for example, ORDERS05.  

 [CIMTYP] = Cimtype of the customized IDOC.  

 [RELNO] = Release number; for example, 620.  

 [EDI_DC40/EDI_DC]  = EDI_DC40 for release version 3 IDOCs and EDI_DC for release version 2 IDOCs.  

 [EDIDC_FIELD] = Field constituting the EDI_DC40/EDI_DC control record structure.  

 [SEGMENT_DEFN] = Segment definition name (NOT segment type name); for example, E2EDK01005. The segment definition node can also appear under a segment group node, based on the structure of the IDOC.  

 [DATAHEADERCOLUMN_(SEGHDR_FLD)] = Each segment has a segment header that consists of a standard set of header fields followed by the segment data. The segment data consists of all segment fields and data. This node represents the segment header fields; for example, DATAHEADERCOLUMN_SEGNAM.  

 [SEG_FIELD] = Segment field name constituting a particular segment definition [SEGMENT_DEFN].  

#### Receiving an IDOC in RFC Format  
 You can also receive IDocs in RFC format. The RFCs used to receive IDOCs from SAP are:  

- IDOC_INBOUND_ASYNCHRONOUS for version 3 IDOCs.  

- INBOUND_IDOC_PROCESS for version 2 IDOCs.  

  The following code shows the structure of an IDOC received as an IDOC_INBOUND_ASYNCHRONOUS operation.  

```  
<IDOC_INBOUND_ASYNCHRONOUS xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <IDOC_CONTROL_REC_40>  
    <EDI_DC40 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <EDIDC_FIELD1>field1</EDIDC_FIELD1>  
      <EDIDC_FIELD2>field2</EDIDC_FIELD2>  
      …  
    </EDI_DC40>  
  <IDOC_DATA_REC_40>  
    <EDI_DD40 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <[SEG_HEADER_FIELD1]>value1</[SEG_HEADER_FIELD1]>  
      <[SEG_HEADER_FIELD2]>value2</[SEG_HEADER_FIELD2]>  
      …  
      <SDATA>segment value</SDATA>  
    </EDI_DD40>  
    …  
  </IDOC_DATA_REC_40>  
</IDOC_INBOUND_ASYNCHRONOUS>  
```  

 [EDIDC_FIELD] = Field constituting the EDI_DC40/EDI_DC control record structure  

 [SEG_HEADER_FIELD] = Each segment has a segment header that consists of a standard set of header fields followed by the segment data. The segment data consists of all segment fields and data. This node represents the segment header fields; for example, SEGNAM, MANDT, and DOCNUM.  

 For more information about the format of tRFC operations, see [Message Schemas for tRFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md).  

### Message Actions for IDOC Receive Operations  
 The following table shows the message actions for the Receive and ReceiveIdoc operations.  


|      Operation       |                                    Action                                     |                                    Example                                     |
|----------------------|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
|       Receive        |     [MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Receive      |     http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Receive      |
|   Receive Response   | [MESSAGE_VERSION]/Idoc/[VERSION] /[IDOCTYP]/[CIMTYP]/[RELNO]/Receive/response | http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Receive/response |
|     ReceiveIdoc      |                      [MESSAGE_VERSION]/Idoc/ReceiveIdoc                       |           http://Microsoft.LobServices.Sap/2007/03/Idoc/ReceiveIdoc            |
| ReceiveIdoc Response |                  [MESSAGE_VERSION]/Idoc/ReceiveIdoc/response                  |       http://Microsoft.LobServices.Sap/2007/03/Idoc/ReceiveIdoc/response       |

