---
description: "Learn more about: How to Configure the Scope Shape"
title: "How to Configure the Scope Shape"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure the Scope Shape
The **Scope** shape provides a contextual framework for its contents. The first block of a **Scope** shape is the context block, or body, in which the basic actions of the scope take place; it is analogous to the try block in a try/catch statement. Following the body, the **Scope** shape may also include one or more exception-handler blocks and a compensation block.  
  
> [!NOTE]
>  In a multiple machine environment where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server are located on different machines, if the Coordinated Universal Time (UTC) is different on the two machines then the **Timeout** property you configure for the **Scope** shape may get triggered earlier than expected because of the UTC time on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server machines is unsynchronized. Note that this is not a time zones issue as Coordinated Universal Time is unaffected by time zones.  
  
### To configure a Scope shape as a transaction boundary  
  
1.  In the Properties window, set the **Transaction Type** property to **Atomic** or **Long Running**.  
  
    > [!NOTE]
    >  The orchestration must itself be a long-running transaction in order for you to set the Transaction Type to Atomic or Long Running.  
  
2.  If the **Transaction Type** is set to **Atomic**, then in the Properties window, specify the following properties:  
  
    |Property|Description|  
    |--------------|-----------------|  
    |Batch|Boolean value that determines if this transaction can be batched with other transactions across multiple instances of the orchestration. This property is never used in BizTalk Server because BizTalk Server does not support batching atomic transactions across multiple instances of orchestrations. This property will be deprecated in the future release.|  
    |Isolation Level|Determines the degree to which data is accessible among concurrent transactions:<br /><br /> -   Read Committed—To prevent the selected transaction from accessing data modifications in concurrent transactions until they are committed. This option is the Microsoft SQL Server default setting.<br />-   Repeatable Read—To require read locks until the selected transaction is complete.<br />-   Serializable—To prevent concurrent transactions from making data modifications until the selected transaction is complete. This option is the most restrictive isolation level.|  
    |Retry|Boolean value that determines whether this transaction is retried when an error occurs. The default value is **True**. **Note:**  An atomic transaction will be retried if you throw Microsoft.XLANG.BaseTypes.RetryTransactionException, or if the orchestration engine is unable to store its state or commit the transaction.|  
    |Timeout|Determines the time in seconds until the transaction fails due to inactivity. If you do not want to use a timeout, set the value of this property to 0. **Note:**  This is a DTC timeout, and is not enforced by the orchestration engine. For atomic transactions only, the engine will not interrupt the transaction. It proceeds normally until commitment, at which point it fails to commit only if participating in a DTC transaction through one of the objects inside it.|  
  
3.  If the **Transaction Type** is set to **Long Running**, then in the Properties window, specify the following property:  
  
    |Property|Description|  
    |--------------|-----------------|  
    |Timeout|Determines the time in seconds until the transaction times out and is considered a failed transaction. If you do not want to use a timeout, set the value of this property to 0.|  
  
### To configure a Scope shape to contain local variables  
  
1.  Double-click the scope in the Orchestration View window.  
  
2.  Right-click the Variables folder under the scope and then click **New Variable**.  
  
3.  Proceed from step 2 in "To add a variable" in [How to Add Orchestration Variables](../core/how-to-add-orchestration-variables.md).
