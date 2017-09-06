---
title: "Interceptor BamActivity Element | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dee61b4-83cd-4a22-b8a6-1c1a7ea3648b
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Interceptor BamActivity Element
The **BamActivity** element defines a single BAM activity.  
  
## Format  
 The `BamActivity` element includes a **Name** attribute and contains one or more `OnEvent` elements.  
  
```  
<ic:BamActivity Name="PurchaseOrder">  
  <!-- One or more OnEvent elements -->  
</ic:BamActivity>   
```  
  
### Attributes  
  
|Attribute name|Description|  
|--------------------|-----------------|  
|Name|User-defined name of the BAM activity.|  
  
## Example  
 The following example contains a sample BamActivity for "MyOrderWorkflow" with a single OnEvent.  
  
```  
<ic:BamActivity Name="MyOrderWorkflow">  
  <ic:OnEvent Name="MyActivityEvent"  Source="OrderWorkflow">  
    …  
  </ic:OnEvent>  
</ic:BamActivity>  
```  
  
## See Also  
 [Interceptor EventSource Element](../core/interceptor-eventsource-element.md)   
 [Interceptor OnEvent Element](../core/interceptor-onevent-element.md)