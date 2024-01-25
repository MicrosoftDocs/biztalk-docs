---
description: "Learn more about: Using the Flat File Serializing Engine"
title: "Using the Flat File Serializing Engine"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Using the Flat File Serializing Engine
The flat file serializing engine is invoked by calling the **Serialize** method of the **IFFDocumentSpec** interface. By providing a customized **XmlReader** as the argument to the method, you can control the final data that gets serialized. Data could be in any format, or could simply be a reader created of off an XmlDocument.  
  
## Example  
  
```  
Stream stm = docspec.Serialize(new MyXmlReader(originalXmlReader), Encoding.Unicode);  
```  
  
## See Also  
 [Microsoft.BizTalk.Component.Interop.IFFDocumentSpec](/dotnet/api/microsoft.biztalk.component.interop.iffdocumentspec)   
 [Using the Flat File Parsing Engine](../core/using-the-flat-file-parsing-engine.md)
