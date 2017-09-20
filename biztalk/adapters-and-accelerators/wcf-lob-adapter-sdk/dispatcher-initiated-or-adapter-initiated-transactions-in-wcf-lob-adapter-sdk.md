---
title: "Configure dispatcher-initiated or adapter-initiated transactions with the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 85b9ef8d-3922-4838-a41a-32db5e005dc0
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure dispatcher-initiated or adapter-initiated transactions with the WCF LOB Adapter SDK
## Inbound Transactions  
 There are two methods of implementing transactions with inbound operations: dispatcher-initiated or adapter-initiated. The requirements of the adapter dictate which method should be used. The value of the `SupportsTransactedInbound` property indicates which type of transaction your adapter will implement.  
  
 The following table compares dispatcher-initiated with adapter-initiated transactions.  
  
|SupportsTransactedInbound|Transactional Behavior|  
|-------------------------------|----------------------------|  
|True (dispatcher-initiated)|-   TryReceive will always be called within the context of a transaction.<br />-   The transaction will be committed after the message is returned to the service implementation.<br />-   A new transaction will be created for each IInputChannel.Receive call. Spanning a transaction across multiple receives is dependent on the service host and not the adapter developer. **Note:**  If the host is not using the WCF dispatcher (service host) and is instead using channel level programming, the host should honor the **TransactedReceiveEnabled** property of the WCF binding, and should make all calls to IInputChannel.Receive within a transaction. **Note:**  If the adapter uses dispatcher-initiated transactions, and is used with Biztalk Server, set the `SupportedInboundChannels` property to `SupportedInboundChannels.IInputChannel` to indicate that the adapter only supports one-way channels. If this is not set, BizTalk Server will attempt to use two-way channels.|  
|False (adapter-initiated)|-   The adapter developer must implement transaction logic within the adapter.<br />-   Adapter-initiated transactions can only work with a two-way messaging (Reply Channel) model.<br />-   One transaction can span multiple messages, since dependent clones will be created for each message by the dispatcher.|  
  
### Dispatcher-initiated Transactions  
 When SupportsTransactedInbound is set to **true**, the WCF dispatcher will then automatically create a transaction when calling the **TryReceive** method of the adapter, and will commit the transaction after the message is returned to the service implementation. This does not require any specific transactional code implementation within the adapter other than setting the `SupportsTransactedInbound` property to **true**. However, this is dependent on the adapter being hosted within a service host that uses the WCF dispatcher, and will not occur if you are using channel level programming. When using channel level programming, the host should honor the `TransactedReceiveEnabled` property of the WCF binding and make all calls to Receive within a transaction.  
  
 The following demonstrates a client creating a transaction, and then calling the adapter using channel level programming.  
  
```csharp  
Message message;  
//Use a new TransactionScope  
using (System.Transactions.TransactionScope tx = new System.Transactions.TransactionScope())  
{  
    message = channel.Receive(TimeSpan.FromMinutes(2));  
    tx.Complete();  
}  
```  
  
### Adapter-initiated Transactions  
 When hte `SupportsTransactedInbound` property is set to **false**, transaction support must be implemented within the adapter code by creating a new transaction. Before returning a message from **TryReceive**, the transaction must be attached to the message by calling the **Set** method of the **TransactionMessageProperty** class. This implementation requires explicit transaction support in the adapter code, and provides greater control over the transactional behavior of the adapter.  
  
 The following demonstrates creating a dependent transaction, and attaching this to the message before it is returned to the client.  
  
```csharp  
  
Transaction transaction = inboundConnection.CurrentTransaction; //Existing transaction  
DependentTransaction dt = transaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
TransactionMessageProperty.Set(dt, message);  
inboundReply.DependentTransaction = dt; //this will later be closed during Reply processing  
```  
  
## See Also  
 [Development Activities](../../esb-toolkit/development-activities.md)