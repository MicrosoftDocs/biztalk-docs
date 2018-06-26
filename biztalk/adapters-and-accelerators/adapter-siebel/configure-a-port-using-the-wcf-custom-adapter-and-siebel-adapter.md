---
title: "Configure a port using the WCF-custom adapter and Siebel adapter in BizTalk | Microsoft Docs"
description: Create WCF-custom send and receive ports to use the Siebel eBusiness Applications adapter in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53c5ee07-36ae-474b-9241-8b53c9066ca1
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure a port using the WCF-custom adapter and Siebel adapter
This topic provides instructions on how to configure WCF-Custom send ports to perform outbound operations on a Siebel system using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).
  
## Deploying Adapters for Sending Messages to a Siebel System  
 Perform the following steps to configure a WCF-Custom send port for sending messages to a Siebel system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
 
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
3. Expand the application under which you wish to deploy the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
4. Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between BizTalk Server and the Siebel system.  
  
5. In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.  
  
6. From the **Type** drop-down list, select **WCF-Custom** and click **Configure**.  
  
7. In the **WCF-Custom Transport Properties** dialog box, do the following:  
  
   1. Click the **General** tab and in the **Address (URI)** field specify the connection URI to connect to a Siebel system. For more information about the connection URI, see [Create the Siebel system connection URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md).  
  
   2. On the **General** tab, in the **Action** text box, type the action for the operation. See [Messages and message schemas](messages-and-message-schemas-for-siebel-adapter-in-biztalk.md) for a list of actions for each operation. For example, the action to invoke the Insert operation on the Account business component is:  
  
      ```  
      http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Insert  
      ```  
  
   3. Click the **Binding** tab and from the **Binding Type** drop-down list, select **siebelBinding**. You can also specify the different binding properties exposed by the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. For more information, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).  
  
   4. Click the **Credentials** tab and do one of the following:  
  
      - Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to a Siebel system.  
  
      - Select the **Use Single Sign-On** option, and specify an affiliate ESSO application.  
  
        For more information about security with respect to BizTalk Server, see [Security with Siebel adapter and BizTalk Server](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md).  
  
   5. To return to the **Send Port Properties** dialog box, click **OK**.  
  
8. From the **Send handler** drop-down list, select **BizTalkServerApplication**.  
  
9. If you chose Static One-Way Send Port in step 4, specify a send pipeline. From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.  
  
10. If you chose Static Solicit-Response Port in step 4, specify send and receive pipelines.  
  
    1.  From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.  
  
    2.  From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.  
  
11. Click **OK**.  
  
## See Also  
[Manually configure a physical port binding to the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md)