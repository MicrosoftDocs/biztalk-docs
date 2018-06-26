---
title: "Configure a port using the WCF-Siebel adapter | Microsoft Docs"
description: Create WCF-Siebel send ports to use the Siebel eBusiness Applications adapter in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6314104-c742-440c-b530-b5a82295353a
caps.latest.revision: 5
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure a port using the WCF-Siebel adapter
How to configure WCF-Siebel send ports to perform outbound operations on a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).
  
## Deploy adapters for sending messages to a Siebel system  
 Perform the following steps to configure a WCF-Siebel send port for sending messages to a Siebel system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).  
  
3. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
4. Expand the application under which you wish to deploy the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
5. Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between BizTalk Server and the Siebel system.  
  
6. In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.  
  
7. From the **Type** drop-down list, select the WCF-Siebel adapter you added earlier and click **Configure**.  
  
8. In the transport properties dialog box, do the following:  
  
   1. Click the **General** tab, click the **Configure** button, and provide values for the connection parameters. For more information about the connection URI, see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
   2. On the **General** tab, in the **Action** text box, type the action for the operation. See [Messages and message schemas](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) for a list of actions for each operation. For example, the action to invoke the Insert operation on the Account business component is:  
  
      ```  
      http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
      ```  
  
   3. Click the **Binding** tab and specify values for the binding properties. For more information, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
   4. Click the **Credentials** tab and do one of the following:  
  
      - Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.  
  
      - Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.  
  
        For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).  
  
   5. To return to the **Send Port Properties** dialog box, click **OK**.  
  
9. From the **Send handler** drop-down list, select **BizTalkServerApplication**.  
  
10. If you chose Static One-Way Send Port in step 5, specify a send pipeline. From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.  
  
11. If you chose Static Solicit-Response Port in step 5, specify send and receive pipelines.  
  
    1.  From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.  
  
    2.  From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.  
  
12. Click **OK**.  
  
## See Also  
[Manually configure a physical port binding to the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)