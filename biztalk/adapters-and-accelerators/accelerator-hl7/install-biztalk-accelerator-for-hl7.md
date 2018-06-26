---
title: "Install BizTalk Accelerator for HL7 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 52347742-f858-47bb-bc73-1a6095ea9e8e
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install BizTalk Accelerator for HL7

## Hardware and software requirements

The minimum hardware and software requirements are the same as [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]. 


|                                                                                                                                                                   |                                                                                BizTalk requirements                                                                                 |                                                                                                                                                                                                                                                            SQL and OS requirements                                                                                                                                                                                                                                                            |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                       [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]                                                        |             [Hardware and Software Requirements for BizTalk Server 2016](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)             |                                      **SQL Server hardware and software requirements**: <br/>[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)<br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/><br/>**Windows Server hardware requirements**: <br/>[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/server-basics)<br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)                                      |
| [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] <br/><br/> [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] 2013 | [Hardware and Software Requirements for BizTalk Server 2013 and 2013 R2](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) | **SQL Server hardware and software requirements**: <br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/>[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)<br/>[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)<br/><br/>**Windows Server hardware requirements**: <br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)<br/>[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx) |

> [!TIP]
> The hardware requirements listed are the minimum. Every environment is different and there's a very good chance that your environment may need more. See [Recommendations for Installing, Sizing, Deploying, and Maintaining a BizTalk Server Solution](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx)

## Install HL7

### Before you begin

* The HL7 accelerator install files are in `BizTalk Server <version>\BizTalk Accelerators` on the [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] ISO, download location, network share, or wherever you downloaded the [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] program.
* The user installing and configuring [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] must be a member of the BizTalk Administrators group, and a member of the Administrators group on the SQL Server where the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] data is stored.
* The computer and signed-in user must have access to the primary domain controller (PDC). If the setup fails to access the PDC, then the installation fails, and won’t continue.  
* BizTalk Server should have the basic components installed and configured, including a 32-bit BizTalkServerApplication host with standard out of the box adapters, Enterprise Single Sign-on (SSO), the Group, and Runtime.
* Read the [installation known issues](../../adapters-and-accelerators/accelerator-hl7/installation-known-issues.md).
* [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] is available in Enterprise and Standard Editions. The following table shows the compatibility between the different editions of [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  


  | [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] edition | Compatible edition of [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] |
  |-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
  |                                      Enterprise Edition                                       |                                     Enterprise Edition                                      |
  |                                       Standard Edition                                        |                               Enterprise or Standard Edition                                |
  |                                       Developer Edition                                       |                                     Enterprise Edition                                      |

### Default installation

1. Run the [!INCLUDE[btaBTAHL7NoNumber_md](../../includes/btabtahl7nonumber-md.md)] (A4HL7) **setup.exe** as Administrator. 

   > [!TIP]
   >  Starting with [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)] and newer versions, the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] installation includes a 32-bit installation package and a 64-bit installation package.
   > 
   > On a 32-bit computer, install only the 32-bit package. On a 64-bit computer, install the 32-bit **or** 64-bit package. The 64-bit package enables the adapter and pipelines to run in both 32-bit and 64-bit mode.  

2. On the welcome page, select **Next**.  

3. Accept the **License Agreement**, and then select **Next**.  

4. Enter your user name and organization, and then select **Next**.  

5. Select the **Typical** setup, and then select **Next**.  

6. The **Logging Service Account** page automatically gives the following groups the logging permissions: 

   * BizTalk Server Administrators
   * BizTalk Application Users
   * BizTalk Server B2B Operators
   * BizTalk Server Operators

   Select **Next**. 

7. Review the summary, and select **Next**.  

8. For the **Destination Folder**, select **Next** to use the default folder. Or, select **Change** to choose a different installation folder. 

9. In **Logging Database Information**, enter the following, and then select **Next**.  


   |         Use this         |                                                                                                                                                                                                                   To do this                                                                                                                                                                                                                   |
   |--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Database Server Name** |                                                                                                                             The default value is the server name. <br/><br/>**Note**  The server name defaults to the name of the computer that the BizTalkMgmtDb database resides. You cannot change this value.                                                                                                                              |
   |  **HL7 Database name**   | Enter the name of the database that contains the data for your [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] solution, or accept the default setting, which is **BTAHL7**. <br/><br/>**Note**  You must use the ANSI-ASCII character set per database requirements; [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] does not support other character sets. |
   |   **Test connection**    |                                                                                                                                                                                              Select to confirm you have SQL Server connectivity.                                                                                                                                                                                               |

    > [!NOTE]
    >  If the database selected already exists, then a message box appears. Select **OK** to continue.  

10. Select **Install**.

11. Select **Finish** when completed.  

    > [!TIP] 
    > Select **Launch Tutorial** to install the End-To-End Tutorial. 

