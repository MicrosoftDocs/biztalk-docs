---
title: "HTTP Adapter Samples | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP adapters, examples"
  - "examples, HTTP adapters"
ms.assetid: 6796ea39-2947-45df-b228-1ecdb23a7ab8
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# HTTP Adapter Samples
This section contains samples that illustrate advanced functionality when using the BizTalk HTTP Adapter.  
  
> [!NOTE]
>  Before running this sample, you need to do the following steps:  
> 
> 1. Open IIS, add ISAPI and CGI restrictions:  
> 
>    Click Machine Name on left panel, then click "ISAPI and CGI restrictions" on the right panel, then Add the ISAPI or CGI path:  
> 
>    On a 64 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\HttpReceive64\BTSHTTPReceive.dll  
> 
>    On a 32 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\HttpReceive\BTSHTTPReceive.dll  
> 
>    Check allowed extension path or execute.  
>    2.  Click "HTTPRequestResponseSample" on left panel, then click "Handler Mapping" on middle panel, then click "Add script mapping” with the following setting:  
> 
>    Request path:BTSHTTPReceive.dll  
> 
>    Executable:  
> 
>    On 64 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\HttpReceive64\  
> 
>    On 32 bit machine add:   C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\HttpReceive\  
> 
>    Request restrictions:  
> 
>    Verbs: POST  
> 
>    Access: Script  
  
## In This Section  
  
-   [HTTPSolicitResponse](../core/httpsolicitresponse.md)  
  
-   [HTTPRequestResponse](../core/httprequestresponse.md)