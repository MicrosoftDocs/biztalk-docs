---
description: "Learn more about: How the Remove Namespace Sample Works"
title: "How the Remove Namespace Sample Works"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How the Remove Namespace Sample Works
The second and third tests use the **Remove Namespace** component located in the **NamespaceSampleSendPipeline** pipeline. It takes as input a document with a namespace on the root node, such as the following:  
  
```  
<ns0:CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1"   
    Status="Status_2"   
    xmlns:ns0="http://schemas.microsoft.biztalk.esb.test.com/test">  
```  
  
 The **Remove Namespace** component simply removes this namespace and returns a document that does not have a root node namespace, as shown here:  
  
```  
<CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1" Status="Status_2">  
```
