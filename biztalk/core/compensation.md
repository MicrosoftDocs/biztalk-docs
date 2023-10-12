---
description: "Learn more about: Compensation"
title: "Compensation"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Compensation
If an error occurs and you need to undo or reverse the effects of a successfully committed transaction, you can do so by adding compensation code to your orchestration.  
  
 The compensation can be invoked after the transaction has completed its actions successfully. At that point, the state of the orchestration is known, and state information is available to the code in the compensation, which means that you can write code to act appropriately depending on the state of the orchestration when the transaction commits.  
  
 Compensations can also be provided on atomic transactions. These compensations can only be called after the atomic transaction commits. You need to write code to undo or reverse the path of the normal execution in the compensation.  
  
 The compensation block is flexible; it can contain any other shape, including another transaction scope.  
  
> [!NOTE]
>  You can do a compensation only once on a given scope.  
  
## In This Section  
  
-   [How to Configure the Compensate Shape](../core/how-to-configure-the-compensate-shape.md)  
  
-   [How to Add Custom Compensation to an Orchestration](../core/how-to-add-custom-compensation-to-an-orchestration.md)  
  
-   [How to Add a Compensation Block](../core/how-to-add-a-compensation-block.md)
