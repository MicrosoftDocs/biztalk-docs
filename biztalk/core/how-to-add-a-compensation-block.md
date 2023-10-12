---
description: "Learn more about: How to Add a Compensation Block"
title: "How to Add a Compensation Block"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Add a Compensation Block
If you do not add your own compensation, the runtime engine performs a default compensation that invokes the compensations of any nested transactions within the current transaction. It first invokes the compensation of the most recently completed transaction, and works backward until all nested transactions have been compensated.  
  
 This holds true even when your compensation takes place inside a Loop shape: the compensations will be run in reverse order. First, the compensation for the last iteration of the loop will be invoked, then the compensation for the previous iteration, and so on.  
  
> [!CAUTION]
>  Because data is persisted to physical memory for compensation to work, using compensations inside a loop might affect performance, which might be an issue given a large number of iterations.  
  
 If the default ordering does not fit your requirements, you can write your own compensation handler to explicitly call the compensation handlers of the nested scopes in the order you specify.  
  
### To add a Compensation Block  
  
1.  Right-click the **Scope** shape for the transaction to which you want to add a **Compensation Block**, and then click **New Compensation Block**.  
  
    > [!NOTE]
    >  To add a **Compensation Block** to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to **Atomic** or **Long Running**.  
  
     A **Compensation Block** is added to the orchestration immediately following the associated **Scope** shape.  
  
2.  Inside the **Compensation Block** shape, add shapes to create the process for undoing a committed transaction.
