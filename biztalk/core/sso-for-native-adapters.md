---
title: "SSO for Native Adapters | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "adapters, SSO"
  - "SSO, adapters"
ms.assetid: d8527f0f-910c-42ce-9bd3-83ab6d4349c0
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SSO for Native Adapters
Enterprise Single Sign-On (SSO) enables you to sign on only once when interoperating with different computer systems or Web sites. This feature of Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables BizTalk adapters to provide the appropriate user ID and credentials to multiple applications within your network that use a common authentication mechanism based on your Microsoft Windows credentials. After Windows authenticates your credentials, you do not need to provide additional credentials to connect to the applications.  
  
 SSO is available for the HTTP and SOAP adapters, although it is disabled by default. For the HTTP adapter, you can configure the send port and receive location to use SSO; for the SOAP adapter, you can configure only the receive location to use SSO. For both adapters, you use the BizTalk Server Administration console to configure SSO.  
  
 Authentication in SSO relies primarily on Windows authentication and the Windows groups created in Active Directory. All operations completed by a user or administrator with SSO require that Windows authenticate the user or administrator first.  
  
 For more information about how SSO works with the HTTP and SOAP adapters, see the appropriate topics in See Also.  
  
## See Also  
 [Using SSO](../core/using-sso.md)   
 [HTTP Adapter](../core/http-adapter.md)   
 [SOAP Adapter](../core/soap-adapter.md)