---
title: "How to Configure a SOAP Send Handler | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send handlers, SOAP adapters"
  - "SOAP adapters, denial of service"
  - "denital of service, HTTP adapters"
  - "configuring [SOAP adapters], send handlers"
  - "configuring [SOAP adapters], denial of service"
  - "SOAP adapters, send handlers"
  - "denial of service, SOAP adapters"
ms.assetid: fd610a3f-ca10-42e0-b81e-219e07e33830
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure a SOAP Send Handler
Use the following procedure to configure the SOAP send handler.  

> [!CAUTION]
>  When using HTTP or SOAP adapter handlers, it is recommended that you install the host instances for these handlers on Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]computers.  

### To change global variables for a SOAP send handler  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  

2. In the expanded adapter list, click **SOAP**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.  

3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.  

4. On the **Proxy** tab, do the following.  


   |   Use this    |                                                                                                                  To do this                                                                                                                   |
   |---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Use proxy** |                                                                                          Indicate whether the SOAP send handler uses a proxy server.                                                                                          |
   |  **Server**   |                  Specify the name of the proxy server.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256                   |
   |   **Port**    | Specify the port the SOAP send handler uses.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> Default Value: 80<br /><br /> Type: Long<br /><br /> Minimum value: 0<br /><br /> Maximum value: 65535 |
   | **User name** |             Specify the user name to use for authentication.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256             |
   | **Password**  |             Specify the password to use for authentication.<br /><br /> This property only requires a value if **Use proxy** is selected.<br /><br /> Type: String<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256              |


5. Click **OK**.  

## See Also  
 [Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md)   
 [Publishing Web Services](../core/publishing-web-services.md)