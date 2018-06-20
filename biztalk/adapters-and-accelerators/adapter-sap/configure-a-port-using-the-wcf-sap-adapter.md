---
title: "Configure a port using the WCF-SAP adapter in BizTalk| Microsoft Docs"
description: Create a WCF-SAP port to send or receive messages from SAP using the mySAP adapter in BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 420683f8-2516-4c65-895d-fe535824d450
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure a port using the WCF-SAP adapter
This topic provides instructions on how to configure WCF-SAP send and receive ports to perform outbound and inbound operations on SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).
  
## Deploy adapters to send messages to SAP  
Complete the following steps to configure a WCF-SAP send port for sending messages to SAP system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).  
  
3. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
4. Expand the application under which you want to deploy the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
5. Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between BizTalk Server and the SAP system.  
  
6. In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.  
  
7. From the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.  
  
8. In the transport properties dialog box, do the following:  
  
   1. Click the **General** tab, click the **Configure** button, and provide values for the connection parameters. For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
   2. On the **General** tab, in the **Action** text box, type the action for the operation. See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) for a list of actions for each operation. For example, the action to invoke the RFC_CUSTOMER_GET would be:  
  
      ```  
      http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
      ```  
  
   3. Click the **Binding** tab and specify values for binding properties exposed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
      > [!NOTE]
      >  The binding properties are displayed based on whether you are configuring a send port or a receive port. For example, binding properties related to inbound operations are not available while configuring a send port because inbound operations require a receive port configuration.  
  
   4. Click the **Credentials** tab and do one of the following:  
  
   -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an SAP system.  
  
   -   Select the **Use Single Sign-On** option, and specify an affiliate SSO application.  
  
        For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).  
  
        To return to the **Send Port Properties** dialog box, click **OK**.  
  
9. From the **Send handler** drop-down list, select **BizTalkServerApplication**.  
  
10. If you chose to create a **Static One-Way Send Port** in step 5, specify a send pipeline. From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.  
  
11. If you chose to create a **Static Solicit-Response Port** in step 5, specify send and receive pipelines.  
  
    1.  From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.  
  
    2.  From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.  
  
12. Click **OK**.  
  
## Deploy adapters to receive messages from SAP  
Complete the following steps to configure a WCF-SAP receive port for receiving messages from SAP system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. Add the WCF-SAP adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Add the SAP Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md).  
  
3. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
4. Expand the application under which you want to deploy the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
5. Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port** depending on the mode of communication between BizTalk Server and the SAP system.  
  
6. In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.  
  
7. On the **Receive Locations** tab, click **New**. The **Receive Location Properties** dialog box appears.  
  
8. In the **Receive Location Properties** dialog box, do the following:  
  
   1.  Specify a name for the receive location.  
  
   2.  From the **Type** drop-down list, select the WCF-SAP adapter you added earlier, and then click **Configure**.  
  
9. In the transport properties dialog box, do the following:  
  
   1. Click the **General** tab, click the **Configure** button, and provide values for the connection parameters. For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
   2. Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**. For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
      > [!NOTE]
      >  The binding properties are displayed based on whether you are configuring a send port or a receive port. For example, binding properties related to inbound operations are not available while configuring a send port because inbound operations require a receive port configuration.  
  
   3. Click the **Other** tab, and do one of the following:  
  
   4. Select **User account**, and specify the user name and password to connect to an SAP system.  
  
   5. Select **Get credentials from affiliate application** option, and specify an affiliate application.  
  
       For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).  
  
       Click **OK** to return to the **Receive Location Properties** dialog box.  
  
10. From the **Receive handler** drop-down list, select **BizTalkServerApplication**.  
  
11. If you chose to create **One-way Receive Port** in step 5, specify a receive pipeline. From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.  
  
12. If you chose to create **Request Response Receive Port** in step 5, specify send and receive pipelines.  
  
    1.  From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.  
  
    2.  From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.  
  
13. Click **OK** in the **Receive Location Properties** dialog box.  
  
14. Click **OK** in the **Receive Port Properties** dialog box.

## See also
[Manually configure a physical port binding to the SAP adapter](manually-configure-a-physical-port-binding-to-the-sap-adapter.md)