---
description: "Learn more about: How to Configure the Compensate Shape"
title: "How to Configure the Compensate Shape"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure the Compensate Shape
If you are using nested transactions in your orchestration, you can add a **Compensate** shape in the compensation block or an exception block of a transaction scope. This enables your orchestration to explicitly perform compensation on a nested transaction. You specify which transaction you would like to be compensated in the **Compensate** shape, and any compensation code in the nested transaction will be run, provided the transaction committed successfully.  
  
> [!NOTE]
>  The **Compensation** property refers to the unique identifier of the transaction scope; it does not refer to the name of the scope.  
  
 If you want to compensate more than one nested transaction, you add an additional **Compensate** shape for each transaction.  
  
 No **Compensate** shape is necessary if there is no other compensation code in an outer transaction; the compensation code of any nested transactions will be run automatically. The **Compensate** shape gives you control over the process by allowing you to decide whether or not you want a nested transaction to be compensated.  
  
### To configure a Compensate shape  
  
-   In the Properties window, select the compensation block to call from the **Compensation** drop-down list.  
  
     The drop-down list will display all of the transactions which can be compensated, which includes the current transaction and any immediate child transactions of the current transaction. If you cannot see a transaction that you expect, it might be due to the relationship of the transactions.  
  
    > [!NOTE]
    >  You cannot compensate the current transaction from within the body of the transaction.  You can compensate it from the compensation block or an exception block of the transaction.  
  
     If you choose to compensate the current transaction, that means that the default handler will be invoked, and not an explicit compensation block (if there is one). This is a mechanism for automatically compensating directly nested transactions that have completed successfully.
