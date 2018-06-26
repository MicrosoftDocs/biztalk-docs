---
title: "Operations on BAPIs in SAP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BAPI, operations"
  - "BAPIs, operations on"
  - "Business Application Programming Interface"
  - "BAPIs"
  - "BAPI, transactions"
  - "BAPI transactions, limitations on"
ms.assetid: 6be26641-e8d3-4e11-8d82-4fdb13076580
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on BAPIs in SAP
A Business Application Programming Interface (BAPI) is a method of a SAP business object that can be called by an external process. BAPIs are transactional on the SAP system.  
  
 The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] supports BAPI calls in the outbound direction. It surfaces BAPIs in two ways:  
  
- **As an RFC**. You can invoke a BAPI directly by invoking the appropriate RFC.  
  
- **As methods of business objects**. The adapter surfaces BAPIs as methods of business objects as a convenience to help you retrieve metadata when you use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].  
  
> [!IMPORTANT]
>  You can invoke a BAPI on the adapter as an RFC or as a method of a business object; but regardless of how you invoke the BAPI on the adapter, it always invokes the BAPI on SAP through the RFC interface.  
  
 The adapter supports BAPI transactions. The BAPI transaction model on SAP enables users to combine several BAPIs into one logical unit of work (LUW). An SAP LUW consists of all the steps involved in a transaction including updating the database.  
  
 The topics in this section explain how BAPIs are surfaced as business objects and how BAPI transactions (LUWs) are supported by the adapter.  
 
  
## BAPI Operations (as Business Object Methods)  
 The adapter surfaces BAPIs as business objects methods as a convenience to help you retrieve metadata when you use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] or the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. The adapter always invokes BAPIs on the SAP system using the RFC interface.  
  
 The adapter surfaces BAPIs by name as operations under the appropriate business object for outbound operations. Business objects are collected by functional group under the BAPI category node by the adapter. (You can browse or search for business objects and BAPIs under the **BAPI** node when you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] or the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].)  
  
 The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following on BAPIs:  
  
- IMPORT parameters  
  
- EXPORT parameters  
  
- CHANGING parameters  
  
- Table parameters  
  
  For more information about the message structures and SOAP actions used for BAPIs surfaced as business object methods, see [Message Schemas for BAPI Operations](../../adapters-and-accelerators/adapter-sap/message-schemas-for-bapi-operations.md).  
  
## BAPI Transactions  
 When you invoke a BAPI, it is always part of an LUW on the SAP system. This is true whether you invoke the BAPI as an RFC or as a method of a business object. The RFC SDK treats all BAPIs sent over the same SAP connection as part of the same LUW. After a call to commit or roll back the transaction on a connection, the next BAPI sent over the connection begins a new LUW.  
  
 You call BAPI_TRANSACTION_COMMIT or BAPI_TRANSACTION_ROLLBACK to commit or roll back the transaction. The adapter surfaces these two BAPIs:  
  
- Under the Basis node as RFC operations.  
  
- Under each business object.  
  
  You control the BAPIs in a transaction by ensuring that they are all sent over the same SAP connection (including the call to commit or roll back the transaction). You can do this in:  
  
- BizTalk Solutions by using the **ConnectionState** message context property to ensure that the BAPIs in a transaction are sent using the same connection. This property is surfaced by the adapter and provides you with explicit control over the connection used to send a message in a BizTalk orchestration.  
  
   For performing BAPI transactions using BizTalk Server, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following message context properties.  
  
  |Field|Description|  
  |-----------|-----------------|  
  |OPEN|Opens a new channel for the transaction.|  
  |REUSE|Reuse existing channel for the transaction.|  
  |CLOSE|Commit the transaction and close the existing channel.|  
  |ABORT|Abort the transaction and close the existing channel.|  
  
   For more information, see [Run BAPI Transactions in SAP using BizTalk Server](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md).  
  
  > [!NOTE]
  >  Make sure you set the **EnableBizTalkCompatibilityMode**binding property when performing transactions using BizTalk Server.  
  
- WCF service model solutions by ensuring that the BAPIs in a transaction are sent using the same WCF client. For more information, see [Invoke BAPIs in SAP using WCF Service Model](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md).  
  
- WCF channel model solutions by ensuring that the BAPIs in a transaction are sent over the same WCF channel. For more information, see [Develop applications using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md).  
  
### Limitations on BAPI Transactions  
 The following restrictions apply on BAPI transactions:  
  
- It is not possible to make two write accesses on the same instance within one LUW. For example, you cannot create an order and update it in the same transaction.  
  
- When performing BAPI a transaction using [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], all the messages must be sent over a single host instance of the send port.  
  
- If an instance is created, updated, or deleted by using a write BAPI, a read BAPI cannot view the most recent data until the write BAPI is committed.  
  
- An external client that invokes an LUW should call all the BAPIs that the LUW contains on the same SAP connection.  
  
> [!IMPORTANT]
>  BAPIs that belong to Release 3.1 call COMMIT WORK as part of their implementation. This means that these BAPIs cannot be included with other BAPIs in an LUW (because they will commit the transaction). For more information, see the SAP documentation.  
  
## See Also  
 [What Operations Can be Performed Using the Adapter?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)