---
title: "Assemblies and Artifacts Installed by the Exception Management Samples | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af580992-73d4-4b16-a1cc-fa819b441fca
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Assemblies and Artifacts Installed by the Exception Management Samples
The following table lists the assemblies and other artifacts installed for the ESB Exception Management sample.  
  
|Location|Category|Name and version of the component|  
|--------------|--------------|---------------------------------------|  
|BizTalk application GlobalBank.ESB|Orchestrations|GlobalBank.ESB.ExceptionHandling.Processes.EAIProcess|  
|||GlobalBank.ESB.ExceptionHandling.Handlers.EAIGenericHandler|  
|||GlobalBank.ESB.ExceptionHandling.Handlers.EAIProcessHandler|  
|BizTalk application GlobalBank.ESB|Send Ports|EAIProcessHandler.RepairSubmit|  
|||EAIGenericHandler.PostTmpMsg|  
|||EAIProcess.PostApproval|  
|||EAIProcessHandler.PostDecline|  
|||ALL.Exceptions_FILE (references the GlobalFaultProcessor pipeline)|  
|BizTalk application GlobalBank.ESB|Receive Ports|EAIProcess.RequestPort|  
|BizTalk application GlobalBank.ESB|Receive Locations|EAIProcess.RequestPort_FILE|  
|||EAIProcess.ReSubmit_HTTP|  
|BizTalk application GlobalBank.ESB|Schemas|GlobalBank.ESB.ExceptionHandling.Schemas.System_Properties Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Schemas.Request Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Schemas.RequestDenied Version 2.0.0.0|  
|BizTalk application GlobalBank.ESB|Pipelines|GlobalBank.ESB.ExceptionHandling.Pipelines.GlobalFaultProcessor Version 2.0.0.0|  
|BizTalk application GlobalBank.ESB|Resources|GlobalBank.ESB.ExceptionHandling.Handlers Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Processes Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Schemas Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Pipelines Version 2.0.0.0|  
|BizTalk application GlobalBank.ESB|Policies||  
|BizTalk application GlobalBank.ESB|Maps|GlobalBank.ESB.ExceptionHandling.Schemas.MapToReqDenied Version 2.0.0.0|  
|Global assembly cache|Assemblies|GlobalBank.ESB.ExceptionHandling.Handlers Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Processes Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Schemas Version 2.0.0.0|  
|||GlobalBank.ESB.ExceptionHandling.Pipelines Version 2.0.0.0|  
|%Program Files%\\BizTalk Server\Pipeline Components|Pipeline components||