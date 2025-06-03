---
description: "Learn more about: Wrapping the Parsing Engine"
title: "Wrapping the Parsing Engine"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
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
