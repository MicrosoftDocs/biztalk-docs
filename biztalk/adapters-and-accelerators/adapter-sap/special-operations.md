---
title: "Special Operations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "operations, special operations surfaced by the SAP adapter"
ms.assetid: 8725fe63-6ff4-49c8-b386-d4c67e2be440
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Special Operations
The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces several special operations. These operations are not based on SAP system artifacts. They are surfaced to provide functionality for adapter client applications. The special operations are:  
  
- **RfcGetAttributes**. This operation is surfaced under the RFC node and exposes functionality of the RFC SDK. It provides the following information about the RFC connection:  
  
  - The system ID  
  
  - The partner code page  
  
  - The language  
  
    For more information about the RfcGetAttributes operation including its message schema, see [Message Schemas for RFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).  
  
- **RfcConfirmTransID**. This operation is surfaced under the TRFC node and exposes RFC SDK functionality. You use this operation to confirm SAP transaction IDs on the SAP system.  
  
   For more information about how to use the RfcConfirmTransID operation and about its message schema, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).  
  
- **string SapAdapterUtilities.ConvertGuidToTid(Guid)**. This is a public method exposed by the SAP adapter assembly. (It is not an operation surfaced by the adapter.) It returns the SAP transaction ID (TID) mapped to the specified GUID.  
  
   Internally, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] maps the SAP transaction ID (TID) that identifies a logical unit of work (LUW) on the SAP system to a GUID. This GUID is exposed to adapter clients, so that they can commit a tRFC (LUW) by invoking the RfcConfirmTransID operation to confirm its TID on the SAP system.  
  
   However, for some scenarios, you may need the TID that is associated with a tRFC. For example, you may want to identify the LUW on the SAP system to troubleshoot an issue. For these scenarios you can call **ConvertGuidToTid**. To use **ConvertGuidToTid** in your code, you must add a reference to the SAP adapter assembly to your project.  
  
   For more information about invoking tRFCs, see [Operations on tRFCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md). The following example shows how to invoke **ConvertGuidToTid**.  
  
  ```  
  // messageGuid is the GUID associated with a tRFC or IDOC  
  
  string tid = SapAdapterUtilities.ConvertGuidToTid(messageGuid);  
  ```  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)