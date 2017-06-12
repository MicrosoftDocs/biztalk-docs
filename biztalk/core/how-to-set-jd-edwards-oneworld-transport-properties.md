---
title: "How to Set JD Edwards OneWorld Transport Properties | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "setting transport properties"
  - "transport properties, setting"
ms.assetid: 6d38088b-a496-414e-aae6-d28c5d6398b6
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Set JD Edwards OneWorld Transport Properties
The JD Edwards OneWorld Transport Property System Definition is used for design and run-time logon. You set these credentials to browse JD Edwards OneWorld business functions at design time and make calls at run time.  
  
 When a connection is made to JD Edwards OneWorld, parameters are passed to the connection object (User, Password, Environment). It returns an instance of the JD Edwards OneWorld aApplication business function. The credentials are further defined by the name of the enterprise/application server, and the defined TCP/IP port on which the service listens.  
  
 The enterprise server name and port are read from a file that is named jdeinterop.ini. These values must be the same as those that are in the System Definition settings.  
  
> [!NOTE]
>  All entries are case sensitive.  
  
## Setting Properties  
 In the **Transport Properties** dialog box, you set the connection and credential parameters that are specific to the server system and the objects you are trying to access.  
  
 The steps in this process are as follows:  
  
#### To set transport properties  
  
1.  Provide credentials.  
  
     You can access the JD Edwards OneWorld system using one of the following methods:  
  
    -   Logon credentials (Password, User name): If you use this method, go to step 5.  
  
    -   Single Sign-On.  
  
2.  To use Single Sign-On (SSO), select **Yes** in the **Use SSO**.  
  
     For more information about how to set up SSO, see [Using Single Sign-On](../core/using-single-sign-on3.md).  
  
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
  
### Adapter Required Properties  
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
  
## See Also  
 [Creating JD Edwards OneWorld Send Handlers](../core/creating-jd-edwards-oneworld-send-handlers.md)