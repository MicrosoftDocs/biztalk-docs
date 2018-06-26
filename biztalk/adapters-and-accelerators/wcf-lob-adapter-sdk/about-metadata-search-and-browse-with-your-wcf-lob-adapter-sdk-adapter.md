---
title: "About metadata search and browse with your WCF LOB Adapter SDK adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dc529ba-86ce-4f83-a4f8-73f5765308e2
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# About metadata search and browse with your WCF LOB Adapter SDK adapter
Unlike a static service built using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], adapters built using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] can provide dynamic information about the types and operations available in a line-of-business system. Developers can support the following operations:  
  
- **Metadata Browse**, enabling the user to review a list of all operations and types available in the line-of-business system.  
  
- **Metadata Search**, enabling the user to search for operations using different criteria often based on the line of business system. For example, the user could search on "*CUST\*" to retrieve all operations that have "CUST" anywhere in their name.  
  
- **Metadata Retrieval**, which supplies information about a specific list of supported operations or data types.  
  
  If the line of business system contains hundreds or thousands of operations, providing the ability to search for specific operations or browse certain groups of information can enhance the user experience.  
  
## See Also  
 [Plan and Design your Adapter using the WCF LOB Adapter SDK ](plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk.md)