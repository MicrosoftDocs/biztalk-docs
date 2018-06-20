---
title: "Operations on tRFCs in SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RFCs, invoking transactional RFCs in an SAP System"
  - "TID database"
  - "transactional RFCs"
  - "tRFCs, receiving inbound iransactional RFC calls from an SAP system"
  - "tRFCs"
  - "GUID parameter"
  - "RFCs, processing inbound"
  - "RfcConfirmTransID"
  - "transaction ID (TID)"
  - "tRFC Operations"
  - "IDOCS, receiving IDOCs as a tRFC server"
  - "adapters, operations on tRFCs"
  - "RFC, invoking an RFC"
ms.assetid: d6a5c515-d6aa-4b70-9c23-32d1dd94d473
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on tRFCs in SAP
Transactional RFCs (tRFCs) are RFCs that are invoked as part of a logical unit of work (LUW). On an SAP system, an LUW contains all of the steps necessary to complete a business or programming task. A tRFC represents a way of invoking an RFC; it is not a unique SAP artifact.  
  
 You can use the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] both as a tRFC client and as a tRFC server.  
  
-   **As a tRFC client**, the adapter enables your application to invoke a single RFC in an LUW on the SAP system. This guarantees one-time only execution of the RFC. It does not imply transactional behavior.  
  
-   **As a tRFC server**, the adapter enables you to receive multiple RFCs inside an LUW. The adapter supports inbound tRFC calls in a transactional context; that is commit and roll back behavior are supported.  
  
## tRFC Operations  
 A tRFC implies a way of invoking an RFC; it is not a separate SAP artifact. Therefore, every RFC on the SAP system (for which the adapter can retrieve metadata) is also surfaced as a tRFC by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. tRFCs are surfaced by RFC name as operations under the TRFC metadata category node. (You can browse or search for tRFCs under the **TRFC** node when you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].)  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following on tRFCs:  
  
-   IMPORT parameters  
  
-   CHANGING parameters (only the input side of the CHANGING parameter is supported)  
  
> [!NOTE]
>  tRFCs are executed asynchronously, so no output values (EXPORT or CHANGING parameters) are returned for them.  
  
 A GUID parameter is surfaced by the adapter for tRFC operations. This GUID is mapped by the adapter to the SAP transaction ID (TID) that is associated with the tRFC. You can use this GUID parameter to:  
  
- Confirm the tRFC on the SAP system in tRFC client calls. You do this by invoking the RfcConfirmTransId operation. This is a special operation surfaced by the adapter to confirm a TID on the SAP system.  
  
- Get the actual SAP TID used for a tRFC from the adapter in both tRFC client and tRFC server scenarios. You do this by invoking the SAP utility method, ConvertGuidToTid.  
  
  For more information about these operations, see [Special Operations](../../adapters-and-accelerators/adapter-sap/special-operations.md). For more information about the message structures and SOAP actions used for tRFCs by the adapter, see [Message Schemas for tRFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md).  
  
## Invoking Transactional RFCs in an SAP System  
 Typically, tRFCs are used to execute one or more RFC calls inside a single LUW; however, due to limitations in the SAP RFC SDK, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports only a single tRFC per LUW. For this reason, the adapter creates an LUW (SAP TID) for each tRFC. For such clients, SAP defines an LUW as a mechanism to guarantee "one-time" execution of the RFC and does not imply commit and rollback-based transactions.  
  
 The following steps summarize the tasks that are performed in an RFC client call using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Some of these steps are performed by the adapter client, and some are performed by the adapter.  
  
1. The adapter client sends a request message for the tRFC operation. The adapter client can optionally supply a GUID in this message.  
  
2. The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] receives the request message and uses the RFC SDK to get a transaction ID (TID) from the SAP system. If the request message contains a GUID, the adapter maps this GUID to the SAP TID; otherwise, the adapter creates a new GUID and maps it to the SAP TID  
  
3. The adapter uses the TID to make the tRFC call to the SAP server. The status of the TID is marked as **FINISHED** on the SAP system.  
  
4. The adapter returns the GUID (that is mapped to the TID) to the adapter client in the response message.  
  
5. The adapter client invokes the RfcConfirmTransID operation on the adapter with the GUID returned in the previous step.  
  
6. The adapter uses the GUID in the RfcConfirmTransID request message to identify the SAP TID and confirms the tRFC call on the SAP system. This causes the SAP server to delete the TID entry from its database.  
  
> [!NOTE]
>  tRFC client calls do not return EXPORT or CHANGING parameters.  
  
 For more information about:  
  
-   Invoking a tRFC using BizTalk Server, see [Invoke tRFCs in SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md).  
  
-   Invoking a tRFC using the WCF service model, see [Invoke tRFCs in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md).  
  
-   Message structures and SOAP action for invoking a tRFC, see [Message Schemas for tRFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md).  
  
## Receiving Inbound Transactional RFC Calls from an SAP System  
 You can use the adapter as a tRFC server to receive tRFCs from SAP. As a tRFC server, when the adapter receives a tRFC, it invokes the corresponding tRFC operation on your application. The adapter supports the following functionality when it acts as a tRFC server:  
  
