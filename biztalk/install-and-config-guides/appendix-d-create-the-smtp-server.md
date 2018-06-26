---
title: "Appendix D: Create the SMTP Server | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7441ba9-a498-42ec-a04d-7f2731407373
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Appendix D: Create the SMTP Server
Create the SMTP Server used by SQL Server Database Mail.  
  
SQL Server Database Mail is required to configure BAM Alerts when using any of the following SQL versions: 

* [!INCLUDE[sqlserver2016_md](../includes/sqlserver2016-md.md)]
* [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)]
* [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] 
  
  SQL Server Database Mail uses an SMTP Server to send BAM Alerts. SMTP Server is included with Internet Information Services (IIS). SMTP can be installed locally on the BizTalk Server or on another server with IIS installed.  
  
> [!IMPORTANT]
>  Typically, client operating systems like Windows 10, Windows 7, and so on, do not include SMTP Server capabilities. You can connect to an existing SMTP Server on a Windows Server using the *SMTP E-mail* feature within IIS. The *SMTP E-mail* feature is NOT an SMTP Server, which is required for SQL Server Database Mail. As a result, this topic does not include the steps to install and configure an SMTP Server on client operating systems.  

## Install and configure the SMTP server  
  
These steps apply to:

* Windows Server 2016
* Windows Server 2012 R2
* Windows Server 2012
  
### Install SMTP Server  
   
1.  In **Server Manager**, select **Dashboard** in the left pane.  
  
3.  Select **Add roles and features**. **Add Roles and Features** can also be opened from the **Manage** menu in the top right-hand corner.  
  
4.  In **Before You Begin**, select **Next**.  
  
5.  Select **Role-based or feature-based installation**, and select **Next**.  
  
6.  Select **Select a server from the server pool**, select the desired server, and select **Next**. The **Server Selection** window lists the servers that have been added using **Add Server** in **Server Manager**. By default, it selects the local server.  
  
7.  In **Server Roles**, select **Next**.  
  
8.  In **Features**, check **SMTP Server**. If prompted, select **Add Features**. Select **Next**.  
  
9. In **Confirmation**, select **Restart the destination server automatically if required**, and select **Install**. When complete, select **Close**.  

### Configure the SMTP Server  
 The following steps configure the SMTP Virtual Server using the IIS 6.0 Manager:  
  
1.  Open the IIS Manager: In Start, search for **inetmgr6.exe**, and open it.  
  
