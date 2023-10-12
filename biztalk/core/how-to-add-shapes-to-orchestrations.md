---
description: "Learn more about: How to Add Shapes to Orchestrations"
title: "How to Add Shapes to Orchestrations"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Add Shapes to Orchestrations
This section describes the procedures for adding and removing shapes in your orchestration. For more information about the available shapes, see [Orchestration Shapes](../core/orchestration-shapes.md).  
  
### To add a shape to an orchestration  
  
1.  In the Toolbox, on the **BizTalk Orchestrations** tab, drag the shape onto a connecting line on the Orchestration Design Surface.  
  
     —Or—  
  
2.  Right-click the connecting line or the shape placeholder where you want to add the shape, point to **Insert Shape**, and then click the shape name you want to add.  
  
    > [!NOTE]
    >  A Smart Tag appears on shapes that are not yet fully configured.  
  
> [!NOTE]
>  **Transform** shapes and **Message Assignment** shapes can only exist within a **Construct Message** shape. If you add one of these shapes to your orchestration outside of a **Construct Message** shape, it is placed automatically inside a new **Construct Message** shape.  
  
> [!NOTE]
>  **Catch Exception** and **Compensation** blocks can only exist following a **Scope** shape.  
  
### To remove a shape from an orchestration  
  
1.  Right-click the shape on the design surface, and then click **Delete**.  
  
     —Or—  
  
2.  Select the shape and press the **DELETE** key.  
  
## See Also  
 [Creating Orchestrations](../core/creating-orchestrations.md)
