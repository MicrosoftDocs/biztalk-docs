---
title: "Orchestration Variable Types | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "orchestrations, variables"
ms.assetid: 34990be2-35b6-40ec-b107-42a1c7b45aca
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Orchestration Variable Types
You can declare variables of the following predefined types:  

|||||  
|-|-|-|-|  
|boolean|byte|char|datetime|  
|decimal|double|int16|int32|  
|int64|long|sbyte|single|  
|string|timespan|uint16|uint32|  
|uint64||||  

 You can also declare variables of any .NET-based types that are referenced in your project.  

## Considerations for Declare Orchestration Variables  
 When declare orchestration variables, consider the following:  

- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] supports multivalued context properties for certain content-based routing scenarios, but you cannot use such properties in orchestrations.  

- In order to support suspension and re-hydration of orchestrations, all orchestration variables must be capable of having their state persisted.  Typically, this is accomplished by the variable's type or class being serializable or streamable.  

- These .NET-based types (classes) must be serializable classes.  They may either implement this by being declared with the "[Serializable]” attribute or by explicitly implementing the ISerializable .NET interface (in the System.Runtime.Serialization namespace).  

- If the .NET-based type is actually a runtime callable wrapper (RCW) of an underlying COM component, then that COM component must implement the interface(s) required for the RCW to be a serializable .NET class (e.g. IPersistStream, IPersistStreamInit).  

- Because any .NET-based (or underlying COM) types are executing within the flow of an orchestration, methods in these types must not delay execution of the orchestration (e.g. through contention for resources, etc.).  And any consumption of resources by these type implementations will affect the host instance in which the calling orchestration runs.
