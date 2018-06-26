---
title: "Configure the FileAct and InterAct Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d3876ff-e8e4-47f4-9ca8-d4dad419ed67
caps.latest.revision: 20
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the FileAct and InterAct Adapter
Configure the different artifacts used by the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] runtime. 

  
## Prerequisites  
   
- Install the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]
  
- Sign in as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators group
  
- Confirm SQL Server is running
  
## Step 1: Configure the FileAct and InterAct adapter  
  
1.  In the **Microsoft BizTalk FileAct and InterAct Adapter Configuration** wizard, go to **Overview**. In the left pane, select **Runtime** to configure the runtime components of the adapters.  
  
2.  In **Runtime Configuration**, under **Account**, select the ellipsis […] to enter the COM plus configuration for the Store and Forward mode.  
  
3.  In **User Credentials**, enter the user name (in the *domain\user name* format) and password for the account used in the COM plus configuration. Select **OK**.  
  
    > [!NOTE]
    >  A **User Credentials** warning appears if the account you entered has higher privileges than are recommended. Select **Yes** to continue.
  
4.  Select **Apply configuration** to apply the COM plus configuration to the FileAct and InterAct Adapter.  
  
5.  In the **Summary**, review, and select **Next**.  
  
6.  When the configuration completes, review the list of components. A check mark means that the component is configured successfully. An "X" means that there is a problem with that component.  
  
    > [!NOTE]
    >  Use the **Logfile** link to view the configuration events.  
  
7.  Select **Finish** to complete the configuration. The **Overview** shows the current configuration status for the Runtime components.  

Next, create the host and host instances to run these adapters.

## Step 2: Create the host and host instances

We recommend that you create a dedicated host for the FileAct adapter and a separate dedicated host for the InterAct adapter. For each adapter, create at least one host instance.  

[Managing BizTalk Hosts and Host Instances](../../core/managing-biztalk-hosts-and-host-instances.md) list the steps to create hosts and host instances. 

Once created, the next step is to add the send handler, and use the Client Message Partner you created in the SWIFT Alliance Gateway (SAG).

## Step 3: Create the send handler

You use the FileAct and InterAct send handler properties as the send port configuration values, if the properties are not set on the individual FileAct or InterAct send port. 
  
1. In the **BizTalk Server Administration** console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.  
  
2. Select the **FileAct** or **InterAct** adapter. In the right pane, double-click the send handler.  
  
3. In the **Host name** drop-down list, select the host you created in the previous section. Then select **Properties**.  
  
4. In the **Transport Properties**, select the **Argument** property, and enter the following argument as:  
  
    `-SagMessagePartner <Client Message Partner created in SAG\>`
  
   > [!NOTE]
   >  Replace <`Client Message Partner created in SAG`> with the name of the client message partner. Leave the default values for the Crypto Mode, FACrypto Mode, and LogMessages properties.  
  
5. Select **OK** to save your changes, and then to close the properties window. 
  
6. Under **Platform Settings**, select **Host Instances**.  
  
7. Restart the host instances: 

   - Right-click the FileAct host instance, and **Restart**
   - Right-click the InterAct host instance, and **Restart**.  

Next, enter the server message partners in the SWIFTNet paramfile to enable the FileAct and InterAct receive adapters.
  
## Step 4: Configure the SWIFTNet param file

To enable the FileAct and InterAct receive adapters to initialize with the values, the Server message partners created in SAG must be entered in the SWIFTNet paramfile. The paramfile is typically located in `c:\SWIFTAlliance\RA\<remote access instance name\>\cfg\paramfile`. After you configure the paramfile, start **SnlReceiver.exe**.  
  
