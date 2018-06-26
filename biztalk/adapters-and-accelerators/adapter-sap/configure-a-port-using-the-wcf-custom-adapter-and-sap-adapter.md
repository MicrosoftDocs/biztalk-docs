---
title: "Configure a port using the WCF-custom adapter and SAP adapter in BizTalk | Microsoft Docs"
description: Create a WCF-Custom port to send or receive messages from SAP using the mySAP adapter in BizTalk Adapter Pack (BAP)
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3962456-e9ac-4575-8266-b35e892dd428
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure a port using the WCF-custom adapter and SAP adapter
This topic provides instructions on how to configure WCF-Custom send and receive ports to perform outbound and inbound operations on SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security User Rights](../../core/minimum-security-user-rights.md). 
  
## Deploy adapters to send messages to SAP  
Complete the following steps to configure a WCF-Custom send port for sending messages to SAP system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
3. Expand the application under which you want to deploy the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
4. Right-click **Send Ports**, point to **New**, and point to a type of port you want to configure depending on the mode of communication between BizTalk Server and the SAP system.  
  
5. In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.  
  
6. From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
7. In the **WCF-Custom Transport Properties** dialog box, do the following:  
  
   1. Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the SAP system. For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
   2. On the **General** tab, in the **Action** text box, type the action for the operation. See [Messages and message schemas](messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md) for a list of actions for each operation. For example, the action to invoke the RFC_CUSTOMER_GET would be:  
  
      ```  
      http://Microsoft.LobServices.Sap/2007/03/Rfc/RFC_CUSTOMER_GET  
      ```  
  
   3. Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**. You can specify the different binding properties exposed by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
   4. Click the **Credentials** tab and do one of the following:  
  
      -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to an SAP system.  
  
      -   Select the **Use Single Sign-On** option, and specify an affiliate SSO application.  
  
           For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).
  
           To return to the **Send Port Properties** dialog box, click **OK**.  
  
8. From the **Send handler** drop-down list, select **BizTalkServerApplication**.  
  
9. If you chose Static One-Way Send Port in step 4, specify a send pipeline. From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.  
  
10. If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.  
  
    1.  From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.  
  
    2.  From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.  
  
11. Click **OK**.  
  
## Deploy adapters to receive messages from SAP
Complete the following steps to configure a WCF-Custom receive port for receiving messages from SAP system using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
3. Expand the application under which you want to deploy the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
4. Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port** depending on the mode of communication between BizTalk Server and the SAP system.  
  
5. In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.  
  
6. On the **Receive Locations** tab, click **New**. The **Receive Location Properties** dialog box appears.  
  
7. In the **Receive Location Properties** dialog box, do the following:  
  
   1.  Specify a name for the receive location.  
  
   2.  From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
8. In the **WCF-Custom Transport Properties** dialog box, do the following:  
  
   1.  Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for the SAP system. For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).  
  
   2.  Click the **Binding** tab, and from the **Binding Type** drop-down list, select **sapBinding**. For more information about binding properties, see [Read about BizTalk Adapter for mySAP Business Suite binding properties](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
   3.  Click the **Others** tab, and do one of the following:  
  
       -   Select **User account**, and specify the user name and password to connect to an SAP system.  
  
       -   Select **Get credentials from affiliate application** option, and specify an affiliate application.  
  
            For more information about security with respect to BizTalk Server, see [Security with the SAP adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sap/security-with-the-sap-adapter-and-biztalk-server.md).
  
            Click **OK** to return to the **Receive Location Properties** dialog box.  
  
9. From the **Receive handler** drop-down list, select **BizTalkServerApplication**.  
  
10. If you chose **One-way Receive Port** in step 4, specify a receive pipeline. From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.  
  
11. If you chose **Request Response Receive Port** in step 4, specify send and receive pipelines.  
  
    1.  From the **Receive pipeline** drop-down list, select the pipeline corresponding to XMLReceive.  
  
    2.  From the **Send pipeline** drop-down list, select the pipeline corresponding to XMLTransmit.  
  
12. Click **OK i**n the **Receive Location Properties** dialog box.  
  
13. Click **OK** in the **Receive Port Properties** dialog box.  
  
## See Also  
[Manually configure a physical port binding to the SAP adapter](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)