---
title: "How to Configure the HTTP Receive Adapter2 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP receive adapter, configuring"
  - "configuring HTTP receive adapter"
ms.assetid: dd26fd57-90d8-4ffe-b56f-8de55ecc6f68
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure the HTTP Receive Adapter
You can use the HTTP receive adapter to submit messages to BizTalk Server. The HTTP receive adapter is an Internet Information Services (IIS) ISAPI extension that is hosted in the IIS process.  
  
### To configure the HTTP receive adapter  
  
1.  Copy the HTTP receive adapter (BTSHTTPReceive.dll) from **\<BizTalk2010>\HttpReceive>** to the folder containing your Single Sign-On (SSO) project (for example, **<Adapter_install>\biztalk2010\SSO\mySSODemo**).  
  
    1.  Add a new Web service extension mySSODemo.  
  
    2.  Browse to and copy <BizTalk_install>\HttpReceive to the folder containing your SSO project, for example,  
  
         <Adapter_install>\biztalk2010\SSO\mySSODemo\BTSHTTPReceive.dll.  
  
    3.  Set status of mySSODemo Web service extension to **Allowed**.  
  
2.  Restart IIS to ensure that all changes are in effect.  
  
## See Also  
 [Security in the adapter](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)