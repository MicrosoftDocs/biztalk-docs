---
title: "Install BizTalk Accelerator for SWIFT | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "documentation"
ms.assetid: 8d492248-fde6-4fd8-be6b-e86ac7d0808b
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install BizTalk Accelerator for SWIFT
Install [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)] on BizTalk Server. 

\<!--- Previous text
- [Installation Guide for BizTalk Accelerator for SWIFT](http://go.microsoft.com/fwlink/?LinkId=198120)    
- [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Readme, located in the \Program Files\Microsoft BizTalk Accelerator for SWIFT \Documentation folder.  
  -->

## Hardware and software requirements

The minimum hardware and software requirements are the same as [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].


|                                                                                                                                                                   |                                                                                BizTalk requirements                                                                                 |                                                                                                                                                                                                                                                            SQL and OS requirements                                                                                                                                                                                                                                                            |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                       [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]                                                        |             [Hardware and Software Requirements for BizTalk Server 2016](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)             |                                      **SQL Server hardware and software requirements**: <br/>[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)<br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/><br/>**Windows Server hardware requirements**: <br/>[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/server-basics)<br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)                                      |
| [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] <br/><br/> [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] 2013 | [Hardware and Software Requirements for BizTalk Server 2013 and 2013 R2](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) | **SQL Server hardware and software requirements**: <br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/>[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)<br/>[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)<br/><br/>**Windows Server hardware requirements**: <br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)<br/>[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx) |

> [!TIP] 
> The hardware requirements listed are the minimum. Every environment is different and there's a very good chance that your environment may need more. See [Recommendations for Installing, Sizing, Deploying, and Maintaining a BizTalk Server Solution](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx). 

## Install SWIFT

### Before you begin

* Sign in using an account that is a member of the the BizTalk Server Administrators group. 
* In your BizTalk Server download, the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] setup is in the `\BizTalk Accelerators` folder.
* BizTalk Server must be installed, and SQL Server must be running.
* A silent installation is supported, but is not recommended due to the complexity of the additional configuration steps that are required.
* The A4SWIFT setup always runs with the `/InstallPlatform` argument. As a result, the setup always installs msvcr71.dll, mfc71u.dll, msvcp71.dll, and atl71.dll, which are required for Visual Studio. The setup installs these DLL files into the `%WINDIR%\System32` folder, whether the DLLs have been previously installed or not.

### Default installation

1. Run the [!INCLUDE[btaA4SWIFTNoVersion_md](../../includes/btaa4swiftnoversion-md.md)] **setup.exe** as Administrator.
2. Select **Install**.
3. Enter your **User name**, your **Organization**, and your product key. Select **Next**.
4. Read the licensing agreement, and then select **Accept**.
5. Select **Complete**, and then select **Next**.
6. Review the **Summary** page. To make any changes, select **Back**.

    To enable auto-logon after a system reboot, select **Set**, and enter the sign-in account. This is only enabled during the setup. When setup is complete, this setting is disabled.

    Select **Install**.

7. Select **Finish** when complete. A setup log file is generated in a temp folder, similar to: `C:\Users\username\AppData\Local\Setup(111016 xxxxxx).log`.

> [!NOTE]
> If **Run Configuration Wizard** is selected on the Installation Completed page, the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration Wizard runs automatically when you click **Finish**. 


### Custom installation

1. Run the [!INCLUDE[btaA4SWIFTNoVersion_md](../../includes/btaa4swiftnoversion-md.md)] **setup.exe** as Administrator.
2. Select **Install**.
3. Enter your **User name**, your **Organization**, and your product key. Select **Next**.
4. Read the licensing agreement, and then select **Accept**.
5. Select **Custom**, and then select **Next**.
6. Select your components, and then select **Next**:


   |                     Select this                      |                                                                      To do this                                                                      |
   |------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                  A4Swift components                  |                          Required to process (schema resolution, parsing, validation) of SWIFT messages with BizTalk Server                          |
   |          Message repair and reconciliation           |    Install pipelines, orchestrations, and runtime schemas. Creates the A4SWIFT database in SQL Server for messaging, repair, and reconciliation.     |
   | Web components for message repair and new submission | Installs the component for Message Repair and New Submission that create web services for validation, certificate security, history, and BIC lookup. |
   |            Software Development Kit (SDK)            |                                    Includes sample source code, toolkits, and starter projects for Visual Studio.                                    |
   |                BRE Deployment Utility                |               Utility for deploying Business Rule Engine (BRE) policies associated with SWIFT message types that are already deployed.               |
   |                       Tutorial                       |                                Iincludes instructions and samples for developing a SWIFT solution in BizTalk Server.                                 |
   |                        Tools                         |                                                       Includes tools for A4SWIFT development.                                                        |
   |                        Source                        |                                                 Installs sample source code for A4SWIFT development.                                                 |


7. Review the **Summary** page. To make any changes, select **Back**.

    Select **Install**.

8. Select **Finish** when complete. A setup log file is generated in a temp folder, similar to: `C:\Users\username\AppData\Local\Setup(111016 xxxxxx).log`.

> [!NOTE]
> If **Run Configuration Wizard** is selected on the Installation Completed page, the [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration Wizard runs automatically when you click **Finish**. 

## Next steps
[Configure BizTalk Accelerator for SWIFT ](../../adapters-and-accelerators/accelerator-swift/configure-biztalk-accelerator-for-swift.md)