2.  Expand the computer name. Right-click **[SMTP Virtual Server #1]**, and select **Properties**.  
  
3.  In the **Access** tab, select the **Relay** button.  
  
4.  Select **Add**. For **Single Computer**, enter `127.0.0.1`, and select **OK**.  
  
     By adding 127.0.0.1, we are allowing the local server to send messages from this SMTP Server. If you want additional computers to send messages from this SMTP server, enter their IP addresses.  
  
5.  In the **Delivery** tab, select **Outbound Security**. Choose from the following:  
  
     **Anonymous access**: An account name or password is not required. This option disables authentication for the SMTP Server.  
  
     **Basic authentication**: The account name and password of the server that you are connecting to are sent as clear text. This account you enter transmits the e-mails. Basic Authentication can be selected when sending e-mail to a personal account or an Exchange account. Because the credentials are passed in clear text, it is recommended to enable **TLS encryption**.  
  
     **Integrated Windows Authentication**: The Windows domain account name and password are used to authenticate. The account you enter transmits the e-mails.  
  
     **TLS encryption**: Similar to SSL, TLS secures the connection. Requires a valid SSL server certificate installed on this server.  
  
    > [!TIP]
    >  To test core SMTP functionality with a personal e-mail account, including an Exchange account, select **Anonymous access**. When Basic authentication is selected, SMTP uses the AUTH command. Some e-mail providers may fail because of the AUTH command. If the AUTH command fails, an error may be logged in the Windows event logs on the SMTP Server.  
  
6.  In the **Delivery** tab, select **Outbound connections**. By default, the TCP Port is 25. A different port can be entered if it is open within your firewall. Select **OK**.  
  
7.  In the **Delivery** tab, select **Advanced**. By default, the **Fully Qualified Domain Name** of the local server is listed. Depending on the internet provider, the **Smart Host** property can remain empty. You may need to contact the internet provider to confirm if a Smart Host is required. Otherwise, you may be able to enter smtp.*EMailProvider*.com.  
  
    > [!NOTE]
    >  A **Smart Host**, also known as a relay host, is a dedicated server used by an Exchange Server to route all outgoing messages. When the **Smart Host** receives the messages, the **Smart Host** forwards the messages to a remote domain. The goal of a **Smart Host** is to improve performance of an Exchange Server. The Exchange Server only transmits to the smart host; instead of repeatedly contacting the remote domain until a connection is made.  
  
8.  Select **OK** to close all windows.  
  
9. Restart the SMTP Server: Right-click **[SMTP Virtual Server #1]**, select **Stop**, and then select **Start**. A restart is needed to apply the SMTP Server settings. 

  
## Windows Server 2008 R2: Install and Configure SMTP Server  
  
### Install SMTP Server  
 The following steps install the SMTP Server feature:  
  
1.  In **Server Manager**, select **Features**, and select **Add Features**.  
  
3.  In **Add Features**, select **SMTP Server**. If prompted, select **Add Required Role Services**, and select **Next**.  
  
4.  Continue with the installation by selecting **Next**.  
  
5.  In the **Confirm Installation Selections** window, select **Install**. When complete, select **Close**.  
  
### Configure the SMTP Server  
 The following steps configure the SMTP Virtual Server using the IIS 6.0 Manager:  
  
1.  Open the IIS 6.0 Manager: In **Start**, search for **IIS**, and select **Internet Information Services (IIS) 6.0 Manager**.  
  
2.  Expand the computer name. Right-click **[SMTP Virtual Server #1]**, and select **Properties**.  
  
3.  In the **Access** tab, select the **Relay** button.  
  
4.  Select **Add**. For **Single Computer**, enter `127.0.0.1`, and select **OK**.  
  
     By adding 127.0.0.1, we are allowing the local server to send messages from this SMTP Server. If you want additional computers to send messages from this SMTP server, enter their IP addresses.  
  
5.  In the **Delivery** tab, select **Outbound Security**. Choose from the following:  
  
     **Anonymous access**: An account name or password is not required. This option disables authentication for the SMTP Server.  
  
     **Basic authentication**: The account name and password of the server that you are connecting to are sent as clear text. Basic Authentication can be selected when sending e-mail to a personal account or an Exchange account. Because the credentials are passed in clear text, it is recommended to enable **TLS encryption**.  
  
     **Integrated Windows Authentication**: The Windows domain account name and password are used to authenticate. The account you enter transmits the e-mails.  
  
     **TLS encryption**: Similar to SSL, TLS secures the connection. Requires a valid SSL server certificate installed on this server.  
  
    > [!TIP]
    >  To test core SMTP functionality with a personal e-mail account, including an Exchange account, select **Anonymous access**. When Basic authentication is selected, SMTP uses the AUTH command. Some e-mail providers may fail because of the AUTH command. If the AUTH command fails, an error may be logged in the Windows event logs on the SMTP Server.  
  
6.  In the **Delivery** tab, select **Outbound connections**. By default, the TCP Port is 25. A different port can be entered if it is open within your firewall. Select **OK**.  
  
    > [!TIP]
    >  The TCP Port can be used for Inbound connections and Outbound connections.  
  
7.  In the **Delivery** tab, select **Advanced**. By default, the **Fully Qualified Domain Name** of the local server is listed. Depending on the internet provider, the **Smart Host** property can remain empty. You may need to contact the internet provider to confirm if a Smart Host is required. Otherwise, you may be able to enter smtp.*EMailProvider*.com.  
  
    > [!NOTE]
    >  A **Smart Host**, also known as a relay host, is a dedicated server used by an Exchange Server to route all outgoing messages. When the **Smart Host** receives the messages, the **Smart Host** forwards the messages to a remote domain. The goal of a **Smart Host** is to improve performance of an Exchange Server. The Exchange Server only transmits to the smart host; instead of repeatedly contacting the remote domain until a connection is made.  
  
8.  Select **OK** to close all windows.  
  
9. A restart is needed to apply the SMTP Server settings. To restart the SMTP Server: Right-click **[SMTP Virtual Server #1]**, select **Stop**, and then select **Start**.  
  
  
## Test the SMTP Server  
 Telnet can be used to test the SMTP Server configuration. The following steps send a message using your configured SMTP Server to an e-mail address. [http://support.microsoft.com/kb/153119](http://support.microsoft.com/kb/153119) provides descriptions of the telnet commands.  
  
1. Open a command window as Administrator.
  
2. In the command prompt, type:  
  
    `telnet localhost 25`  
  
    If telnet is not installed, install it by typing:  
  
    `pkgmgr /iu:"TelnetClient"`  
  
3. Start communication by typing:  
  
    `EHLO server`  
  
4. Enter the Mail From address:  
  
    `MAIL FROM: *YourEmailAddress*@*YourProvider*.com`  
  
    For example, enter:  
  
    `MAIL FROM: EmailAddress@outlook.com`  
  
5. Enter the Mail To address:  
  
    `RCPT TO: *YourEmailAddress*@*YourProvider*.com`  
  
    For example, enter:  
  
    `RCPT TO: EmailAddress@outlook.com`  
  
6. Tell the SMTP Server you are ready to send data by typing:  
  
    `DATA`  
  
7. Enter the Subject by typing:  
  
    `Subject: Test Message`  
  
8. Hit Enter twice.  
  
9. Enter the message body by typing:  
  
     `This is the message body of the test message.`  
  
10. Hit Enter, type a period (.), and hit Enter.  
  
    Check the RCPT TO address for the e-mail message. If the e-mail is not delivered (Check your Inbox and Spam folder), then the message was not successfully sent, and may reside in the SMTP Queue folder (C:\inetpub\mailroot\Queue).  
  