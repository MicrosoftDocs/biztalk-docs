---
title: "How to Add Constant Values | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f46bf66e-caf2-4352-930f-c3c43a5717c3
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Add Constant Values
When testing maps, you will sometimes want to set constant values for use during the test.  
  
## Set constant values for nodes in the source or destination schema trees  
  
1. Select a record or field in the source or destination schema trees.  
  
2. In the Properties window, in the **General** category, use the **Value** property to enter a value for the selected record or field.  
  
   > [!NOTE]
   >  You can only associate a value with a record with its **Content** property set to **Text Only** or **Mixed**.  
  
   For a node in source schema, if you set the **Value** property to **\<empty\>**, the generated instance message for the source schema contains an empty value for the respective node.  
  
   Sometimes, you do not use all the fields in the target schema, i.e. some of the fields in the target schema do not have any incoming links. In such cases, the Test Map operation throws error, provided that the **Validate TestMap Input** or **Validate TestMap Output** properties are set to **True**. To avoid Test Map errors in such cases, set the **Value** property of the node to either a constant value or **\<empty\>**. Use **\<empty\>** if you do not want to set arbitrary data for unused target schema fields.  
  
## See Also  
[Validate and test your maps](../core/how-to-configure-map-validation-and-test-parameters.md)