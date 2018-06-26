---
title: "Walkthrough: Using the Message Security Mode with the WCF-NetTcp Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7f6e892-34ce-4132-8867-54cc3bbfe507
caps.latest.revision: 47
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Using the Message Security Mode with the WCF-NetTcp Adapter

> [!NOTE]
>  For more information about adapters, see [Adapters in BizTalk Server](../core/adapters-in-biztalk-server.md).  

## Introduction

 This walkthrough shows how to configure the WCF-NetTcp adapter to use the [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] Message security mode, which uses the WS-Security specification to help secure messages that the adapter transmits. This specification describes enhancements to the SOAP messaging protocol to accomplish confidentiality, integrity, and authentication at the SOAP message level. Message security mode requires the service certificate to be specified for operations such as encryption/decryption and signing/verification purposes depending on the security mode combinations.  

 The WCF-NetTcp adapter uses the NetTcpBinding binding to communicate between [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] clients and [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] remote services. It provides full access to SOAP security, reliability, and transaction features. It allows orchestrations and schemas to be published as [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] services, and also provides the ability for an orchestration to consume external WCF services. This adapter uses the TCP transport, and messages have binary encoding. The WCF-NetTcp adapter consists of both a send adapter and a receive adapter.  

 This walkthrough shows how to create certificates for Message security mode by using the Active Directory Certificate Service. You will create certificates for the server and the client, and then configure a WCF-NetTcp receive location to use the certificates in Message security mode. By using a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] client, you will send messages to that receive location in an encrypted state according to XML Encryption Syntax and Processing.  

 After completing this walkthrough, you will understand how to perform the following tasks:  

- Use the Active Directory Certificate Service to create a certificate request and complete the process by issuing the certificate.  

- From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, configure the WCF-NetTcp adapter to use the Message security mode.  

## Prerequisites  
 To perform the steps in this sample ensure that your environment installs the following prerequisites;  

- Both the computer that builds the assemblies and runs the deployment process, and the computer that runs the sample, require Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], Microsoft [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], and Microsoft BizTalk Server.  

- The computer used to build the assemblies and run the deployment process requires Microsoft Visual Studio.  

- The computer that runs the sample requires the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Adapters and the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Administration Tools. These are options to install during setup of Microsoft BizTalk Server.  

- On the computers that you use to perform administrative tasks, you must run as a user account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application settings within the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console. This user account must also be a member of the local Administrators group for application deployment, managing host instances, and other tasks that may be required.  

- On any computer that requires [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] capability, complete the one-time setup procedure for the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] samples at [http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510).  

- On the computer that runs the sample and imports a binding or an .msi file into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ensure the host is not a trusted host or the import will fail.  

- On the computer that runs the sample ensure that Active Directory Certificate Services is installed.  

