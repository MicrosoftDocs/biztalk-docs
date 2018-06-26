---
title: "Operations on Business Services in Siebel | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "operations, on business services"
  - "business services, operations on"
ms.assetid: 29a1a88c-8c7b-46f1-8faf-49ddd32ba2f0
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Operations on Business Services in Siebel
A Siebel business service is a collection of business methods that can be directly invoked in Siebel. Whereas business components and business objects are associated to specific data and tables in Siebel, business services invoke the objects to perform specific tasks.  
  
 The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces the business service methods as operation names and supports IN, OUT, and INOUT parameters. For example, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] surfaces the **ATPRunCheck** method as an operation. This method belongs to the **ATP** business service.  
  
 Certain conditions that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] imposes while using the Siebel business services:  
  
- If a Siebel business service method takes an argument that does not have the data type specified, the adapter exposes the argument as TEXT.  
  
- A Siebel business service method argument can be of the following types:  
  
  - String (exposed as xsd:string)  
  
  - Number (exposed as xsd: decimal)  
  
  - Date (exposed as xsd:DateTime, with pattern facet indicating that time part must be set to 00:00:00)  
  
  - Hierarchy (exposed as xsd:string)  
  
  - Integration Object (exposed as xsd:string)  
  
    Also, the business service method verifies whether the value passed for an argument complies with the corresponding type. So, if a business service method accepts or returns values that do not comply with the corresponding argument type, the adapter may throw an exception. If the adapter does succeed in invoking the business service method, the schema validation may fail.  
  
  For information about:  
  
- Performing operations on business services using BizTalk Server, see [Invoke Business Service Methods Using BizTalk Server and the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/invoke-business-service-methods-using-biztalk-server-and-the-siebel-adapter.md).  
  
- Message structures and SOAP actions to perform operations on business services, see [Message Schemas for Business Service Operations](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-service-operations.md)).  
  
## See Also  
 [Connect to an SAP system using the adapter](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)