---
description: "Learn more about: How to Use Expressions to Dynamic Transform Messages"
title: "How to Use Expressions to Dynamic Transform Messages"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Use Expressions to Dynamic Transform Messages
You can use expressions to dynamic transform messages in your orchestration. XLANG exposes a transform method that can be called from within a **Message Assignment** shape inside of a **Construct Message** shape. This is the same method that is called when a **Transform** shape is used, but allows you to programmatically transform the messages using the map you designated within the orchestration. This is useful when you are doing type-agnostic message processing. For example, if you have a business process that needs to choose from a series of maps to transform inbound messages based on the parameters provided by the received inbound messages, you can achieve this by using the transform method in the Expression shape while maintaining your overall business process intact.  
  
## Transforming messages  
 You can use the following sample code to programmatically transform the messages in the **Message Assignment** shape:  
  
```  
MyMapType = typeof(MyMapName);  
transform(MyOutputMsg) = MyMapType(MyInputMsg);  
```  
  
 In this example, MyMapType is declared as a variable of type **System.Type** in the orchestration. MyMapName is the name of a map that was already created in your BizTalk project. If you would like to reference a map that is in a separate BizTalk assembly, you will need to reference that assembly in your BizTalk project. MyInputMsg is the source message and MyOutputMsg is the destination message. If your map takes multiple source messages, then you can use the following sample code to transform the messages:  
  
```  
MyMapType = typeof(MyMapName);  
transform(MyOutputMsg) = MyMapType(MyInputMsg1, MyInputMsg2);  
```  
  
> [!NOTE]
>  If you have multiple source messages, they must be placed in order in the expression with respect to the input message part number indicated in the map.  
  
> [!IMPORTANT]
>  When dynamic transforming messages in the Expression shape, we recommend that you write a cache in user code for caching the compiled maps, and then use the cache in the Expression shape to retrieve the maps before performing the message transformation. If you are not caching the maps, it is possible to see Common Language Runtime (CLR) memory grow significantly. Dynamic mapping requires that the .NET Runtime perform code access check which results in a .NET Evidence object being placed in the Large Object Heap for each transformation and this object is not disposed of until the orchestration completes. Therefore, when there are a lot of these types of transforms occurring simultaneously, you may see the memory usage increase substantially which can also lead to the out of memory exception.  
  
## See Also  
 [Orchestration Shapes](../core/orchestration-shapes.md)   
 [Creating Maps Using BizTalk Mapper](../core/creating-maps-using-biztalk-mapper.md)
