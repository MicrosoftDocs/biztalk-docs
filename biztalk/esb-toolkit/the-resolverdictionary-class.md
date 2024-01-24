---
description: "Learn more about: The ResolverDictionary Class"
title: "The ResolverDictionary Class"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# The ResolverDictionary Class
The **ResolverDictionary** class is a **Dictionary**-based class that can store instances of the **Resolver** class as **String** name/value pairs. When creating instances of the **ResolverDictionary** class, you must provide a reference to an existing **Dictionary** instance. The **ResolverDictionary** class provides the data that the **Resolver** class uses when it performs run-time resolution.  
  
 The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] installer installs and registers the **Microsoft.Practices.ESB.Resolver.dll** assembly with the **ResolverDictionary** class in the global assembly cache.  
  
 The **ResolverDictionary** class exposes one method and one property:  
  
-   **Item(** key **)**. This method takes a string value that contains a key name. It returns the corresponding string value or an empty string if the item does not exist in the underlying **Dictionary** instance.  
  
-   **BaseDictionary**. This property returns a reference to the underlying **Dictionary** instance.
