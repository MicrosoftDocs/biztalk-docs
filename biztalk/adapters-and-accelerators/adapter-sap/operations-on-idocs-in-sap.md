---
title: "Operations on IDOCs in SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDOC, operations to receive an"
  - "IDOCs"
  - "IDOCs, operations on"
  - "tRFC server"
  - "IDOC, operations to send an"
  - "RFC server"
ms.assetid: 6abcc646-c7a3-48cf-a09e-01f516dcef97
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on IDOCs in SAP
IDOCs are standardized EDI-like documents that SAP supports for asynchronously communicating with SAP and non-SAP systems. IDOCs are used for sending and receiving “business” documents such as sales orders, for example, to or from a trading partner’s SAP system or an external program.  
  
 Although the SAP system supports a number of port types to send and receive IDOCs (such as file port, CPIC port), the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports sending and receiving IDOCs via the tRFC port.  
  
## Operations to Send an IDOC  
 All IDOC calls to SAP are internally treated as tRFC calls in which the adapter acts as a tRFC client and calls an RFC in SAP to send an IDOC. Just like any other tRFC client call, the adapter client optionally passes a GUID to the adapter, which in turn associates it with the transaction ID (TID) that it uses for the call on the SAP system. (If the adapter client does not pass a GUID, the adapter generates its own GUID.) The GUID is returned to the adapter client in the response message. The adapter client can use this GUID to confirm the TID on the SAP system. The actual SAP TID used by the adapter for the tRFC call can be obtained by invoking a special static method in the SAP binding, **ConvertGuidToTid**. Having the actual TID may be useful for troubleshooting issues on the SAP system.  
  
 After the call to send the IDOC is completed, the TID must be confirmed on the SAP system. This enables the SAP system to delete the TID from its database. The adapter client can confirm the TID on the SAP system.  
  
- Explicitly, by invoking the **RfcConfirmTransID** operation on the adapter. This operation takes a GUID (returned in the response message above) and causes the adapter to confirm the associated TID on the SAP system.  
  
- Implicitly, by setting the **AutoConfirmSentIdocs** binding property. If this binding property is true, the adapter automatically commits the TID after it sends the IDOC to the SAP system. See [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md) for more information.  
  
  The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses the following RFCs to send an IDOC:  
  
- INBOUND_IDOC_PROCESS. This function module is used for SAP releases before 4.0.  
  
- IDOC_INBOUND_ASYNCHRONOUS. This function module is used for SAP release 4.0 and later.  
  
### Sending IDOCs with Segment Data Across Multiple Lines  
 IDOCs are constituted of segments. Each segment entry in an IDOC flat-file contains the segment header info (containing the DOCNUM field) and the segment data. In some IDOCs, the segment data can be split across multiple lines. For example:  
  
```  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
Segment data wrapped from the previous line  
Segment header (DOCNUM is one of the fields here)  |  Segment data  
```  
  
 The WCF-based [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports sending such IDOCs to the SAP system. To support sending such IDOCs, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] determines whether each segment data is a continuation of the previous one, or whether it is a new segment data. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] decides this by parsing each segment header and looking for the DOCNUM field. If the segment data is split across two lines, the second line does not have a segment header and as a result the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not find the DOCNUM field. Hence, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can determine that it is a continuation of the previous segment data.  
  
 For example, in the representation of an IDOC shown above, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] does not find any DOCNUM field in “`Segment data wrapped from the previous line`” and is able to decide that the line is a continuation of the previous segment data. Considering the size of IDOC flat files in production environments, performing such checks for each segment data may result in increased processing time.  
  
> [!NOTE]
>  The adapter uses the DOCNUM field instead of a carriage return line feed (CRLF) to identify and extract each segment record from IDOC data. If the DOCNUM fields in the control and data records are invalid or partly blank, the adapter fails to parse the IDOC. Hence, the IDOC is not sent to the SAP system.  
  
### Operations to Send an IDOC  
 The following operations are supported for sending IDOCs to an SAP system:  
  
- **Send**. Use this operation to send an IDOC to the SAP system using a strongly-typed schema. The schema for this operation exposes control record fields and data record fields, including segment headers and segment fields. The Send operation is specific to an IDocType + CimType + ReleaseNumber + Version combination.  
  
   This operation is surfaced for each IDOC and is available under a specific IDOC node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
  > [!NOTE]
  >  To be able to successfully perform a **Send** operation, you must have relevant authorization in the SAP system. For more information.  
  
- **SendIdoc**. Use this operation to send an IDOC to the SAP system using a weakly-typed schema. The schema for this operation exposes IDOCs as a single string field consisting the control record and data record. The SendIdoc operation takes an IDOC string and a GUID as a parameter.  
  
   This is a single operation surfaced for all IDOCs exposed by the SAP system and is available under the root **IDOC** node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
  For more information about:  
  
- Sending an IDOC to an SAP system using BizTalk Server, see [Send IDOCs to SAP by Using BizTalk Server](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md).  
  
