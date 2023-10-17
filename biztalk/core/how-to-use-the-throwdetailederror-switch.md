---
description: "Learn more about: How to Use the ThrowDetailedError Switch"
title: "How to Use the ThrowDetailedError Switch | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Web services, security"
  - "Web services, debugging"
ms.assetid: 8a8af3c0-a9a2-42fe-b0be-a5a106403747
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Use the ThrowDetailedError Switch
If an error occurs, the Web client receives a generic **SoapException**.  
  
 To debug your published Web service, you can add a switch to the Web.config file to control the level of the exception details returned from the published Web service.  
  
 The Web.config file contains an application setting switch, **ThrowDetailedError**. **False** is the default setting for **ThrowDetailedError**. If you change the setting to **True**, the server proxy returns inner exception information to the Web client enabling you to debug the published Web service.  
  
 The following XML code shows the **ThrowDetailedError** switch that appears in the Web.config file under the \<appSettings\> node:  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!IMPORTANT]
>  BizTalk Server does not return inner exception information to the Web client by default since it may contain sensitive information, such as application call stacks. After debugging, you should set the **ThrowDetailedError** setting to **False**.  
  
## See Also  
 [Debugging Published Web Services](../core/debugging-published-web-services.md)
