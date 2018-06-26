---
title: "How to Configure a WCF-WSHttp Send Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF-WSHttp adapters, global variables"
  - "configuring [WCF-WSHttp adapters], send handlers"
  - "configuring [WCF-WSHttp adapters], global variables"
  - "send handlers, WCF-WSHttp adapters"
ms.assetid: b2c30edb-8f7b-4d3c-812b-5b877c47fda1
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a WCF-WSHttp Send Handler
Use the following procedure to configure the WCF-WSHttp send handler.  

> [!CAUTION]
>  When using WCF-WSHttp adapter handlers, it is recommended that you install the host instances for these handlers on [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computers.  

### To change global variables for a WCF-WSHttp send handler  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  

2. In the expanded adapter list, click **WCF-WSHttp**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.  

3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.  

4. In the **General** tab, Click **Properties**, On the **Proxy** tab, do the following.  


   |   Use this    |                                                                                                                                                                                                                        To do this                                                                                                                                                                                                                        |
   |---------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Use proxy** |                                                                                                                                                                              Indicate whether this send port uses a proxy server.<br /><br /> The default value is cleared.                                                                                                                                                                              |
   |  **Address**  |                      Specify the address of the proxy server. Use the **https** or the **http** scheme depending on the security configuration. This address can be followed by a colon and the port number. For example, http://127.0.0.1:8080.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.                      |
   | **User name** | Specify the user name to use for authentication. If integrated or Basic authentication is used, the user name includes the domain, that is, domain\username. If Digest authentication is used, the user name does not include domain\\.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string. |
   | **Password**  |                                                                                             Specify the password to use for authentication.<br /><br /> This property requires a value only if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256<br /><br /> The default is an empty string.                                                                                             |


5. Click **OK**.  

## See Also  
 [Configuring the WCF-WSHttp Adapter](../core/configuring-the-wcf-wshttp-adapter.md)