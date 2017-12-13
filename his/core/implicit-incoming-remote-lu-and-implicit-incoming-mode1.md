---
title: "Implicit Incoming Remote LU and Implicit Incoming Mode1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7ccacec-9758-4104-87f5-fd8bfe8d979f
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Implicit Incoming Remote LU and Implicit Incoming Mode
An implicit incoming remote LU is a remote APPC LU that defines the properties to use when [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)] receives a request to start a session with a local LU and when the remote LU named in the request is not recognized by Host Integration Server.  
  
 An implicit incoming mode is a mode that defines the properties to use when Host Integration Server receives a request to start a session and the mode named in the request is not recognized by Host Integration Server.  
  
 An implicit incoming remote LU requires an implicit incoming mode. An implicit incoming mode must be configured for any remote LU that will be used as an implicit incoming remote LU. An implicit incoming mode can be (but does not have to be) configured for remote LUs that will only be used explicitly.  
  
 You may want to accept incoming requests that arrive by many different remote LUs without having to explicitly define each remote LU on a Host Integration Server computer. The Implicit Incoming Remote LU and Implicit Incoming Mode allow for flexible acceptance of requests. When these two items have been configured, and an incoming request is received by Host Integration Server, the remote LU need not be recognized, as long as the local LU specified in the request is recognized. In such a situation, Host Integration Server uses the properties of the Implicit Incoming Remote LU and Implicit Incoming Mode for that LU-LU session.  
  
 For a session to be established, the incoming local LU name must be recognized by Host Integration Server. Then the incoming remote LU must either be recognized explicitly or handled implicitly (if an implicit incoming remote LU has been configured). If the remote LU is recognized explicitly, but the mode is not recognized (as part of an LU-LU pair), Host Integration Server internally creates a new mode definition with the correct name using the properties of the implicit incoming mode. Alternatively, if the remote LU is handled implicitly, Host Integration Server also handles the mode implicitly, by internally creating a mode, as described.  
  
### To use an implicit incoming remote LU  
  
1.  In the SNA Manager tree, expand an SNA subdomain, expand the server you want to work with, expand **SNA service**, and then expand **Local APPC LUs**.  
  
2.  Right-click the first local LU that you want to configure, and click **Properties**.  
  
3.  Click the **Advanced** tab, and specify the **Implicit Incoming Remote LU** for incoming conversations, and then click **OK** to exit.  
  
4.  Using steps 2–4, configure each local LU that the remote system will call.  
  
5.  Expand **Remote APPC LUs**, right-click the remote LU that you want to configure, and then click **Properties**.  
  
6.  Click the **Options** tab, and select the **Implicit Incoming Mode**.  
  
7.  On the **Action** menu, click **Save configuration**.  
  
> [!NOTE]
>  All incoming requests must specify a local LU name that is recognized by Host Integration Server, even when using an implicit incoming remote LU and implicit incoming mode.  
  
## See Also  
 [APPC Mode Definition](../core/appc-mode-definition2.md)   
 [Default Local APPC LU and the Default Remote APPC LU](../core/default-local-appc-lu-and-the-default-remote-appc-lu1.md)   
 [Default Outgoing Local APPC LU Pool](../core/default-outgoing-local-appc-lu-pool1.md)   
 [Single-System APPC](../core/single-system-appc2.md)