- You must download the walkthrough code and extract it to your computer.  This walkthrough is a part of the entire [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Adapter Walkthrough package. You can download the file **WCFAdapterWalkthroughs.exe** from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Developer Center at [http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140).  

## Create the certificates for this walkthrough  

1. In this section you will request service and client certificates, issue the certificates, and install them into the appropriate stores. Active Directory Certificate Services is used to create a certificate with a trusted certificate chain. If you did not install Active Directory Certificate Services as part of the Prerequisites, then install Active Directory Certificate Services on your computer. If it is already installed, go to step 2.  

   1.  Click **Start**, point to **Administrative Tools**, and then click **Server Manager**.  

   2.  Under the **Server Manager** node, click **Add**, and then click **Roles**.  

   3.  This brings up the **Before you begin** dialog for the **Add Roles Wizard**. Click **Next**.  

   4.  On the **Select Server Roles** page, select **Active Directory Certificate Services**, click **Next**, and then follow the on-screen instructions to complete the installation.  

2. Create a certificate request for the service authentication as follows:  

   1. In Internet Explorer, visit the Web site `http://localhost/certsrv`. On the **Welcome** page, click **Request a Certificate**, and then click **Advanced certificate request** on the **Request a Certificate** page.  

      > [!NOTE]
      >  When using [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] as the certificate authority and requesting a certificate request from a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computer, you may get the error **“In order to complete certificate enrollment, the Web site for the CA must be configured to use HTTPS authentication”**. If this error occurs, the enrollment website needs to be configured with a Web Certificate (SSL). Refer to these links for details in accomplishing this task:  
      > 
      >  [AD CS: Web Enrollment](http://technet.microsoft.com/library/cc732517.aspx)  
      > 
      >  [IIS Server Certificate Installation Instructions](http://msdn.microsoft.com/library/ms751408.aspx)  

   2. On the **Advanced Certificate Request** page, click **Create and submit a request to this CA**.  

   3. On the **Advanced Certificate Request** page, type `localhost` in the **Name** text box, select **Server Authentication Certificate** from the **Type of Certificate Needed** drop-down list, and then click **Submit**.  

3. Create a certificate request for client authentication as follows:  

   1.  In Internet Explorer, visit the Web site `http://localhost/certsrv`. On the **Welcome** page, click **Request a Certificate**, and then click **Advanced certificate request** on the **Request a Certificate** page.  

   2.  On the **Advanced Certificate Request** page, click **Create and submit a request to this CA**.  

   3.  On the **Advanced Certificate Request** page, type `contoso` in the **Name** text box, select **Client Authentication Certificate** from the **Type of Certificate Needed** drop-down list, and then click **Submit**.  

   > [!NOTE]
   >  The client authentication certificate is used if you are running BizTalk Server on machine other than the Domain Controller. This will be configured in the adapter’s property dialog.  

4. Issue the certificates by using the Certification Authority management console as follows:  

   1.  Click **Start**, point to **Administrative Tools**, and then click **Certification Authority**.  

   2.  In the **Certification Authority** management console, expand your certification authority's name, and then double-click **Pending Request**.  

   3.  In the right pane of the **Certification Authority** management console, right-click the request for the service authentication certificate, point to **All Tasks**, and then click **Issue**.  

   4.  In the right pane of the **Certification Authority** management console, right-click the request for the client authentication certificate, point to **All Tasks**, and then click **Issue**.  

   5.  Close the **Certification Authority** management console.  

5. Install the issued certificates on your computer as follows:  

   1.  In Internet Explorer, visit the Web site `http://localhost/certsrv`.  

   2.  On the **Welcome** page, click **View the status of a pending certificate request**.  

   3.  On the **View the Status of a Pending Certificate Request** page, click the server authentication certificate.  

   4.  On the **Certificate Issued** page, click **Install this Certificate**.  

   5.  In Internet Explorer, visit the Web site `http://localhost/certsrv`.  

   6.  On the **Welcome** page, click **View the status of a pending certificate request**.  

   7.  On the **View the Status of a Pending Certificate Request** page, click the client authentication certificate.  

   8.  On the **Certificate Issued** page, click **Install this Certificate**.  

6. Make sure that the issued certificates are installed properly as follows:  

   1.  Open Microsoft Management Console (MMC). To do so, click **Start**, click **Run**, type `mmc`, and then click **OK**.  

   2.  In the MMC, on the **File** menu, click **Add/Remove Snap-in**.  

   3.  In the **Add/Remove Snap-in** dialog box, click **Add**.  

   4.  In the **Add Standalone Snap-in** dialog box, select **Certificates** from the **Available standalone snap-in** list, and then click **Add**.  

   5.  In the **Certificate snap-in** dialog box, select the **My user account** option, and then click **Finish**.  

   6.  Close all of the open dialog boxes.  

   7.  In the MMC, in the Console Root window, expand **Certificates - Current User**, expand **Personal**, expand **Certificates**, and then make sure that the certificates that you installed in the previous step are displayed.  

## Create the BizTalk application for this walkthrough  

1. Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **BizTalk Group**, right-click **Applications**, point to **New**, and then click **Application**.  

3. In the **Application Properties** dialog box, on the **General** tab, type `WcfMessageSecurity`, and then click **OK**.  

4. Create a receive location using the WCF-NetTcp adapter for the BizTalk application as follows:  

   1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **WcfMessageSecurity**, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**  

   2. In the **Receive Port Properties** dialog box, in the **Name** text box, type `WcfMessageSecurity.OrderRequest.Receive`, and then click **OK**. The name of this receive port is strictly arbitrary but this name makes logical sense.  

   3. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **Receive Locations**, click **New**, and then click **One-way Receive Location**. The [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] client will send a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] message to this receive location. Select the **WcfMessageSecurity.OrderRequest.Receive** recive port, and then click **OK**.  

   4. In the **Receive Location Properties** dialog box, in the **Name** text box, type `WcfMessageSecurity.OrderRequest.Receive.NetTcp`. The name of this receive location is strictly arbitrary but this name makes logical sense.  

   5. In the **Receive Location Properties** dialog box, in the **Transport** section next to **Type**, select **WCF-NetTcp** from the drop-down list, and then click **Configure**.  

   6. In the **WCF-NetTcp Transport Properties** dialog box, on the **General** tab, in the **Address (URI)** text box, type `net.tcp://localhost/WcfMessageSecurity`.  

   7. In the **WCF-NetTcp Transport Properties** dialog box, on the **Security** tab, select **Message** from the **Security mode** drop-down list, and then select **Certificate** from the **Message client credential type** drop-down list. This configures the WCF-NetTcp adapter to use the Message security mode.  

   8. Configure the service certificate to use with Message security mode. In the **WCF-NetTcp Transport Properties** dialog box, in the **Service certification** section, click **Browse**. In the **Select service certificate** dialog box, select the server authentication certificate you installed in the previous procedure, and then click **OK** to close the dialog box and save the changes.  

   9. Close all of the open dialog boxes.  

      > [!NOTE]
      >  To authenticate the client certificates with the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] receive adapters, the CA certificate chain for the client certificates must be installed in the Trusted Root Certification Authorities certificate store of the computer running the host instances for the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] adapters. Because this walkthrough assumes that the certificate service is installed on the same computer as the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] client and the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] adapters, you do not have to install the CA certificate chain on your computer.  

