---
title: "The Sample Operations Error Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ops adapters, error handler"
  - "process management solution tutorial, Ops adapters"
ms.assetid: e6c55f01-c004-4340-beaa-d77764ae34c1
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# The Sample Operations Error Handler
The sample operations error handler has three major assemblies: **OperationsClient**, **OperationsHandler**, and **OperationsServer**.  
  
 The solution configures the adapter to use the **OpsClient** object in the **OperationsClient** assembly. As you'd expect, the **OpsClient** object implements the **IOpsAIC** interface.  
  
 The **OpsClient** object uses the **IOperationsSystem** interface to call the **OpsHandler** object through the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] remoting feature. The **IOperationsSystem** interface appears as follows:  
  
```  
public interface IOperationsSystem  
{  
    void Initialize(string initData);  
    void Post(string originMachine, byte[] message);  
}  
  
```  
  
 The **OperationsServer**, a console application, listens for requests for the **OpsHandler** object and acts as the server for the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] remoting feature. Calling the **Execute** method of the **OpsClient** object in turn invokes the **Post** method of the **OpsHandler** object.  
  
 The **OpsHandler** methods respond by writing out their argument strings using the **Trace** object. This posts the errors to the console. For more information about the **Trace** object, see "Trace Class" in the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Class Library.  
  
> [!NOTE]
>  The pattern here is the same as that in the **OrderHandler** in which an interface specifies the method calls between a client and a remoted object. There is, however, an additional layer of indirection here between the **OpsClient** and the **OpsHandler**.  
  
## See Also  
 [The Ops Adapter](../core/the-ops-adapter.md)