---
description: "Learn more about: Using the Flat File Serializing Engine"
title: "Using the Flat File Serializing Engine | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components [custom], code samples"
  - "IFFDocumentSpec interface"
  - "pipeline components [custom], flat file documents"
  - "pipeline components [custom], engines"
ms.assetid: 0a519f0f-392b-4fa3-ab08-f09012d033af
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the Flat File Serializing Engine
The flat file serializing engine is invoked by calling the **Serialize** method of the **IFFDocumentSpec** interface. By providing a customized **XmlReader** as the argument to the method, you can control the final data that gets serialized. Data could be in any format, or could simply be a reader created of off an XmlDocument.  
  
## Example  
  
```  
Stream stm = docspec.Serialize(new MyXmlReader(originalXmlReader), Encoding.Unicode);  
```  
  
## See Also  
 [Microsoft.BizTalk.Component.Interop.IFFDocumentSpec](/previous-versions/)   
 [Using the Flat File Parsing Engine](../core/using-the-flat-file-parsing-engine.md)