### Custom installation
1. Run the [!INCLUDE[btaBTAHL7NoNumber_md](../../includes/btabtahl7nonumber-md.md)] (A4HL7) **setup.exe** as Administrator. 

   > [!TIP]
   >  Starting with [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)] and newer versions, the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] installation includes a 32-bit installation package and a 64-bit installation package. 
   > 
   > On a 32-bit computer, install only the 32-bit package. On a 64-bit computer, install the 32-bit **or** 64-bit package. The 64-bit package enables the adapter and pipelines to run in both 32-bit and 64-bit mode.  

2. On the welcome page, select **Next**.  

3. Accept the **License Agreement**, and then select **Next**.  

4. Enter your user name and password, and then select **Next**.  

5. Select **Custom**, and then select **Next**.  

6. Select the features that you want to install, and then select **Next**.  


   |       Feature        |      Sub-feature       |                                                                                                   Description                                                                                                    | Typical Install | Custom Install |
   |----------------------|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|----------------|
   |      **Engine**      |                        |                                 Validates, processes, and routes messages.<br /><br /> You must be a member of the BizTalk Server Administrators group to install this feature.                                  |        ✓        |       ✓        |
   |      **Engine**      |   Engine Components    |                                      Processes [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] flat file and XML-encoded messages.                                      |        ✓        |       ✓        |
   |      **Engine**      |   Outbound Batching    |                                       Creates and routes [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] batch format documents.                                        |        ✓        |       ✓        |
   |      **Engine**      |       Pipelines        |                                      Sample pipelines for building your [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] solution.                                       |        ✓        |       ✓        |
   |     **Adapter**      |                        |                                                                                    Utilities to enable end-point connections.                                                                                    |        ✓        |       ✓        |
   |     **Adapter**      |          MLLP          |                          MLLP adapter to enable TCP/IP-based connections using [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] MLLP protocol.                           |        ✓        |       ✓        |
   |     **Adapter**      |     MLLP Test Tool     |                                                   Test tool that emulates MLLP-based sending and receiving client applications over TCP/IP-based connections.                                                    |                 |                |
   |     **Schemas**      |                        |                                                                                Selection of HL7 V2.X flat file based XSD schemas.                                                                                |        ✓        |       ✓        |
   |    **Artifacts**     |                        |                                             Tools for working with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] artifacts.                                              |                 |       ✓        |
   |    **Artifacts**     |     Orchestration      |                               A sample orchestration you can use to build your [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] solution.                                |                 |       ✓        |
   | **Other Components** |     Test Instances     |                           Sample/test data you can use as a starting point for your [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] solution.                           |                 |                |
   | **Other Components** |           -            |                                                  Other components in [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)].                                                   |        ✓        |       ✓        |
   | **Other Components** | Configuration Explorer |                           Application you use to define your logging for data stores, configure party-specific validation, header mapping, batching, and acknowledgment requirements.                            |        ✓        |       ✓        |
   | **Other Components** |          SDK           |                                    Contains utilities for HL7 2.XML schemas, such as the components and artifacts needed for the End-to-End Tutorial and the MLLP utilities.                                     |        ✓        |       ✓        |
   | **Other Components** |   Logging Framework    |                                       Components that support logging of [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] events.                                        |        ✓        |       ✓        |
   | **Other Components** |    Starter project     | Plug-in for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] that enables [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] project development. |        ✓        |       ✓        |


7. In **Logging Service Account**, enter the following, and then select **Next**.  


   |     Use this     |                              To do this                              |
   |------------------|----------------------------------------------------------------------|
   | **Account name** | Enter the account name you want to use to start the Logging Service. |
   |   **Password**   |                 Enter the password for this account.                 |
   |    **Domain**    |               Enter the domain name for this account.                |


8. When prompted **The account name has been granted logon as a service right**, select **OK**.  

9. Review the summary, and select **Next**.  

10. For the **Destination Folder**, select **Next** to use the default folder. Or, select **Change** to choose a different installation folder.

11. In **Logging Database Information** page, enter the following, and then select **Next**.  


    |         Use this         |                                                                                                                                                                                                                   To do this                                                                                                                                                                                                                    |
    |--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **Database Server name** |                                                                                                                              The default value is the server name. <br/><br/>**Note**  The server name defaults to the name of the computer that the BizTalkMgmtDb database resides. You cannot change this value.                                                                                                                              |
    |  **HL7 Database name**   | Enter the name of the database that contains the data for your [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] solution, or accept the default setting; which is **BTAHL7**. <br/><br/> **Note**  You must use the ANSI-ASCII character set per database requirements; [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] does not support other character sets. |


12. Select **Install**.  

13. Select **Finish** when completed.  

    > [!TIP] 
    > Select **Launch Tutorial** to install the End-To-End Tutorial.   

## Next steps
Step through some tutorials at [Get started with the BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md).