- Sending an IDOC to an SAP system using WCF service model, see [Send IDOCs to SAP by Using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md).  
  
- Message structures and SOAP action for sending an IDOC, see [Message Schemas for IDOC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).  
  
## Operations to Receive an IDOC  
 To receive an IDOC, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can behave either as a tRFC server or an RFC server:  
  
- For the adapter to behave as a tRFC server, the binding property **TidDatabaseConnectionString** must be set to the connection string for the TID database on your computer. For a tRFC server scenario, the adapter accepts a tRFC client call from the SAP system to receive the IDOC.  
  
- For the adapter to behave as an RFC server, the **TidDatabaseConnectionString** should be null (default). For an RFC server scenario, the adapter accepts an RFC client call from the SAP system to receive the IDOC.  
  
  The following RFCs are used to send and receive IDOCs; when sending IDOCs, the adapter uses these RFCs, whereas when receiving IDOCS, the SAP system uses them.  
  
- INBOUND_IDOC_PROCESS. This function module is used for SAP releases before 4.0.  
  
- IDOC_INBOUND_ASYNCHRONOUS. This function module is used for SAP release 4.0 and later.  
  
  The following operations are supported for receiving IDOCs from an SAP system:  
  
- **Receive**. Use this operation to receive an IDOC from the SAP system using a strongly-typed schema. The schema for this operation exposes control record fields and data record fields including segment headers and segment fields.  
  
   This operation is surfaced for each IDOC and is available under a specific IDOC node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
  > [!NOTE]
  >  To be able to successfully perform a **Receive** operation, you must have relevant authorization in the SAP system. For more information.  
  
  > [!NOTE]
  >  Using the **Receive** operation, you can also receive multiple IDOCs.  
  
- **ReceiveIdoc**. Use this operation to receive an IDOC from the SAP system using a weakly-typed schema. The schema for this operation exposes IDOCs as a single string field consisting of the control record and data record. This operation receives IDOCs as a string in an XML message under the \<idocData\> tag.  
  
   This is a single operation surfaced for all IDOCs exposed by the SAP system and is available under the root **IDOC** node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
  When receiving IDOCs, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports different message formats, which can be specified as a value for the binding property, **ReceiveIDocFormat** exposed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
- If set to "Typed", the XML schema is strongly typed to the specific IDOC being received. (The schema for this message can be seen from the Receive operations. Note that the schema is different for different IDOCs). This yields an XML IDOC.  
  
- If set to "String", the incoming IDOC data is returned as a String value. (The schema for this message can be seen from the ReceiveIdoc operation). This yields an XML message with the \<idocData\> tag.  
  
- If set to "Rfc", the message schema matches the RFC (or tRFC) schema for the RFC operations IDOC_INBOUND_ASYNCHRONOUS or INBOUND_IDOC_PROCESS, depending on the incoming IDOC version. If you specify this binding property you should use the IDOC_INBOUND_ASYNCHRONOUS or INBOUND_IDOC_PROCESS RFC to receive the IDOC. In the first two options, the adapter internally uses this RFC. In this option, you explicitly use this RFC to receive an IDOC.  
  
  The operation that you use to receive an IDOC must match the format of the IDOC data emitted by the adapter. The following table provides a summary of the different combinations in which you can receive an IDOC from SAP.  
  
|To receive an IDOC using|Set the binding property ReceiveIDOCFormat to|  
|------------------------------|---------------------------------------------------|  
|**Receive** operation|Typed|  
|**ReciveIdoc** operation|String|  
|IDOC_INBOUND_ASYNCHRONOUS RFC|Rfc|  
|INBOUND_IDOC_PROCESS RFC|Rfc|  
  
 Another binding property **PadReceivedIdocsWithSpaces** pads the received IDOC with white spaces for optional fields when receive format expected is “String”. This enables compatibility with the IDOC data format received using the previous version of the adapter.  
  
 For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite Binding Properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
 For more information about:  
  
-   Receiving an IDOC from an SAP system using BizTalk Server, see [Receive IDOCs from SAP by Using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md).  
  
-   Receiving an IDOC from an SAP system in a transactional context using BizTalk Server, see [Receive IDOCs from SAP in a Transactional Context by Using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md).  
  
-   Message structures and SOAP action for receiving an IDOC, see [Message Schemas for IDOC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).  
  
##  <a name="BKMK_Authorize"></a> SAP Authorization for Using Send or Receive Operations  
 When you use the **Send** or **Receive** operations to send or receive IDOCs using a strongly-typed schema, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] internally invokes the IDOCTYPE_READ_COMPLETE RFC to retrieve the metadata for the IDOC. Invoking this RFC requires the following authorization in SAP:  
  
```  
Authorisation object S_IDOCDEFT, Fields:  
EDI_TCD, value 'WE30'  
ACTVT, value - 03 (display)  
EDI_DOC, value  *  
EDI_CIM, value *  
```  
  
 You can use the SU01 transaction in SAP to add an authorization object. For more information about the transaction, contact your SAP administrator or refer to SAP documentation.  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)