1. Open the **SWIFTNet paramfile**. In the location marked with "***" add the following. Note that the `AdapterType` value can be `Interact` or `Fileact`.  
  
     ```spawn "snlreceiver -SagMessagePartner <Server MessagePartnerName\> -AdapterMode <AdapterType\>"```  
       
  
   ```  
    username:snlowner  
    subsystem_name:SampleSubsystem  
    #subsystem_group: SampleSubsystem  
    #subsystem_dependency:Support,Swarm  
    subsystem_nature:critical  
    subsystem_start:  
    ***  
    *END  
    subsystem_stop:  
    *KILL9:snlreceiver  
    *END  
    subsystem_status:  
    *NB:1:snlreceiver  
    *END  
    start_event:SNL001:subsystem SampleSubsystem is up  
    stop_event:SNL002:subsystem SampleSubsystem is down  
   ```  
  
> [!NOTE]
>  Before you start SNLreceiver, enable the receive ports for the adapter you are using (FileAct or InterAct).  
  
2. Start and stop SnlReceiver.exe:

    1.  On the desktop, select the **Remote API** icon to open the Remote API command prompt.  
  
    2.  At the command prompt, type `Swiftnet start`. Select ENTER to start SnlReceiver.exe.  
  
    3.  At the command prompt, type `Swiftnet stop`. Select ENTER to stop SnlReceiver.exe.  

  
Next, update the file **autoexec.bat** to set the SWIFT environment variables.

## Step 5: Update autoexec.bat to configure the receive adapters

Update the **autoexec.bat** file to set the SWIFT environment variables on the computer where you installed the [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] receive adapters. The environment variables are generated from the system that has the receive adapter installed in the path `c:\SWIFTAlliance` with an instance of the receive adapter named **Ra1**. Update the SWIFT environment variables appropriately for your configuration.  
  
 The following is a sample of the autoexe.bat file:
  
```  
SET COMPUTERNAME=<Machine Name>  
SET GENLOG_DIR=C:\SWIFTAlliance\RA\Ra1\log  
SET GENUTIL_DIR=C:\SWIFTAlliance\RA\bin  
SET HOMEDRIVE=C:  
SET LOGONSERVER=\\SERVERNAME  
SET OSA_DIR=C:\SWIFTAlliance\RA\Ra1\log  
SET OSA_INSTANCE=Ra1  
SET PKIEXECDIR=C:\SWIFTAlliance\RA  
SET SAGRA_HOME=C:\SWIFTAlliance\RA  
SET SESSIONNAME=RDP-Tcp#1  
SET SLP_ENV=DEFAULT  
SET SLP_FILE=server.slp  
SET SNL_DOMAIN_NAME=Ra1  
SET SPK_DATA_DIR=C:\SWIFTAlliance\RA\data\pki  
SET SWNET_BIN_PATH=C:\SWIFTAlliance\RA\Ra1\bin  
SET SWNET_CFG_PATH=C:\SWIFTAlliance\RA\Ra1\cfg  
SET SWNET_HOME=C:\SWIFTAlliance\RA  
SET SWNET_HOST=HOSTNAME  
SET SWNET_INST=Ra1  
SET SWNET_LOG_PATH=C:\SWIFTAlliance\RA\Ra1\log  
SET SWNET_SLP_PATH=C:\SWIFTAlliance\RA\data\  
SET SWNET_VERSION=5.0.20  
SET SWTRACE=C:\SWIFTAlliance\RA\Ra1\log  
SET Path=%PATH%;C:\SWIFTAlliance\RA\bin  
SET Path=%PATH%;C:\SWIFTAlliance\RA\lib  
  
```  
  
## See some examples
For examples of FileAct and InterAct messages, see [Sample InterAct and FileAct Messages](../../adapters-and-accelerators/fileact-interact/sample-interact-and-fileact-messages.md).  
  
## See Also  

[Install the FileAct and InterAct Adapter](../../adapters-and-accelerators/fileact-interact/install-the-fileact-and-interact-adapter.md)  
[Uninstall or repair the FileAct and InterAct adapter](../../adapters-and-accelerators/fileact-interact/uninstall-or-repair-the-fileact-and-interact-adapter.md)  
[Read the installation known issues](../../adapters-and-accelerators/fileact-interact/read-the-installation-known-issues.md)
