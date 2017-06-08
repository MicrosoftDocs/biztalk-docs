---
title: "Transform Shape | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.orch.shape.transform"
ms.assetid: 0bf78389-597f-437c-a893-88ec99147f55
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Transform Shape
You can use the **Transform**shape to move data from one message into another. You specify one or more input messages, one or more output messages, and an XSLT map for the transform. The map assigns message parts from the input messages to message parts in the output messages. You only use transforms in the construction of messages, so your Transform shape always appears inside a Construct Message shape.  
  
> [!NOTE]
>  Any source or destination messages in a Transform must be based on a schema.  
  
|Use this|To do this|  
|--------------|----------------|  
|**Input Messages** property|Specify which messages will be the source of the data.|  
|**Map Name** property|Specify the name of the XSLT map that will do the transformation.|  
|**Output Messages** property|Specify which messages will be the destination of the data.|  
|**Report to Analyst** property|Select **True** if you want to make this shape viewable in the Visual Business Analyst Tool.|  
  
## See Also  
 [How to Configure the Transform Shape](../core/how-to-configure-the-transform-shape.md)