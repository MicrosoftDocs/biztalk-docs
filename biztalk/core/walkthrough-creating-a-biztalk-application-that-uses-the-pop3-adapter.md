---
title: "Walkthrough: Creating a BizTalk Application That Uses the POP3 Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tutorials, POP3 adapters"
  - "configuring [POP3 adapters], mailboxes"
  - "configuring [POP3 adapters], tutorials"
  - "POP3 adapters, mailboxes"
  - "POP3 adapters, tutorials"
  - "configuring [POP3 adapters], Outlook Express"
ms.assetid: b44c3b1d-7b4f-425c-831a-1ce5f6379595
caps.latest.revision: 14
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Walkthrough: Creating a BizTalk Application That Uses the POP3 Adapter
This section takes you through creating a simple Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application using the POP3 adapter.  
  
> [!NOTE]
>  The application assumes that you have access to a computer running Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] with Email Services installed and configured. For information about configuring [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] with Email Services see Windows Server Help.  
> 
> [!NOTE]
>  In this example Microsoft Outlook Express is used as the e-mail client and [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] is used as the e-mail server. However, any POP3 e-mail client and RFC-compliant POP3 server could be used for this scenario.  
  
 This application assumes that you have not yet created any send ports or receive locations. If you have existing send ports or receive locations, substitute appropriate names when you work through the steps.  
  
 The application is a simple content-based routing application using only a receive location and a send port. The receive location reads from a mailbox on the server running [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]("the Windows server"\). The send port takes the message from the receive location and sends it to a folder on the local file system of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 To create the application, you have to create the mailbox, set up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location and send port, start the send port and enable the receive location, and send a test message to the mailbox. Follow the steps below to create the application.  
  
## Create a mailbox on Windows Server 2003  
 To create a mailbox on Windows Server 2003 with Email Services installed, follow these steps:  
  
1. Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **POP3 Service**.  
  
2. Expand *\<servername\>* and click the domain where you would like to create a mailbox.  
  
3. In the **POP3 Service** dialog box, in the right pane, click the **Add Mailbox** option.  
  
4. In the **Add Mailbox** dialog box, in the **Mailbox Name** box, type **EmailTest**.  
  
5. Select the **Create associated user for this mailbox** check box.  
  
6. In the **Password** and **Confirm Password** boxes, type a password, and then click **OK**.  
  
7. Make a note of the **Account name** and **Mail Server** log on information displayed for use with clear text authentication in the **POP3 Service** dialog box, and then click **OK**. This information will be used by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location that you configure with the POP3 transport type.  
  
## Create the receive location  
 Follow these steps to create the receive location:  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console double-click the default database **\<**<em>machine_name</em>**\>.BizTalkMgmtDb.dbo**, where *machine_name* is the name of your computer. Click **Applications**, then click **BizTalk.Application.1**.  
  
2. Right-click **Receive Ports**, click **New**, click **One-way receive port**.  
  
3. In the **Receive Port Properties** dialog box, in the **Name** box, type **POP3Receive**.  
  
4. Click **Receive Locations**, and then click **New**.  In the **Receive Location Properties** dialog box, in the **Name** box, type **POP3Receive**.  
  
5. In the **Transport Type** box, select **POP3**.  
  
6. In the **Receive Handler** box, select **BizTalkServerApplication**.  
  
7. In the **Receive Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.  
  
8. In the **Transport** box, click the **Configure** button.  
  
9. In the **POP3 Transport Properties** dialog box, in the **Apply MIME Decoding** box, select **False**.  
  
10. In the **Mail Server** box, type the name of the Windows Server-based server where you created a mailbox.  
  
11. In the **Authentication Scheme** box, select **Basic**.  
  
12. In the **Password** box, click the drop-down arrow and type the password for the mailbox.  
  
13. In the **User Name** box, type the fully qualified user name for the mailbox, for example <em>username@host.domain.toplevel_domain.</em>  
  
14. In the **Polling Interval** box, type **1**, click **OK**, and then click **OK** again.  
  
## Create the send port and destination folder on the BizTalk server  
 Follow these steps to create the send port and destination folder on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
1. Create a folder on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] file system. This will be the destination for the send port.  
  
2. Right-click **Send Ports**, click **New,** then click **Static one-way Send Port.**  
  
3. In the **Send Port Properties** dialog box, in the **Transport Type** box, select **FILE**.  
  
4. In the **Name** box, type **SendToFile**.  
  
5. In the **Transport** box, click the **Configure** button.  
  
6. Next to the **Destination folder** box, click **Browse**, select the folder that you created on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then click **OK**.  
  
7. In the **File name** box, type **%MessageID%.txt**, and then click **OK**.  
  
8. In the **Send Pipeline** box, select **Microsoft.BizTalk.DefaultPipelines.PassThruTransmit**.  
  
9. Click **Filters**.  
  
10. In the **Property** box, select **BTS.ReceivePortName**.  
  
11. In the **Value** box, type **POP3Receive**, and then click **OK**.  
  
## Enable the receive location and start the send port  
 Follow these steps to enable the receive location and start the send port:  
  
1. Right-click the **POP3Receive** receive location, and then click **Enable**.  
  
2. Right-click the **SendToFile** send port, and then click **Start**.  
  
   The next step is to test the application by sending a test message to the mailbox monitored by the receive location.  
  
## Configure Outlook Express to send an e-mail message to the mailbox  
 Follow these steps to configure Outlook Express to send an e-mail message to the mailbox:  
  
1.  Click **Start**, point to **Programs**, and then click **Outlook Express**.  
  
2.  In Outlook Express, on the **Tools** menu, click **Accounts**.  
  
3.  Click **Add** and then click **Mail**.  
  
4.  In the **Display name** box, type a display name, and then click **Next**.  
  
5.  In the **Internet E-mail address** dialog box, in the **E-mail address** box, type **EmailTest@<domain_name>**, and then click **Next**.  
  
     Make sure to enter the appropriate value for *<domain_name>*. This value should match the name of the domain under which this mailbox was created in the POP3 Service Administration interface on the Windows server.  
  
6.  In the **E-mail Server names** dialog box, in the **Incoming mail** and **Outgoing mail** boxes, type the server name or IP address of the Windows server, and then click **Next**.  
  
7.  In the **Internet Mail Logon** dialog box, in the **Account name** box, type **EmailTest**.  
  
8.  In the **Password** box, type the password for the EmailTest account, select the **Remember password** option, click **Next**, and then click **Finish**.  
  
9. Click to select the account that you just created, and then click **Properties**.  
  
10. In the **Properties** dialog box, click the **Advanced** tab, click to select the option to **Leave a copy of messages on the server**, and then click **OK**.  
  
11. In the **Internet Accounts** dialog box, click **Close**.  
  
12. Use Outlook Express to compose a test message, type **Test** into the **Subject** field, and type **EmailTest@<domain_name>** into the **To** field.  
  
13. Click **Send** to send the test message. To ensure that Outlook Express sends the test message immediately, click the **Send/Recv** button in the Outlook Express toolbar.  
  
## View the message  
 Follow these steps to view the message:  
  
1.  Use Windows Explorer to open the folder that you specified as the **Destination Folder** for the send port.  
  
2.  Double click the document in the folder to view the contents of the document in Notepad.  
  
## See Also  
 [What Is the POP3 Adapter?](../core/what-is-the-pop3-adapter.md)