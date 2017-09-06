---
title: "Interceptor EventSource Element | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d78846c1-3984-43af-a13f-9d5c0a66d3b5
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Interceptor EventSource Element
The **EventSource** element provides information about the source of one or more of the events appearing in the interceptor configuration file. In addition to an event source name, you need to indicate the technology and a manifest for the source.  
  
## Format  
 The `EventSource` element has three attributes and may or may not have child elements depending upon which schemas are included. For example, the WCF schema WcfInterceptorConfiguration.xsd provides for the `NamespaceMapping` element.  
  
### Attributes  
  
|Attribute name|Description|  
|--------------------|-----------------|  
|Name|Name for this event source. This name is used by **OnEvent** entries to refer to the source.|  
|Technology|Technology type hosting the event source indicated in the manifest. Use "WF" for Windows Workflow Foundation and "WCF" for Windows Communication Framework.|  
|Manifest|Assembly-qualified class name of the type to use as an event source. For example, `TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08`<br /><br /> If you do not have a public key token, use `PublicKeyToken=null`.|  
  
## Example  
 The following example contains two **EventSource** elements, one targeting WF and one targeting WCF.  
  
```  
<!-- WF -->  
<ic:EventSource Name="OrderWorkflow" Technology="WF" Manifest="SimpleWorkflow.OrderWorkflow, SimpleWorkflow, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
<!-- WCF -->  
<ic:EventSource Name="PurchaseService" Technology="WCF" Manifest="Service.IProcessPOContract, DuplexService, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
```