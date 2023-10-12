---
description: "Learn more about: Customizing Parsing Engine Errors"
title: "Customizing Parsing Engine Errors"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Customizing Parsing Engine Errors
You can register your own error-handling callback with the parsing engine to handle errors.  
  
## Example  
  
```  
bool MyErrorHandler(ErrorContext ctx)  
{  
   // Handle the error  
   return true;  
   // true=continue parsing, false=stop  
}  
  
FFReader ffr = (FFReader)docspec.Parse(new DataReader());  
ffr.OnErrorEvent += MyErrorHandler;  
```  
  
## See Also  
 [Using the Flat File Parsing Engine](../core/using-the-flat-file-parsing-engine.md)
