---
title: "Adapter Interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7398aeb-7c1c-400e-a552-d0ab39e55a0b
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Adapter Interfaces
There are three interfaces that custom adapters must implement, and two interfaces that are optional.  
  
## Mandatory interfaces  
 All adapters must implement the following interfaces.  
  
### IBaseComponent  
 This interface details the **Name**, **Version**, and **Description** of the adapter.  
  
### IBTTransport  
 This interface details the **Transport Type** and **ClassID** of the adapter.  
  
### IBTBatchCallback  
 This interface is a callback interface through which the adapter receives status and error information for a batch of messages it submits to the Messaging Engine.  
  
## Optional interfaces  
 Adapters may or may not implement the following interfaces, depending on their needs.  
  
### IPersistPropertyBag  
 This is a configuration interface through which handler configuration is delivered to the adapter. This interface is required only for adapters that have handler configuration information.  
  
### IBTTransportControl  
 This interface is used to initialize and terminate an adapter. The adapter's transport proxy is passed to it through this interface. This interface is not required for isolated adapters.