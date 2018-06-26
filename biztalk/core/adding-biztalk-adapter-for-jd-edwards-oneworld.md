---
title: "Add BizTalk Adapter for JD Edwards OneWorld | Microsoft Docs"
description: Add the JD Edwards OneWorld to BizTalk Administration, create the send port, configure the transport properties, and use the XMLReceive and XMLTransmit pipelines when using JD Edwards OneWorld adapter in BizTalk Server
ms.custom: ""
ms.date: "10/18/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03126f4e-9156-4c0c-ab5c-0627f0c05263
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure JD Edwards EnterpriseOne artifacts in BizTalk Administration
Microsoft BizTalk Adapter for JD Edwards OneWorld contains both the Receive Handler and Send Handler folders. The Send Handler folder contains BizTalkServerApplication. BizTalk Adapter for JD Edwards OneWorld is creatable; it runs in-process with BizTalk Server and does not run in an isolated host process.  

## Add the adapter to BizTalk Administration 

1.  Open **BizTalk Server Administration**, expand **BizTalk Server Administration**, expand **BizTalk Group**, and then expand **Platform Settings**.  
  
2.  Right-click **Adapters**, select **New**, and select **Adapter**.  
  
3.  Enter a name for the adapter. For example, enter`JDEOneWorld`.  
  
4.  Select **JDEOneWorld** from the **Adapter** list, and select **OK**.  

  
### Check if the adapter is working 
 In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, you can verify that the adapter is functioning correctly by looking at the **Logical System** window. On initial installation, this window is empty because you have not yet established a connection to the server system, nor have you created any logical systems.  
  
 
1. In **BizTalk Server Administration**, expand **Platform Settings**, expand **Adapters**, and then select **JDEOneWorld**.  
  
2. In the details pane, right-click **BizTalkServerApplication**, and select **Properties**.  
  
3. Select the **Properties** tab.  
  
4. Set the SQL Connection parameters.  
  
   -   **Define SQL Database Parameters -** The SQL Server Name and Database are those you set at installation. This is the text area that you can redefine the server and database for this adapter.  
  
5. Select **Close** to exit the **Logical System** window.  
  
    Your next step is to add a logical system using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  

## Create the send port  
  
1.  In **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand your application.  
  
2.  Right-click **Send Ports**, select **New**, and then select **Static Solicit-Response Send Port**.  
  
    > [!NOTE]
    >  You can also use **Static One-Way Port**.  
  
3.  In the **Send Port Properties**, select the **Name** field, and enter a send port name. For example, enter **SendToJDE**.  
  
4.  In the **Type** drop-down list, select **JDEOneWorld**.  
  
5.  In the **URI** drop-down list, select the send handler.  
  
6.  Select **OK**. 

## Configure the transport properties
The JD Edwards OneWorld Transport Property System Definition is used for design and run-time logon. You set these credentials to browse JD Edwards OneWorld business functions at design time and make calls at run time.  
  
 When a connection is made to JD Edwards OneWorld, parameters are passed to the connection object (User, Password, Environment). It returns an instance of the JD Edwards OneWorld aApplication business function. The credentials are further defined by the name of the enterprise/application server, and the defined TCP/IP port on which the service listens.  
  
 The enterprise server name and port are read from a file that is named jdeinterop.ini. These values must be the same as those that are in the System Definition settings.  
  
> [!NOTE]
>  All entries are case sensitive.  
  
### Set the properties  
 In the **Transport Properties** dialog box, you set the connection and credential parameters that are specific to the server system and the objects you are trying to access.  
  
1.  Provide credentials. You can access the JD Edwards OneWorld system using one of the following methods:  
  
    -   Logon credentials (Password, User name): If you use this method, go to step 5.  
  
    -   Single Sign-On.  
  
2.  To use Single Sign-On (SSO), select **Yes** in the **Use SSO**.  
  
     For more information about how to set up SSO, see [Security in the adapter](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)  
  
