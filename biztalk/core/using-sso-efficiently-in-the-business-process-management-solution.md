---
title: "Using SSO Efficiently in the Business Process Management Solution | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSO, process management solutions"
  - "SSO, configuration values"
  - "caching, configuration values [SSO]"
  - "SSO, caching"
  - "process management solution tutorial, SSO"
ms.assetid: 39fbc42d-caa4-4003-a13b-5cde578eb5e1
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using SSO Efficiently in the Business Process Management Solution
Like the Service Oriented solution, the Business Process Management solution uses Enterprise Single Sign-On (SSO) to store configuration values such as the number of order processing stages. It uses the secret store because it is present whenever BizTalk is installed, SSO caches the configuration information so that the values are readily available, and it can protect information such as database connection strings and passwords. For all of these reasons, the secret store is a good place for the configuration information even if Single Sign-On weren't being used for managing connections to the backend applications.  
  
 To reduce latency, the solution uses a local cache for the configuration values. The solution refreshes the cache every five minutes.  
  
 This topic describes the caching mechanism used by the solution. This solution takes a slightly different approach to SSO caching than does the service oriented solution. For a description of how the service oriented solution caches SSO values, see [Using SSO Efficiently in the Service Oriented Solution](../core/using-sso-efficiently-in-the-service-oriented-solution.md).  
  
## Caching Configuration Values Locally  
 The business process management solution uses properties on a singleton object to provide access to the SSO values.  
  
> [!NOTE]
>  Recall that a singleton object is an object that can have only one instance. For more information about singleton objects and creating them in C#, see [http://go.microsoft.com/fwlink/?LinkId=58806](http://go.microsoft.com/fwlink/?LinkId=58806).  
  
 In the solution, an orchestration first retrieves the singleton object and then references the values through the object's properties. Here is code from the **OrderManager** orchestration:  
  
```  
configData = Microsoft.Samples.BizTalk.SouthridgeVideo.Utilities  
                .SsoConfigHelper.Singleton;  
numStages = configData.TotalStages;  
```  
  
 The orchestration calls the **Singleton** method on the **SsoConfigHelper** object to get access to the one copy of the object. With the object in hand, the orchestration retrieves the number of processing stages, **TotalStages**.  
  
 The solution follows a common method of creating a singleton: make the constructor private, have the object create an instance of itself and assign that to a private variable, and, through a method or property, provide access to the value of that variable. The **SsoConfigHelper** object uses a property, **Singleton**, to provide access to the single copy of itself.  
  
> [!NOTE]
>  The **SsoConfigHelper** object uses a static constructor to get the initial values from the SSO cache and to set up the refresh mechanism. Because a static constructor cannot be called, it preserves the singleton design. For more information about static constructors, see [http://go.microsoft.com/fwlink/?LinkId=59142](http://go.microsoft.com/fwlink/?LinkId=59142).  
  
 All objects that an orchestration references, whether directly or indirectly, must be serializable. For more information, see "Serialization" in [Persistence and the Orchestration Engine](../core/persistence-and-the-orchestration-engine.md). Although the **SsoConfigHelper** object is necessarily serializable, if the engine dehydrates the orchestration, when the orchestration rehydrates it will still use the single, current instance of the object. For more information about serialization and BizTalk Server variables, see [Orchestration Variable Types](../core/orchestration-variable-types.md).  
  
> [!NOTE]
>  All public methods on the object in the service oriented solution are static. Thus the orchestration does not need to assign an instance to a variable, and there is no need for the class to be serialized.  
  
 The **SsoConfigHelper** object uses the same mechanisms to retrieve and refresh configuration values as does the service oriented solution. The same pattern of locking is also used. For more information about these mechanisms, see [Using SSO Efficiently in the Service Oriented Solution](../core/using-sso-efficiently-in-the-service-oriented-solution.md) and the source code for **SsoConfigHelper**.  
  
 Like the Single Sign-On caching performed in the service oriented solution, the business process management solution implements the **IPropertyBag** interface from the **Microsoft.BizTalk.SSOClient.Interop** namespace to store the values. The business process management solution uses a **HybridDictionary** object rather than a **NameValueCollection** object.  
  
 Unlike the Service Oriented solution, the Business Process Management solution exposes an object with properties that correspond to the configuration data. This prevents the orchestration from having to deal with differences in message types.  
  
## See Also  
 [Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md)