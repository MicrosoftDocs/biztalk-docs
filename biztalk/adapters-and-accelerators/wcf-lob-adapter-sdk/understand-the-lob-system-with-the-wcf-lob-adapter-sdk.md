---
title: "Understand the LOB system with the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0f97846-5ef2-4530-853a-fba5469156f7
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Understand the LOB system with the WCF LOB Adapter SDK
Before developing your adapter using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], you must have a thorough understanding of the target line-of-business system. If you do not understand the functionality provided by the line-of-business system, how it is exposed, and the different level of support provided for security, transactions, and other features, your adapter may not provide the features required by adapter consumers. This section describes the areas you must understand to effectively design your adapter.  
  
## The Path to Understanding  
 The purpose of an adapter is to expose data and operations from a line-of-business system in a consistent, accessible manner according to the rules imposed by the adapter specification and/or adapter API. To know which operations and data to expose, you must understand what the system does and how it exposes its data and operations. In particular, you must think about the following design issues:  
  
- **Connection lifecycle.** How are connections opened and closed? How are open connections maintained? Are there special requirements for reusing a connection? For more information about connections, see `Microsoft.ServiceModel.Channels.Common.IConnection`.  
  
- **The operation and type metadata exposed by the system.** Does the line-of-business system support operation search and browse and easy access to metadata, or must you develop support code to provide this functionality? For example, in SQL Server operations are objects such as stored procedures. Type metadata about columns, tables, and other objects are easy to retrieve. Legacy line-of-business systems may be more difficult to work with.  
  
- **How operations and data are exposed by the system.** How is the API exposed? Does the API support blocking (synchronous) and non-blocking (asynchronous) calls? Are callbacks supported? Will you interface at the API or protocol level?  
  
- **Support for security, transactions, and reliable messaging.** If the API supports any of these features, you likely want to expose them to the adapter consumer. For example, SQL Server has security and transaction support although reliable messaging isn't practical (but would be with MSMQ or some other queuing system).  
  
- **What functionality and usage scenarios are important?** Don't limit your understanding to the purely technical; discuss and capture business requirements with experienced users. Are there any unique constraints imposed on some operations? Are there operations that are obscure yet useful? Is some functionality rarely used?  
  
  To discover this information, you should consult the user and technical documentation for the target line-of-business system. If the documentation is sparse or missing, you may also be able to learn about the technical aspects of the system by looking for online support forums, online newsgroups, blogs, or by examining the installation files for implementation details. If you have access to the line-of-business developers or code files, you may be able to discover the information you need including connection semantics, support for security, and how operations are searched and invoked.  
  
## See Also  
 [Plan and design your adapter using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk.md)   
 [Get started with the with the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/get-started-with-the-with-the-wcf-lob-adapter-sdk.md)   
 [Selecting the Appropriate Framework](https://msdn.microsoft.com/library/bb798089.aspx)