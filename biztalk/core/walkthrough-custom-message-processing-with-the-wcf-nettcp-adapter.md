---
title: "Walkthrough: Custom Message Processing with the WCF-NetTcp Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b56b7492-2ea0-4c63-8f1b-430eb277517d
caps.latest.revision: 32
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Custom Message Processing with the WCF-NetTcp Adapter
In this walkthrough a [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] client submits a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message containing embedded binary JPEG image data to a BizTalk receive location using the WCF-NetTcp adapter. The binary encoded JPEG image gets extracted by using an XPath statement (with Base64 Node encoding) through the **Inbound Message Body** settings in the adapter’s configuration. XPath processing differs from the default method that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses to handle incoming messages. In the default method, the adapter obtains the entire contents of the **Body** element of the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message, and then submits it to the BizTalk MessageBox database. XPath message processing extracts specific parts of an incoming [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message to create a custom BizTalk message. In this sample XPath processing locates an XML element named **SendPicture** in the incoming [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message (which is in XML format). After finding that element, XPath extracts the element's value as a binary Base64 encoded object, and places that binary value into a BizTalk message. The message is published to the MessageBox database, then output to a FILE send port with the help of a send port filter subscription. No orchestrations are used in this sample, and all the processing is done through BizTalk messaging using XPath.  

 A [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] adapter is used to communicate with [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] clients and [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] remote services from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  It allows orchestrations and schemas to be published as [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] services, and also provides the ability for an orchestration to consume external WCF services. The WCF-NetTcp adapter uses the **NetTcpBinding** binding, which means the TCP transport using an optimized binary message encoding. The WCF-NetTcp adapter consists of both a send adapter and a receive adapter. It provides full access to SOAP security, reliability, and transaction features.  

 After completing this walkthrough, you will understand how to perform the following tasks:  

- By using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, import an MSI file to create a send port, a receive port, and a receive location.  

- By using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, configure a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] receive location to run an XPath statement to extract data from the **SendPicture** element of the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message.  

> [!NOTE]
>  The **hosttrusted** element specifies whether the host associated with the receive handler is trusted. In the bindings.xml file, it is set to its default setting of `false` because in this sample we don't care about the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Enterprise Single Sign-On service (SSO). SSO allows the passing of user credentials through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to integrate third-party applications with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. A `false` setting prevents a BizTalk message from passing through the BizTalk service as part of the SSO processing.  

## Prerequisites  
 To perform the steps in this sample ensure that your environment installs the following prerequisites;  

- Both the computer that builds the assemblies and runs the deployment process, and the computer that runs the sample, require Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], Microsoft [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], and Microsoft BizTalk Server.  

- The computer used to build the assemblies and run the deployment process requires Microsoft Visual Studio.  

- The computer that runs the sample requires the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Adapters and the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Administration Tools. These are options to install during setup of Microsoft BizTalk Server.  

- On the computers that you use to perform administrative tasks, you must run as a user account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application settings within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. This user account must also be a member of the local Administrators group for application deployment, managing host instances, and other tasks that may be required.  

- On any computer that requires [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] capability, complete the one-time setup procedure for the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] samples at [http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510).  

- On the computer that runs the sample and imports an .msi file into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ensure the host is not a trusted host or the import will fail.  

- You must download the walkthrough code and extract it to your computer.  This walkthrough is a part of the entire [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Adapter Walkthrough package. You can download the file **WCFAdapterWalkthroughs.exe** from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Developer Center at [http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140).  

### Configure the WCFCustomMessageProcessing application and artifacts  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Applications**, select **Import**, and then select **MSI file**. Go to the **C:\WCFCustomMessageProcessing\WCFCustomMessageProcessing.msi** file, and then click **Open**. This creates the following artifacts for this application:  

   - **FileSP** send port: The location on the local file system of **C:\WCFCustomMessageProcessing\Out** where the JPEG image data is sent by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] as the final output of the sample processing. You can view the send port filter of **BTS.RecievePortName = NetTcpRP** configured in the **FileSP Properties** dialog box under **Filters**. The filter is associated with the NetTcp receive port. Any messages accepted on the NetTcpRP receive port will be sent to the FileSP send port output location of **C:\WCFCustomMessageProcessing\Out** after the receive location executes the XPath processing on the message.  

   - **NetTcpRP** receive port: The port that logically contains the **NetTcpRL** receive location.  

   - **NetTcpRL** receive location: This uses the default **PassThroughTransmit** pipeline and the WCF-NetTcp adapter to run an XPath statement to pull the JPEG image data out of the incoming [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message.  

### Alternative steps to configure the WCFCustomMessageProcessing application  

- Alternatively, here are the manual steps to configure the application without using the **C:\WCFCustomMessageProcessing\bindings.xml** file. You do not need to do this if the previous binding file import process works correctly.  But, reading it may increase your knowledge of what is going on with the MSI file.  

- Create a one-way receive port (**NetTcpRP**) and a receive location (**NetTcpRL**).  

  1. Expand the **WCFCustomMessageProcessing** application, right-click **Receive Ports**, select **New**, and select **One-way Receive Port**. In the **Receive Port Properties** dialog box, enter `NetTcpRP` for **Name**, and click **OK**.  

  2. Right-click the **NetTcpRP** receive port, select **New**, and select **Receive Location**. In the **Receive Location Properties** dialog box, enter `NetTcRL` for **Name**. In the **Transport** section, click the **Type** drop-down list box, select **WCF-NetTcp** from the drop-down list, and then click **Configure**.  

  3. On the **General** tab, enter **net.tcp://localhost/NetTcpRL/Image** in the **Address(URI)** field.  

  4. On the **Security** tab, set the **Security mode** to **None.**  

  5. On the **Message** tab, select the **Path** option for the **Inbound BizTalk message body**, and enter `/*[local-name()="SendPicture" and namespace-uri()='http://tempuri.org/']/*[local-name()="stream"]` for the body path expression. Select **Base64** as the **Node Encoding**. The **Path** option is set to value because the body of the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives is in the following format: **\<SendPicture xmlns="http://tempuri.org/"\>\<stream\>*actual base 64 encoded binary image data*\</stream\>\</SendPicture\>**  

  6. In the **Receive Location Properties** dialog box, click **OK**.  

- Create a one-way file send port (FileSP) subscribed to the NetTcpRP receive port.  

  1.  Right-click **Send Ports**, select **New**, and select **One-way Receive Port**. Select **Static One-way Port**. Enter `FileSP` for **Name**.  

  2.  In the **Transport** section, click the **Type** drop-down list box, select **FILE** from the drop-down list, and then click **Configure**.  

  3.  Under **Destination Folder** enter `C:\WCFCustomMessageProcessing\Out`, and click **OK**.  

  4.  Click **Filters**, select `BTS.ReceivePortName == NetTcpRP`, and then click **OK.**  

### Configure the send port and run the application  

1. Right-click the **WCFCustomMessageProcessing** application and select **Start**. That will enlist the NetTcpRL receive location and start the FileSP send port.  

2. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open up the `Client.sln` file from the **C:WCFCustomMessageProcessing\Client** folder. In Solution Explorer, right-click the **Client** project and select **Build**.  

3. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], select **Debug**, and then select **Start Without Debugging** to run the Client.exe application. A command prompt will appear saying the image was submitted to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  

4. Observe the successful {GUID}.jpg file output to the send port file folder of **C:\WCFCustomMessageProcessing\Out**. This shows that the application processing to extract the JPEG file and write it out to a FILE send port completed successfully.
