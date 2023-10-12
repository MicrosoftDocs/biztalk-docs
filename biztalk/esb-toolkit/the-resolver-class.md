---
description: "Learn more about: The Resolver Class"
title: "The Resolver Class"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The Resolver Class
The **Resolver** class is a simple structure that exposes a name/value pair. The Resolver Web service returns a generic collection of instances of this class from its methods.  
  
 The ESB Core installer installs and registers the **Microsoft.Practices.ESB.Resolver.dll** assembly with Resolver class in the global assembly cache.  
  
 The use of a dictionary-based name/value approach makes it easier to add new items in future releases and minimizes the size of the resolution result by avoiding inclusion of non-relevant properties that depend on the resolution method and the current resolver type.  
  
 The **Resolver** class exposes two properties:  
  
-   **Name**. This is the name of a name/value pair that contains information that is returned after a connection string is resolved.  
  
-   **Value**. This is the value that corresponds to the name of the name/value pair.
