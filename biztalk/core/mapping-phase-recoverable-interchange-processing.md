---
description: "Learn more about: Mapping Phase (Recoverable Interchange Processing)"
title: "Mapping Phase (Recoverable Interchange Processing)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Mapping Phase (Recoverable Interchange Processing)
By default, when a message in an interchange fails at the mapping phase of a receive port, the entire interchange is suspended. You can change this behavior by adding a property named **BTS.SuspendMessageOnMappingFailure** to the message context, and by setting the value of the context property to `True` from a pipeline component. When this property is set to `True`, the end point manager places the message that failed during mapping in the suspended queue and continues to process remaining messages in the interchange.  
  
 The following code sets the value of the **SuspendMessageOnMappingFailure** property to True.  
  
```  
  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
    bool bSuspend = true;  
    inmsg.Context.Write("SuspendMessageOnMappingFailure", "http://schemas.microsoft.com/BizTalk/2003/system-properties", bSuspend);   
    …  
}  
  
```
