---
title: "Ops Adapter Implementation Details | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "batching, Ops adapters"
  - "Ops adapters, batching"
  - "Ops adapters, creating ports"
  - "Ops adapters, implementing"
  - "Ops adapters, transaction handling"
  - "process management solution tutorial, Ops adapters"
ms.assetid: dbca31ca-c3d8-4a25-9356-ef4bbab671e1
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Ops Adapter Implementation Details
You may find it useful to understand the following aspects of the Ops adapter when modifying the adapter or configuring it programmatically.  
  
> [!NOTE]
>  The Ops Adapter is built using the Adapter Framework. For information about building adapters with the framework, see [Developing Custom Adapters](../core/developing-custom-adapters.md).  
  
## Batch Processing  
 The adapter processes one message at a time so that each message is processed separately, and rollback operations are done on only one order at a time. Although the adapter processes one message at a time, it does so using batching with a batch size of one. This makes it easier to modify the adapter to handle messages in batches.  
  
## Transaction Handling  
 The adapter uses the transaction facilities provided by the Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]**System.Transactions** facilities. The adapter creates a new **CommittableTransaction** and uses it with a **TransactionScope**. The adapter calls the **Initialize** and **Execute** methods within the context of this transaction. Code in the called assembly can participate in the transaction by using **Transaction.Current** static method to get the transaction context. The sample error handler does not make use of this facility. For more information about **System.Transactions**, see "System.Transactions Namespace" in the .NET Framework Class Library version.  
  
## Handling Data Other Than Error Reports  
 In the solution, the adapter handles error report messages from the new error reporting feature. However, because the **Execute** method takes a byte array as its only argument, there is nothing that specifically limits what can be passed to the **Execute** method.  
  
## Using the Adapter When Creating Ports Programmatically  
 You can specify the adapter when creating ports from code. The following table shows the custom property names and how they correspond to the display names.  
  
|Send Custom Property Name|Display Name|  
|-------------------------------|------------------|  
|**DotNetAssemblyStrongName**|**DotNetAssemblyStrongName**|  
|**DotNetClassName**|**DotNetClassName**|  
|**InitializationData**|**InitializationData**|  
|**TransportLocationUri**|Not applicable.|  
  
 All of the properties are string values. You construct the value of the TransportLocationUri property from the assembly name and the class name. The URI has the value OPS://\<DotNetAssemblyStrongName>/\<DotNetClassName> where the placeholders are replaced by the values of the corresponding custom property.  
  
 For information about creating ports from code, see [How to Create MSMQ Receive Locations and Send Ports from Code](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md).  
  
## See Also  
 [The Ops Adapter](../core/the-ops-adapter.md)