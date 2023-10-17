---
description: "Learn more about: Wrapping the Parsing Engine"
title: "Wrapping the Parsing Engine | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pipeline components [custom], wrapping"
  - "pipeline components [custom], code samples"
ms.assetid: e00994de-bb86-40c0-a891-3f202147b5fe
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Wrapping the Parsing Engine
You can create your own **XmlReader** that embeds the reader returned by the **Parse** method and provides customization.  
  
## Example  
  
```  
class MyXmlReader : XmlReader  
{  
   public MyXmlReader(XmlReader xr)  
   {  
      _xr = xr;  
   }  
  
   // Overrides XmlReader and provides customized functionality of _xr  
   // ...  
}  
```  
  
## See Also  
 [Using the Flat File Parsing Engine](../core/using-the-flat-file-parsing-engine.md)
