---
title: "Database Failover Support | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09347fdd-2929-4ed9-b0d8-698508663ecd
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Database Failover Support
You can pass an instance of the **PolicyFetchErrorHandler** delegate as a parameter to overloaded constructors of the **Policy** class. When an error occurs while fetching the policy details from the database, the delegate instance is invoked. You can also use a try-catch block to trap **RuleStoreConnectionException** and **RuleStoreCompatibilityException** exceptions that are raised when the rule engine fails to connect to the Rule Engine database.  
  
 If you do not pass an instance of the **PolicyFetchErrorHandler** delegate as a parameter to the **Policy** constructor, or if you use the **CallRules** shape in an orchestration, then if an error occurs while fetching the policy details from the database, the following events happen:  
  
1.  The rule engine uses the values of the **PolicyFetchErrorHandlerAssembly** and **PolicyFetchErrorHandlerClass** registry entries under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**. The default values for the **PolicyFetchErrorHandlerAssembly** and **PolicyFetchErrorHandlerClass** registry entries are **Microsoft.BizTalk.RuleEngineExtensions** and **Microsoft.BizTalk.RuleEngineExtension.ExceptionHelper** respectively.  
  
2.  The **ExceptionHelper** class implements the **IPolicyFetchErrorMaker** interface.  
  
3.  The rule engine invokes the **get_ErrorHandler** method on the **IPolicyFetchErrorMaker** interface to get a pointer to the error-handling method and invokes it.  
  
4.  The default error-handling method invokes the **SetDBFailure** method, which is defined in BTSDBAccessor.dll.  
  
5.  The **SetDBFailure** method causes the BizTalk service to shut down. The BizTalk service restarts in one minute and shuts down if the databases are still not available. This cycle repeats until the databases are available.