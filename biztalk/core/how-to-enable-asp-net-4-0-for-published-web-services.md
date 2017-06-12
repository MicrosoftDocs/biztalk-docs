---
title: "How to Enable ASP.NET 4.0 for Published Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58646ff2-77a3-49dc-8593-f6e41d85d4f3
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enable ASP.NET 4.0 for Published Web Services
Set the ASP.Net version in IIS.

The BizTalk Server Web Services Publishing Wizard relies on functionality provided with ASP.NET, which is included with the .NET Framework. The ASP.Net versions are included with the .NET CLR version you choose. 

This topic shows you how to change the .NET CLR version. 

## Prerequisites

IIS is included with the **Web Server (IIS)** role in the operating system. When you install this role, also select the newer version of ASP.NET. 
  
## Update an application pool
  
1.  Open **Internet Information Services (IIS) Manager**:

    1. In **Server Manager**, select **Tools**.
    2. Select **Internet Information Services (IIS) Manager**.
  
2.  Expand the server name, and select **Application Pools**.  
  
3.  Select the app pool, and open the **Basic Settings**.  
  
4. Set the **.NET CLR version** to the newer version, and select **OK** to save your changes.  

> [!NOTE]
> You can also change the version in the web.config file.
 
## Allow the ASP.Net extension
  
1.  Open **Internet Information Services (IIS) Manager**:

    1. In **Server Manager**, select **Tools**.
    2. Select **Internet Information Services (IIS) Manager**.
  
2.  Select the server name, and double-click **ISAPI and CGI Restrictions**.  
  
3. Confirm ASP.NET is **Allowed** for the 32-bit and 64-bit versions.  
  
## See Also  
 [Planning for Publishing Web Services](../core/planning-for-publishing-web-services2.md)