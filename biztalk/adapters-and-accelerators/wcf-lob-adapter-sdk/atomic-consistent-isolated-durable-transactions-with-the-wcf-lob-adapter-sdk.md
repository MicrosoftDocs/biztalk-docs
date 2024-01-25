---
description: "Learn more about: Configure atomic, consistent, isolated, and durable transactions using the WCF LOB Adapter SDK"
title: "Configure atomic, consistent, isolated, and durable transactions using the WCF LOB Adapter SDK"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Configure atomic, consistent, isolated, and durable transactions using the WCF LOB Adapter SDK
The [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] supports transactions by relying on functionality exposed by the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]. By using the API exposed by [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], your adapter can support transactions and operations that are:  
  
- **Atomic**, ensuring that either all pending updates are committed or none are committed and are rolled back to their previous state.  
  
- **Consistent**, ensuring that changes made are from one consistent state to another.  
  
- **Isolated**, preventing a transaction to access uncommitted changes in other pending transactions.  
  
- **Durable**, meaning that once committed, updates will be persistent in the face of failures.  
  
  Adapter developers targeting relational database systems or other line-of-business systems that support (or expect) transactions will need to identify how the target system supports and exposes transaction support and then identify an appropriate [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] transaction model to use.  
  
  For more information about [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] transactions, see [Windows Communication Foundation Transactions Overview](/dotnet/framework/wcf/feature-details/transactions-overview). 
  
## See Also  
 [Plan and Design your Adapter using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk.md)