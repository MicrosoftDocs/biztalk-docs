---
title: "Using the MQSAgent COM+ Configuration Wizard | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.mqsagent.wizard"
helpviewer_keywords: 
  - "MQSeries adapters, MQSAgent COM+ Configuration Wizard"
  - "configuring [MQSeries adapters], MQSAgent COM+ Configuration Wizard"
  - "MQSAgent COM+ Configuration Wizard"
ms.assetid: f106700a-7f57-4c83-9344-6525fc10544d
caps.latest.revision: 23
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Using the MQSAgent COM+ Configuration Wizard
The MQSAgent COM+ Configuration Wizard configures the MQSAgent, the COM+ application (MQSeries component) part of the adapter. The wizard sets the application identity of the component, and the role name and users included in the role. The name of the MQSAgent COM+ component created with the MQSAgent COM+ Configuration Wizard is **MQSAgent2**.  

> [!NOTE]
>  The MQSAgent COM+ application is supported on a 64-bit Windows server. It will run as a 32-bit process under WOW64. A [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-based computer that is running on a 64-bit version of Windows Server can communicate with a remote 32-bit computer that has the MQSAgent installed.  
> 
> [!NOTE]
>  The MQSeries Agent and the MQSAgent COM+ Configuration Wizard executable **MQSConfigWiz.exe** are not installed if you upgrade from BizTalk Server 2009 to BizTalk Server. After upgrading to BizTalk Server from BizTalk Server 2009 re-run setup, select the **Modify** option, and select the MQSeries Agent under the Additional Software to install these components.  

## To set the application identity  

-   Use the **Application Identity** page of the MQSAgent COM+ Configuration Wizard to set the application identity for the MQSAgent as follows:  

    |Use this|To do this|  
    |--------------|----------------|  
    |**Interactive User**|Select this option to use the current logon account for the application identity.|  
    |**Local Service**|Set the application identity to a built-in service account.|  
    |**Network Service**|Set the application identity to a built-in account with network access.|  
    |**This user**|Set the application identity to the indicated user name.|  

> [!NOTE]
>  It is not recommended that you use an account with administrative permissions for the application identity. The account must have the minimal rights required: read and write permission for the MQSeries queues.  

## To name the role and add users to it  

- Use the **Name of Role** page of the MQSAgent COM+ Configuration Wizard  to assign a name and users to the role as follows:  


  |     Use this     |                                                                         To do this                                                                          |
  |------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | **Name of role** |                                                                 Type the name of the role.                                                                  |
  |    **Users**     |                                                         Display the users that belong to the role.                                                          |
  |     **Add**      | Add users to the role. These are the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] service accounts using the adapter. |

> [!NOTE]
>  Add to the role only accounts requiring access to the adapter.  

## To set the MSDTC Security configuration on the Windows Server 2008 computer to No Authentication Required  
 If the MQSAgent COM+ application is installed on a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computer and the MQSeries Adapter (which is installed with BizTalk Server) is installed on a [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] computer, the MSDTC Security configuration on the [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] computer must be set to **No Authentication Required**. Follow these steps to set the MSDTC security configuration to No Authentication Required:  

1.  Click **Start** and then click **Control Panel**.  

2.  Double-click **Administrative Tools**.  

3.  Double-click **Component Services** to launch the **Component Services** management interface.  

4.  Expand **Component Services**, expand **Computers**, and then expand **My Computer**.  

5.  Right-click **My Computer** and click the **Properties** menu item.  

6.  In the **My Computer** dialog box, click the **MSDTC** tab and then click **Security Configuration**.  

7.  In the **Security Configuration** dialog box, in the **Transaction Manager Communication** section, select **No Authentication Required**. If you are prompted with a dialog box, click **Yes** to restart the MS DTC Service.  

8.  After the MS DTC service has restarted, click **OK** and click **OK** again to close the **My Computer** dialog box.  

9. Close the **Component Services** management interface.  

## To configure the MQSAgent runtime components to run under an alternative set of credentials  
 The MQSAgent COM+ application includes components for both administration and runtime. If you want to separate this functionality into different COM+ applications for security purposes, follow these steps on the computer that the MQSAgent COM+ application is installed on:  

1.  Enable changes for the MQSAgent COM+ component.  

    -   Click **Start** and then click **Control Panel**.  

    -   Double-click **Administrative Tools**.  

    -   Double-click **Component Services** to launch the **Component Services** management interface.  

    -   Expand **Component Services**, expand **My Computer**, expand **COM+ Applications**, right-click the **MQSAgent2** COM+ application and then click **Properties**.  

    -   Click the **Advanced** tab and uncheck **Disable changes**.  

    -   Click **OK**.  

2.  Create a new COM+ application for the MQSAgent runtime components.  

    -   Right-click **COM+ Applications**, click **New**, **Application** to display the **COM+ Application Install Wizard** and click **Next**.  

    -   Click **Create an empty application**.  

    -   Enter the name **MQSAgent2RunTime**, leave the default option for **Server application** enabled and click **Next**.  

    -   Select the option for **This user**, enter the appropriate account information and click **Next**.  

        > [!NOTE]
        >  This account should have **connect** and **put** and/or **get** permissions on the appropriate IBM WebSphere MQ for Windows queues. You can set the appropriate permissions for this account with the **setmqaut** command available with the IBM WebSphere MQ. For more information about the **setmqaut** command see the IBM WebSphere MQ documentation.  

    -   Click **Next** on the **Add Application Roles** dialog box.  

    -   Click **Next** on the **Add Users to Roles** dialog box.  

    -   Click **Finish**.  

3.  Move the runtime components to the new COM+ application  

    -   Expand the **MQSAgent2** COM+ application.  

    -   Expand **Components**.  

    -   Right-click the **MQSAgent2.MQSAgent.1** component and click **Move** to display the **Move components(s)** dialog box.  

    -   Select **MQSAgent2RunTime** under **Please select a destination** and click **OK**.  

    -   Repeat these steps for the **MQSAgent2.MQSBroker.1** and **MQSAgent2.MQSProxy.1** components.  

## See Also  
 [How to Configure MQSeries Adapter Send and Receive Handlers](../core/how-to-configure-mqseries-adapter-send-and-receive-handlers.md)   
 [Configuring the MQSeries Adapter](../core/configuring-the-mqseries-adapter.md)