5. Create a FILE send port for the BizTalk application. This is the location where the order request output message will be sent by the orchestration representing the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  

   1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **WcfMessageSecurity**, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**  

   2. In the **Send Port Properties** dialog box, on the **General**  tab, in the **Name** text box, type `WcfMessageSecurity.OrderRequest.Send.FILE`.  

   3. In the **Send Port Properties** dialog box, in the **Transport** section next to **Type**, select **FILE** from the drop-down list, and then click **Configure**.  

   4. In the **FILE Transport Properties** dialog box, on the **General**  tab, type `C:\WCFMessageSecurity\OrderRequestOut` in the **Destination folder** text box, and then click **OK**.  

   5. In the **Send Port Properties** dialog box, on the **Filters** tab, select **BTS.ReceivePortName** for the **Property** field, enter `WcfMessageSecurity.OrderRequest.Receive` for the **Value** field, and then click **OK**. This filter expression routes the incoming [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] messages from the client into the **WcfMessageSecurity.OrderRequest.Receive** receive port to this send port.  

## Test the WCF client against the BizTalk application  

1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **WcfMessageSecurity**, and then click **Start**. In the **Start** dialog box, click **Start**.  

2. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand **Platform Settings**, expand **Host Instances**, right-click **BizTalkServerApplication** or another appropriate host instance, and then click **Restart**.  

3. Create a folder named **C:\WCFMessageSecurity** for the working folder for this walkthrough. Extract the walkthrough files to this folder.  

4. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the **WcfMessageSecurity.sln** file in the **C:\WCFMessageSecurity** folder.  

5. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, expand **WcfClient**, and then open **Program.cs** to review.  

   - The client sends a message to the WCF-NetTcp receive location that you created in the previous procedure.  

   - The client creates a channel with the **NetTcpBinding**, and then configures the binding to use certificates for the client credential type.  

   - The client configures the endpoint behavior to use the client authentication certificate that you installed in the previous procedure for the client authentication.  

   - The class, **Program**, implements the **IClientMessageInspector** and **IEndpointBehavior** interfaces to display outgoing [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] messages from this client at a command prompt.  

6. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click the **WcfMessageSecurity** solution, and then click **Rebuild**.  

7. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **Debug** menu, click **Start Without Debugging** to run the WcfClient to send a message to the WCF-NetTcp receive locations. A command prompt appears to show the execution result.  

   1. At the command prompt, review the order request message. Pay attention to the **OrderId** field and the structure of the message.  

   2. At the command prompt, go to the `C:\WCFMessageSecurity\OrderRequestOut` folder, and then make sure the order request message sent by the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] client appears.  

   3. Close the command prompt.
