---
title: "Install the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41b9b34b-3fbb-480f-a335-a218eab33693
caps.latest.revision: 40
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install the WCF LOB Adapter SDK
Install and configure the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]. 

## Requirements 
Install following components on the system where you install the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. 

> [!NOTE]
> **For a list of the supported versions**, see: 
> 
> [Hardware and Software Requirements for BizTalk Server 2016](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
> [Hardware and Software Requirements for BizTalk Server 2013 and 2013 R2](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)

|                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                         Windows                                          | x86 or x64 <br/><br/>Required OS resources include:<br/> <ul><li>Microsoft Distributed Transaction Coordinator (MSDTC) : Required to support OleTx transactions</li><li>Message Queuing (MSMQ) : Required to support reliable messaging</li><li>Internet Information Services (IIS) : Required if you want to host your application in IIS</li><li>Windows Process Activation Service (WAS) : Required if you want to host your application in WAS</li></ul> |
|                             Windows Communication Foundation                             |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|        [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)]        |                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|       [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]       |                                                                                                                                     Required if you are building custom adapters, or developing solutions that use the adapters built with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].                                                                                                                                      |
| [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] |                                                                                                                                                                 Required if you use the adapters with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].                                                                                                                                                                 |

## Install

> [!IMPORTANT]
> * Close all instances of Visual Studio
> * To do a **Complete** setup, confirm that BizTalk Server is installed on the computer.  

1. Run the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] **Setup.exe** as Administrator.

2. Select **Install Microsoft BizTalk Adapters**, and then select **Install Microsoft WCF LOB Adapter SDK**.  

3. On the **Welcome** screen, select **Next**.  

4. Accept the license agreement, and select **Next**.  

5. In **Choose Setup Type**, select the type of installation:  

   -   To install the common run time and tools, select **Typical**.  

   -   To select the features that you want to install and the installation location, select **Custom**, and then select the features you want to install.  

   -   To install all the features, select **Complete**.  

6. Select **Install**.  

## Update or remove

1. Open **Programs and Feature**. 

2. In the list, select **Windows Communication Foundation LOB Adapter SDK**, and then select **Change**.  

3. On the **Welcome** screen, select **Next**.  

4. Do one of the following:  

   - To select the components that you want to install, select **Change**.  

   - To repair errors in the most recent installation, select **Repair**.  

   - To remove the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] from the computer, select **Remove**.  

5. If you choose to modify the installation:  

   1.  Select **Next**.  

   2.  Select **Change**, and then select **Finish**.  

6. If you choose to repair the installation, in the **Ready to repair WCF LOB Adapter SDK** dialog box, select **Repair**, and then select **Finish**.  

7. If you choose to remove the adapters, in the **Ready to remove WCF LOB Adapter SDK** dialog box, select **Remove**, and then select **Finish**.  


#### Remove custom adapters after uninstalling the WCF LOB Adapter SDK  

 If you have developed any custom adapters using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], and you have registered these adapters on your computer, you must also complete the following procedure.  

1.  Remove the custom adapter from the global assembly cache (GAC).  

    1.  Open a **Visual Studio command prompt**.  

    2.  Remove the custom **adapter .dll** from the GAC using **command gacutil /u**.  

2.  Remove the references to the custom adapter binding from machine.config  

    1.  Go to the machine.config file under \<*system drive*\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.  

    2.  Open the file by using a text editor.  

    3.  Search for the element bindingExtensions, client and bindingElementExtensions under system.serviceModel\extensions.  

    4.  Remove the WCF binding that pertains to your custom adapter.  

## Do a silent installation  
 A silent installation is ideal for test scenarios or as part of a large-scale enterprise deployment. [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] provides command line parameters that you can use with AdapterFramework.msi to perform a silent installation.  

> [!NOTE]
>  To perform silent installation, you should be an Administrator on the computer. 


1. Open a command prompt as administrator.  

2. Type the following:

   ```  
   AdapterFramework.msi /quiet MUOPTIN=”Yes”  
   ```  

   Use the following command line options in conjunction with AdapterFramework.msi:  

   * Use `/quiet` to install [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] silently.  

   * Use MUOPTIN=”Yes”&#124;”No” to indicate if the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] should check for updates with Microsoft Update.  

       When set to Yes, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] checks for updates through Microsoft Update. When set to no [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] does not check for updates with Microsoft Update.  

> [!NOTE]
>  To display additional options for command line installation, type `AdapterFramework.msi /?`at the command prompt.  