- An LUW (identified by a SAP TID) can contain multiple tRFCs (RFC calls).  
  
- The adapter creates a committable transaction for each SAP TID. Your application code can enlist in this transaction.  
  
- Commit and roll back are supported.  
  
  The rest of this section provides general information about using the adapter as a tRFC server. For more specific information about:  
  
- Receiving a inbound tRFC calls using BizTalk Server, see [Receive Inbound tRFC Calls from SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md).  
  
- Receiving a inbound tRFC calls using the WCF service model, see [Receive Inbound tRFC Calls in SAP using the WCF Service Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md).  
  
### The TID Database  
 When it acts as a tRFC server, the adapter uses a SQL Server database—the TID database—to manage the transaction IDs that it receives from the SAP system. For example, it uses the TID database to help manage calls from the SAP system to commit, rollback, and confirm the TID. The adapter also stores the GUID that it creates and associates with each SAP TID in the TID database.  
  
### Prerequisites  
 For the adapter to perform as a tRFC server, you must ensure that the following are true:  
  
- The RFC must be declared on the SAP system. This is so the adapter can retrieve metadata that describes the RFC from the SAP system. The RFC is actually implemented in your application.  
  
- The adapter must register with an RFC destination on an SAP gateway. The registration is based on a logical name called a program ID. You supply parameters in the connection URI to specify the program ID, SAP gateway, and SAP server for this registration.  
  
- The TID database must be created in SQL Server. To do this, you must run a SQL script that is installed by the setup. The SQL script is typically installed at \<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. For more information see, [Installing the BizTalk Adapter Pack](http://msdn.microsoft.com/library/2ae27db5-b11b-42c3-a568-e2331badf80e).  
  
- The **TidDatabaseConnectionString** binding property must be set to the SQL database connection string for the TID database. For more information about the **TidDatabaseConnectionString** binding property, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
> [!NOTE]
>  Setting the **TidDatabaseConnectionString** binding property configures the adapter to act as a tRFC server rather than as an RFC server. If the **TidDatabaseConnectionString** binding property is set and you specify an RFC destination in the connection URI, the adapter acts as a tRFC server for incoming calls from the RFC destination. If this binding property is not set, the adapter acts as an RFC server.  
  
### How the Adapter Processes Inbound tRFCs  
 The following steps summarize the tasks that are performed by the RFC client call using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Some of these steps are performed by the adapter client, and some are performed by the adapter.  
  
1.  The SAP system calls into the adapter to enquire whether a TID has already been used. The adapter returns the appropriate response to the SAP system. If the TID is new, the adapter creates a committable transaction. This transaction is used to persist the TID to the TID database in a transactional manner when the SAP program performs a commit (COMMIT WORK). It is also exposed to application code that handles the inbound tRFCs. Additionally, the adapter creates a GUID that it associates with the SAP TID.  
  
2.  The SAP system sends one or more transactional RFCs to the adapter. For each tRFC, the adapter invokes the appropriate tRFC operation on your application. The adapter flows the transaction created in step 1 to your application for each operation. The adapter passes the GUID created in step 1 in the request message for the operation.  
  
3.  SAP system commits the LUW (COMMIT WORK). The adapter tries to commit the transaction associated with the SAP TID (created in step 1).  
  
    1.  If the transaction was aborted (by your application) during any of the calls in step 2, then an error occurs when the adapter tries to commit the transaction. The error is returned to SAP. Go to step 4.  
  
    2.  If the commit is successful, the TID is now in the TID database. Go to step 5.  
  
4.  If an error occurred in step 3, or if SAP rolls back the LUW (RESTART_OF_BACKGROUNDTASK) instead of committing it, the adapter rolls back the transaction. In this case the TID is never persisted to the TID database.  
  
5.  The SAP system confirms the TID. The adapter removes the TID from the TID database (assuming that step 3 completed successfully and the TID exists in the TID database.  
  
> [!NOTE]
>  If an error occurs attempting to connect to the TID Database during a tRFC server operation, an error code indicating that the incoming call from SAP was not processed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is returned to SAP.  
  
### Receiving IDOCs as a tRFC server  
 You use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] as either an RFC server or a tRFC server to receive IDOCs from the SAP system. In either case, you must set the **ReceiveIdocFormat** binding property to specify the format in which the adapter should emit the IDOC data to your application. For more information about receiving IDOCs with the adapter, see [Operations on IDOCs in SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md). For more information about the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
## Special tRFC Operations  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] can also perform certain special tRFC operations on the SAP system. One such operation is RfcConfirmTransID.  
  
- **RfcConfirmTransID.** You invoke this operation on the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] to confirm tRFC calls made to the SAP server. RfcConfirmTransID might be required in scenarios where the adapter is used to send IDOCs to the SAP server as a tRFC. The operation is available under the **TRFC** node when using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
  For more information about the message structure and SOAP action for the RfcConfirmTransID operation, see [Message Schemas for tRFC Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md).  
  
## See Also  
 [Connect to an SAP system using the adapter](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)