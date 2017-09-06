---
title: "How to Throw Fault Exceptions from Orchestrations Published as WCF Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "errors, WCF services"
  - "WCF services, orchestrations"
  - "WCF services, errors"
  - "orchestrations, WCF services"
ms.assetid: 89f57841-d40e-4a5a-90a8-5556a2766c03
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Throw Fault Exceptions from Orchestrations Published as WCF Services
Two types of SOAP faults can be sent from an orchestration: typed and untyped SOAP faults. Typed SOAP faults are those in which an operation has a **System.ServiceModel.FaultContractAttribute** that specifies a custom SOAP fault type. Untyped SOAP faults are those that are not specified in the contract for an operation.  
  
 WCF adapters do not support processing typed fault contract exceptions for orchestrations published as WCF services. However, untyped SOAP faults can always be returned by orchestrations or pipelines. To return an untyped SOAP fault, you need to set the **System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults** on the receive location, or in the config file, to permit WCF clients to obtain information about internal service operation exceptions.  
  
 The following code shows how to set the property in a config file:  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <serviceBehaviors>  
                <behavior name="ServiceBehaviorConfiguration">  
                    <serviceDebug includeExceptionDetailInFaults="true" />  
                </behavior>  
            </serviceBehaviors>  
        </behaviors>  
</configuration>  
```  
  
## See Also  
 [How to Handle Typed Fault Contracts in Orchestrations](../core/how-to-handle-typed-fault-contracts-in-orchestrations.md)