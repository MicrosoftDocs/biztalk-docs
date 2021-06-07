---
description: "Learn about publishing Web services in BizTalk Server by using the BizTalk Web Services Publishing Wizard or by exposing orchestrations as Web services."
title: "Planning for Publishing Web Services2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Web services, planning"
  - "virtual directories, updating"
  - "BizTalk Server Web Services Publishing Wizard"
ms.assetid: 69107557-48e2-4f15-ba42-9fad476a8294
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Plan for Publishing Web Services

You can access Web services from your orchestrations. You can also use the BizTalk Web Services Publishing Wizard to publish your Web service.  
  
The following table lists some of the questions that you need to answer in planning for Web services.  
  
|Planning question|Recommendation|  
|-----------------------|--------------------|  
|Have you built your BizTalk Server project?|You must build your BizTalk Server project prior to running the BizTalk Web Services Publishing Wizard.|  
|Have you enabled your system to run Web services?|You must enable Web services on your computer before running the BizTalk Web Services Publishing Wizard. For more information about enabling your system for Web services, see [Enabling Web Services](../core/enabling-web-services.md).|  
|Have you verified that your schema contains only valid XML characters and elements?|Web services do not support Chinese, Japanese, or Korean (CJK) Unified Ideograph Extension A characters. There are also restrictions on certain XML Schema (XSD) elements. For more information about valid XML characters and supported elements and considerations for elements, see [Considerations When Publishing Web Services](../core/considerations-when-publishing-web-services.md).|  
|Do any of the message types in your BizTalk Server project use user-defined .NET classes?|You must install assemblies containing user-defined .NET classes that message types reference in the global assembly cache (GAC).|  
|Do your Web clients use the supplied credentials for the **WindowsUser** context property?|The credentials supplied by the Web clients consuming a published Web service use the **WindowsUser** context property. Party Resolution uses this property. If you set up a Party using the **WindowsUser** context property and the Web client consumes the Web service with credentials that match the Party, BizTalk Server identifies the message as coming from the corresponding predefined party. For more information about party resolution with pipeline components, see [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).|  
  
## See Also
  
[Publishing Web Services](../core/publishing-web-services.md)
