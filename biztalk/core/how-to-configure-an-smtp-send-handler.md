---
title: "How to Configure an SMTP Send Handler | Microsoft Docs"
ms.custom: ""
ms.date: "2015-10-22"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "send handlers, SMTP adapters"
  - "SMTP adapters, send handlers"
  - "configuring [SMTP adapters], send handlers"
ms.assetid: b68a36ce-f0a5-4302-a405-bb154c935f47
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure an SMTP Send Handler
You can set SMTP send handler properties in the BizTalk Administration console. These send handler properties are used as the send port configuration values if the properties are not set on the individual SMTP send port.  

### To change global variables for an SMTP send handler  

1. In the BizTalk Server Administration Console, expand [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  

2. In the expanded adapter list, click **SMTP**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.  

3. In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated, and then click **Properties**.  

4. In the **SMTP Transport Properties** dialog box, on the **Properties** tab, do the following:  


   |             Use this              |                                                                                                                                                                                                                                                             To do this                                                                                                                                                                                                                                                             |
   |-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **SMTP server name and TCP port** | **[!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)]**<br /><br /> Required. Enter the SMTP server  name and the TCP port number (optional) to use when sending messages. For example, you can enter:<br /><br /> -   mySMTPserver<br />-   mySMTPserver.internet.com:2525<br /><br /> **In previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]** (including BizTalk Server 2013), enter only the SMTP server name. TCP Port 25 is hard-coded.<br /><br /> Maximum length: 256 |
   |     **From (e-mail address)**     |                                                                                                                                                                                                               Required. Enter the e-mail address to put on the SMTP **From** header.<br /><br /> Maximum length: 256                                                                                                                                                                                                               |
   |      **Authentication type**      |                                                                                                                                          Enter the type of authentication to use with the SMTP server.<br /><br /> Options:<br /><br /> -   **No authentication**<br />-   **Basic authentication**<br />-   **Process account (NTLM)**<br /><br /> Default value: Process account (NTLM)                                                                                                                                          |
   |           **User name**           |                                                                                                                                                Enter the user name to use for authentication with the SMTP server.<br /><br /> This property requires a value if **Authentication type** is **Basic authentication**.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256                                                                                                                                                |
   |           **Password**            |                                                                                                                                                Enter the password to use for authentication with the SMTP server.<br /><br /> This property requires a value if **Authentication type** is **Basic authentication**.<br /><br /> Minimum length: 0<br /><br /> Maximum length: 256                                                                                                                                                 |


5. Click **OK**.  

## See Also  
 [Configuring the SMTP Adapter](../core/configuring-the-smtp-adapter.md)