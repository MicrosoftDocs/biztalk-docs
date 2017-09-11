---
title: "Creating Ports | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ports, creating"
  - "receive ports"
  - "creating, send ports"
  - "creating, ports"
  - "Configuration database [BizTalk Server], connecting"
  - "receive ports, creating"
  - "send ports"
  - "send ports, creating"
ms.assetid: 4f99f884-5b84-4f9f-8cec-dd5da259ba7f
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating Ports
Use the following procedures to create [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports for Single Sign-on.  
  
## Creating a Send Port  
  
#### To create a send port  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.  
  
2.  Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.  
  
3.  In the **Send Port Properties** dialog box, do the following:  
  
    1.  Type a name for the send port, for example, `SSOSendToPeopleSoft`.  
  
    2.  From the **Type** drop-down list, select **PeopleSoft**.  
  
    3.  From the **Send handler** drop-down list, select the URI.  
  
    4.  From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
    6.  Click **Configure** to configure the send port.  
  
4.  In the **PeopleSoft Transport Properties** dialog box, do the following:  
  
    1.  Expand **Adapter Required Properties**, and enter **Application Server Path**, **JAVA_HOME**, **user name**, **password**, and the Jar file for connecting into the Peoplesoft system.  
  
         You do not have to set the logon information.  
  
    2.  In the list, select the SSO affiliate application you created to represent the PeopleSoft system.  
  
    3.  For **Use SSO**, select **Yes**.  
  
    4.  Click **OK**.  
  
5.  Click **OK**.  
  
## Creating a Receive Port  
  
#### To create a receive port  
  
1.  In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.  
  
2.  Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Ports**.  
  
3.  In the **Receive Port Properties** window, on the **General** page, do the following:  
  
    1.  In the **Name** field, type `ReceiveFromTIBCOEMS`.  
  
    2.  In the **Authentication** group box, specify how messages are handled when using authentication.  
  
    3.  Select the **Enable routing for failed messages** checkbox.  
  
4.  On the **Receive Locations** page, do the following:  
  
    1.  Click **New**.  
  
    2.  In the **Receive Locations** window, on the **General** page, type the **Name** of the receive location.  
  
    3.  From the **Type** drop-down list, select the transport type, and from the **Receive handler** drop-down list, select the transport address.  
  
    4.  From the **Receive pipeline** drop-down list, select the receive pipeline.  
  
    5.  On the **Schedule** page, select the **Start date** and the **End date** to restrict receiving documents.  
  
    6.  Select the **Enable service window** checkbox.  
  
    7.  Click **OK**.  
  
5.  On the **Inbound Maps** page, select the inbound maps for transforming documents on the selected port.  
  
6.  On the **Tracking** page, select the desired tracking message bodies and tracking message properties.  
  
7.  Click **OK**.  
  
## See Also  
 [Using Single Sign-On](../core/using-single-sign-on2.md)