3.  Select an affiliate application in the list.  
  
     An affiliate application, created by Enterprise Single Sign-On tools, represents an application such as JD Edwards OneWorld. Microsoft BizTalk Adapter for JD Edwards OneWorld uses the credentials of an application user. These credentials are retrieved from the SSO Credentials database for the server system for a specified affiliate application. The credentials are those of the application user who launched the BizTalk Server project.  
  
     For more information, see [Creating Affiliate Applications](../core/creating-affiliate-applications3.md).  
  
4.  Expand the **JD Edwards OneWorld system** node and enter all required information for connection to the JD Edwards OneWorld server.  
  
     ![](../core/media/jdedadapter-02-jdesystem.gif "JDEdAdapter_02_JDESystem")  
  
     After you set the connection parameters, you can browse a JD Edwards OneWorld system. For more information, see [Importing JD Edwards OneWorld Schemas into BizTalk Server Projects](../core/importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md).  
  
5.  Enter a value representing the number of calls, for example 200, in **Max Concurrent Calls** if it is required.  
  
     The `Max Concurrent Calls` parameter lets you optimize your configuration. You use this parameter in instances where the throughput exceeds back-end processing capabilities, to activate message-overload protection. The default is -1, which means that the calls are unlimited.  
  
     When BizTalk Server submits messages to the transmit adapter, it first receives a batch from the adapter. It invokes `TransmitMessage` on the batch to transmit each message. When done, BizTalk Server invokes `Done` on the batch, and the adapter starts transmitting the messages to the back-end. If BizTalk Server obtains multiple batches before invoking `Done`, it might never occur. By setting the maximum number of messages in a batch, you can control messages to the back-end.  
  
     Changing this parameter takes effect within one minute; BizTalk Server must retrieve the changes to the adapter configuration saved in the SQL database.  
  
6.  Select **Yes** for **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.  
  
     For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Microsoft Adapter Wizard for selection.  
  
    > [!NOTE]
    >  The browsingagent.exe does not refresh until you exit the current browsing session. For example, you must exit the **Add generated item** browsing session and reenter to update the browsingagent.exe.  
  
7.  After providing all required information, click **Apply**, and then click **OK** to accept the connection information.  
  
     You must set connection parameters for BizTalk Adapter for JD Edwards OneWorld to access JD Edwards OneWorld.  
  
### Adapter required properties  
 If you did not set global environment variables in Control Panel, you can do so in this section.  
  
|Parameter|Description|  
|---------------|-----------------|  
|`Host`|Type the name of the host server computer name (for example, `actsvr1`); or the IP address of the computer (for example, `123.456.0.789`).|  
|JAVA_HOME|Type the complete path of your JDK installation.|  
|JDE Edwards Environment|Type the name of an environment in JD Edwards OneWorld, for example, `DV7333`.<br /><br /> DV7333 is a common name for the development environment, PY7333 is common for the prototype environment, and PD7333 is common for the production environment.|  
|JDEdwards JAR Files|Enter the complete path and file name for each JAR file:<br /><br /> -   Connector.jar<br />-   Kernel.jar<br />-   JDEJAccess.jar<br />-   JDEActionalInterop.jar<br /><br /> Each jar file must be separated with a semi-colon (;) and no space. For example:<br /><br /> `<drive>\Connector.jar;<drive>\Kernel.jar;`|  
|Password|Type the password of the specified user.|  
|Port|Type the port number that will exchange data (for example, `6009`).|  
|User Name|Type a JD Edwards OneWorld user name that will be used to log on to the JD Edwards OneWorld system.|  

## Use the XMLTransmit and XMLReceive pipelines
Microsoft BizTalk Adapter for JD Edwards OneWorld requires that you select XMLTransmit and XMLReceive for the send and receive pipelines.  
  
1.  In **BizTalk Server Administration**, expand **Applications**, and then expand your application.  
  
2.  Select **Send Ports**, right-click your send port, and select **Properties**.  
  
3.  In the **Send Ports Properties**, do the following:  
  
    1.  Select the send pipeline from the **Send Pipeline** drop-down list.  
  
    2.  Select the Receive pipeline from the **Receive Pipeline** drop-down list.  
  
4.  Select **OK**.  

## Next steps
[Import adapter schemas into Visual Studio](importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects.md)  
[Use Message Context Properties](using-message-context-properties2.md)