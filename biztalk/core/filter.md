---
title: "Filter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8dad59d-4a47-4794-bbf9-cba02fe7f0bf
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Filter
The `Filter` element contains an `Expression` that evaluates to `true` or `false` and determines when an event should be processed or skipped.  
  
## Format  
  
```  
<ic:Filter>  
</ic:Filter>  
```  
  
## Remarks  
  
## Example  
 The following example defines a filter that evaluates to `true` when the user key for the workflow associated with the event equals "DocumentUrl":  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>DocumentUrl</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## See Also  
 [Interceptor OnEvent Element](../core/interceptor-onevent-element.md)