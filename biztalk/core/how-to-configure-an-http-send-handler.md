---
title: "How to Configure an HTTP Send Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send handlers, HTTP adapters"
  - "configuring [HTTP adapters], send handlers"
  - "HTTP adapters, send handlers"
ms.assetid: 821bf30c-b220-4ded-953d-7e745c0698b9
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an HTTP Send Handler
Use the following procedure to change the host with which the HTTP send handler is associated.  

> [!NOTE]
>  Each host can have only one send handler associated with it.  
> 
> [!CAUTION]
>  When using HTTP or SOAP adapter handlers, it is recommended that you install the host instances for these handlers on Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] computers.  

### To change global variables for an HTTP send handler  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  

2. In the expanded adapter list, click **HTTP**, in the right pane right-click the send handler that you want to configure, and then click **Properties**.  

3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated.  

4. On the **Properties** tab, do the following.  


   |         Use this          |                                                                                                                                                                                                 To do this                                                                                                                                                                                                  |
   |---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Request timeout (sec)** | Specify the time-out in seconds when waiting for a response from the server.<br /><br /> If set to zero (0), the HTTP adapter calculates the time-out based on the request message size.<br /><br /> If you do not provide a value, the value for the handler is used.<br /><br /> **Default value:** 0<br /><br /> **Type:** Long<br /><br /> **Minimum value:** 0<br /><br /> **Maximum value:** MAX_LONG |
   |   **Maximum redirects**   |                                                                                                       Specify the maximum redirects allowed for the message being sent.<br /><br /> **Default value:** 5<br /><br /> **Type:** Int<br /><br /> **Minimum value:** 0<br /><br /> **Maximum value:** 10                                                                                                       |
   |     **Content type**      |                                                                 Specify the content type of the request messages.<br /><br /> If you do not provide a value, the value for the handler is used.<br /><br /> **Default value:** Text/XML<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256                                                                  |


5. On the **Proxy** tab, do the following.  


   |   Use this    |                                                                                                                          To do this                                                                                                                           |
   |---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Use proxy** |                                                                Specify whether the HTTP send handler uses the proxy server.<br /><br /> **Default value:** False<br /><br /> **Type:** Boolean                                                                |
   |  **Server**   |               Specify the proxy server address for this send port.<br /><br /> This property requires a value if **Use proxy** is **True**.<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256                |
   |   **Port**    | Specify the proxy server port for this send port.<br /><br /> This property requires a value if **Use proxy** is **True**.<br /><br /> **Default Value:** 80<br /><br /> **Type:** Long<br /><br /> **Minimum value:** 0<br /><br /> **Maximum value:** 65535 |
   | **User name** |      Specify the user name to use for authentication with the proxy server.<br /><br /> This property requires a value if **Use proxy** is **True**.<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256       |
   | **Password**  |        Specify the user password for authentication with the proxy server.<br /><br /> This property requires a value if **Use proxy** is **True**.<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256        |


6. Click **OK**.  

## See Also  
 [Configuring the HTTP Adapter](../core/configuring-the-http-adapter.md)