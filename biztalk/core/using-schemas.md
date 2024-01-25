---
description: "Learn more about: Using Schemas"
title: "Using Schemas"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Using Schemas
This section contains code examples for common tasks associated with using schemas.  
  
## Using XSD schemas  
 The `IDocumentSpec Interface` interface represents a document shape defined by an XML Schema definition language (XSD) schema; the shape is rooted by a top-level element of the XSD. After the schema is installed, it can be retrieved by calling the `IPipelineContext.GetDocumentSpecByType Method` or `IPipelineContext.GetDocumentSpecByName Method` methods in the **IPipelineContext** interface.  
  
```  
IDocumentSpec docspec = pipeineContext.GetDocumentSpecByType("myschema#root");  
```  
  
## Using XSD flat file schemas  
 Both the **GetDocumentSpecByType** and **GetDocumentSpecByName** methods return the **IDocumentSpec** interface. If the schema is actually a flat file schema (one that has additional flat file-specific annotations), you can typecast the **IDocumentSpec** into **IFFDocumentSpec** and initiate parsing and serializing sequences from there.  
  
```  
IFFDocumentSpec docspec = (IFFDocumentSpec) pipeineContext.GetDocumentSpecByType("myschema#root");  
```  
  
## See Also  

[Using the Parsing and Serializing Engines](../core/using-the-parsing-and-serializing-engines.md)
