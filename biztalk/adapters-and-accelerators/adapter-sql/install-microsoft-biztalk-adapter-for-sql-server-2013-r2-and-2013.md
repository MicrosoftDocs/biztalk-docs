---
title: "Install Microsoft BizTalk Adapter for SQL Server - 2013 R2 and 2013 | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56c31d0d-783b-41ee-8265-56c9547e9dca
caps.latest.revision: 31
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install Microsoft BizTalk Adapter for SQL Server - 2013 R2 and 2013
Install the [!INCLUDE[adaptersql_md](../../includes/adaptersql-md.md)] included with [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)], or included with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 2013.

 The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used with:  

- A .NET application  

- Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]  

  Based on how you use the adapters, the required software varies.  

<a name="BKMK_Prereqs_NET"></a>   
## Prerequisites when using the adapter with a .NET Application  
Install the following software on the computer where you are writing .NET applications that consume the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Install the software in the order as listed.  


|                                 2013 R2                                 |                                  2013                                   |
|-------------------------------------------------------------------------|-------------------------------------------------------------------------|
|          [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]          |      Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]      |
|                           Visual Studio 2013                            |                           Visual Studio 2012                            |
| [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] | [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] |
|                   The SQL Server client libraries. .                    |                    The SQL Server client libraries..                    |

<a name="BKMK_Prereqs_BTS"></a>    
## Prerequisites when using the adapter with BizTalk Server  
Install the following software on the computer where you will be using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. We recommend installing the software in the same order as listed here.  


|                                                                                                                                                                                                                                                               2013 R2                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                                                                2013                                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                                                                                                        [!INCLUDE[dotnet451](../../includes/dotnet451-md.md)]                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                    Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)]                                                                                                                                                                                                                                    |
|                                                                                                                                                                                                                                                         Visual Studio 2013                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                         Visual Studio 2012                                                                                                                                                                                                                                                          |
| [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> Install the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. | [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<br /><br /> Install the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. |
|                                                                                                                                                                                                                                                       BizTalk Server 2013 R2                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                                         BizTalk Server 2013                                                                                                                                                                                                                                                         |
|                                                                                                                                                                                                                                                  The SQL Server client libraries.                                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                  The SQL Server client libraries.                                                                                                                                                                                                                                                   |

<a name="BKMK_SuppLOB"></a>   
## Supported SQL Server versions and client libraries  
 The following section presents the supported SQL Server versions and the client libraries required by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

- **Supported server versions**: SQL Server 2005, SQL Server 2008 SP1, SQL Server 2008 R2, SQL Server 2012  

- **Supported client versions**: Microsoft [!INCLUDE[dotnet45](../../includes/dotnet45-md.md)] bundles the client DLLs required to connect to SQL Server. You do not need to explicitly install any client DLLs on your computer.  

- **Required drivers**:  

  - If you use the UDTs shipped with the SQL Server versions, for example, Geography, make sure the following DLLs are present on the computer where you use the adapter to perform operations on SQL Server. For example, if you create BizTalk projects to perform operations on SQL Server, these DLLs must be present on the computer where BizTalk Server is running.  

    - Make sure Microsoft.SqlServer.Types.dll is added to the GAC.  

    - Make sure SqlServerSpatial.dll is available in the System32 folder.  

      You can install these DLLs on the computer by running the SQL Server setup and selecting **Management Tools – Basic** and **Management Tools – Complete** in the **Feature Selection** page of the wizard.  

  - If you use the adapter to perform operations on columns of FILESTREAM data types, make sure you have SQL Client Connectivity SDK installed. You can install the SQL Client Connectivity SDK by running the SQL Server setup and selecting **SQL Client Connectivity SDK** in the **Feature Selection** page of the wizard. The adapter uses the sqlncli10.dll, installed with the SQL Client Connectivity SDK, to perform FILESTREAM operations.  

  - If you create your own UDTs in SQL Server, make sure the respective assemblies for the UDTs are added to the GAC.  

<a name="BKMK_Compat"></a>   
## 64-bit support 

The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can run in a 32-bit or 64-bit host instance.

 For more information about the supported installation scenarios for the 32-bit and 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)],. 

<a name="BKMK_Install_Adap"></a>   
## Install the SQL Adapter  
 Make sure you have the prerequisites installed before installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

 You can install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in the following two ways:  

- **In interactive mode** using the setup wizard  

- **In silent mode** using msiexec in the command lin  

  > [!IMPORTANT]
  >  You must have administrative privileges on the computer where you will install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], irrespective of whether you are installing by using the wizard or the command line.  

<a name="BKMK_Install_Scenarios"></a>   
### 32-bit and 64-bit install scenarios
 With [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] can be used for:  

- [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] design time (when generating metadata for operations).  

- BizTalk Server Administration console design time (for creating physical ports).  

  > [!NOTE]
  >  BizTalk Server Administration console runs as a 32-bit Microsoft Management Console (MMC) application.  

- BizTalk run time (when sending and receiving messages from LOB applications).  

  You can have an installation where you perform all these tasks on the same computer or different computers. Because both [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and BizTalk MMC are 32-bit processes, you must install the 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on the computer where you want to perform the design-time tasks. The following scenarios are supported for installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on 32-bit and 64-bit platforms.  

#### Install scenarios on a 32-bit platform  
 The following scenarios are supported when installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a 32-bit platform.  


|                                                                                                               Visual Studio design time                                                                                                                |                                                                                                                BizTalk MMC design time                                                                                                                 |                                                                                                                    BizTalk run time                                                                                                                    |                                                                                      Visual Studio design time and/or  BizTalk MMC design time + BizTalk run time                                                                                      |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| - Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 32-bit client and other required DLLs. | - Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 32-bit client and other required DLLs. | - Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 32-bit client and other required DLLs. | - Install 32-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 32-bit client and other required DLLs. |

#### Install scenarios on a 64-bit platform  
 The following scenarios are supported when installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a 64-bit platform.  

> [!NOTE]
>  On any computer where you want to perform design-time tasks using either [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] or BizTalk MMC, you must install the 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

|                                                                                                               Visual Studio design time                                                                                                                |                                                                                                                BizTalk MMC design time                                                                                                                 |                                                                                                                                                                                                                                                                                                   BizTalk run time                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                    Visual Studio design time and/or BizTalk MMC design time + BizTalk run time                                                                                                                                                                                                                                                                                                                                                     |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| - Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 32-bit client and other required DLLs. | - Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 32-bit client and other required DLLs. | **For a 32-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 32-bit client and other required DLLs.<br /><br /> **For a 64-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> - Install 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 64-bit client and other required DLLs. | **For a 32-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 32-bit client and other required DLLs.<br /><br /> **For a 64-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].<br /><br /> - Install 64-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 64-bit client and other required DLLs.<br /><br /> - Install 32-bit [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].<br /><br /> - Install 32-bit client and other required DLLs. |

<a name="BKMK_Install_wizard"></a>   
### Install the SQL Adapter in interactive mode  

1. Run the installer.  

   > [!NOTE]
   >  If you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] on a virtual machine, the setup wizard might not proceed beyond a dialog box informing that the setup is checking for available disk space. In such cases, we recommend that you use the silent installation option.   

2. Read the information on the Welcome screen, and then click **Next**.  

3. Read and accept the end-user license agreement (EULA), and then click **Next**.  

4. In the **Destination Folder** dialog box, specify the location where you want to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], click **Next**, and then click **Install**.  

5. In the **Customer Experience Improvement Program** dialog box, specify whether you would like to enroll for the Customer Experience Improvement Program (CEIP). As part of CEIP for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you will share the following data with Microsoft:  

   - Data related to the computer hardware on which you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

   - Data related to the SQL Server versions you are using to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

     Specify your choice and click **OK**.  

   > [!NOTE]
   >  You can always change your preference regarding enrolling for CEIP by running the Setup in Repair mode from the Control Panel.  

6. Click **Finish**.  

<a name="BKMK_SilentInst"></a>   
### Install the SQL adapter in Silent mode  
 The following procedure demonstrates how to perform a silent installation of [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the `msiexec` command.  

1. Open a command prompt, and navigate to the folder where you have the installer.  

2. Run the following command to install the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]:  

   > [!NOTE]
   >  To perform silent installation on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.  

   ```  
   msiexec /i SqlAdapterSetup.msi /qn  
   ```  

    You can also choose to enroll for CEIP as part of the silent installation. As part of CEIP for [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you will share the following data with Microsoft:  

   - The computer hardware on which you are installing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

   - The SQL Server versions you are using to connect using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

     To enroll for CEIP, run the following command:  

   ```  
   msiexec /i SqlAdapterSetup.msi /qn CEIP_OPTIN=true  
   ```  

    By default, the option is false.  

    For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).  

<a name="BKMK_PostInst"></a>   
## Post-installation tasks  

<a name="BKMK_Register_Bindings"></a>   
#### Register the Bindings  
Complete these steps *only* if the setup wizard fails to register the adapter bindings in the machine.config file.  

1. Navigate to the machine.config file on the computer. For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.  

   - For Microsoft .NET Framework 3.5 SP1, \<*version*\> is the version v2.0.50727 of the .NET Framework.  

   - For Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \<*version*\> is the version v4.0.30319 of the .NET Framework.  

2. Open the file using a text editor.  

3. To register the adapter bindings:  

   1. Search for the element "system.serviceModel" and add the following under it:  

      ```  
      <client>  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  
      ```  

   2. Search for the element "bindingElementExtensions" under system.serviceModel\extensions.  

   3. Add the following section under the "bindingElementExtensions" node.  

       For the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:  

      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. Search for the element "bindingExtensions" under system.serviceModel\extensions.  

   5. Add the following section under the "bindingExtensions" node.  

       For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], add:  

      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  



4. Save and close the machine.config file.  

<a name="BKMK_PubKey"></a>   
#### Determining the Public Key and Version  
Complete the following steps to determine the public key and version for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

1. Navigate to the Windows directory, typically C:\WINDOWS\assembly.  

2. Right-click the DLL for which you want the public key, and then select **Properties**. The following table lists the name of the DLLs for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  


   |                              Adapter                              |      Name of the DLL       |
   |-------------------------------------------------------------------|----------------------------|
   | [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] | Microsoft.Adapters.Sql.dll |


3. On the **General** tab, the value against the **Public Key Token** label specifies the public key for the DLL. Similarly, the value against the **Version** label specifies the version number for the DLL.  

4. Copy the public key, and then click **Cancel**.  

<a name="BKMK_Modify_Adap"></a>   
## Update or change the SQL adapter installation  
 Perform the following steps to modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation. Make sure you have the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installed before you run the setup wizard to modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation.  

 You can modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in the following two ways:  

-   **In interactive mode** by running the setup wizard.  

-   **In silent mode** by using the command line.  

#### Update the SQL Adapter installation in interactive mode  

1.  Click **Start**, and then click **Control Panel**.  

2.  In Control Panel, double-click **Programs and Features**.  

3.  In the **Programs and Features** window, select **Microsoft BizTalk Adapter for SQL Server**, and then click **Change**.  

4.  Read the information on the Welcome screen, and then click **Next**.  

5.  In the **Change, repair, or remove installation** dialog box, click **Repair**.  

6.  In the **Ready to repair Microsoft BizTalk Adapter for SQL Server** dialog box, click **Repair**.  

7.  If required, change your preferences regarding opting for CEIP, and then click **OK**.  

8.  Click **Finish**.  

#### Update the SQL Adapter installation in silent mode  

1. Open a command prompt, and navigate to the root directory of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installer.  

2. Run the following command:  

   > [!NOTE]
   >  To modify the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in silent mode on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.  

   ```  
   msiexec /i SqlAdapterSetup.msi /qn /f  
   ```  

   > [!IMPORTANT]
   >  While modifying the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installation in the silent mode, you cannot change your preferences for opting in or out of CEIP. The preferences will remain the same as you specified during the installation, even if you explicitly set the CEIP_OPTIN to true or false.  

    For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).   

<a name="BKMK_Remove_Adap"></a>   
## Uninstall or remove the SQL Adapter  
 Perform the following steps to remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] from your computer. Make sure you have the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installed before you run the setup wizard to remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

 You can remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in the following two ways:  

-   **In interactive mode** by running the setup wizard.  

-   **In silent mode** by using the command line.  

#### Uninstall in interactive mode  

1.  Click **Start**, and then click **Control Panel**.  

2.  In Control Panel, double-click  **Programs and Features**.  

3.  In the **Add or Remove Programs** window, select **Microsoft BizTalk Adapter for SQL Server**, and then click **Remove**.  

4.  In the dialog box, click **Yes**.  

#### Uninstall in silent mode  

1. Open a command prompt, and navigate to the root directory of the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] installer.  

2. Run the following command:  

   > [!NOTE]
   >  To remove the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in silent mode on an x64-based platform, in the following commands, replace SqlAdapterSetup.msi with SqlAdapterSetup64.msi.  

   ```  
   msiexec /x SqlAdapterSetup.msi /qn  
   ```  

    This command removes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] from the computer.  

    For more information about the `msiexec` command, type `msiexec` on the command line and press `ENTER`, or see [https://support.microsoft.com/kb/230781](https://support.microsoft.com/kb/230781).  

<a name="BKMK_PostRemove"></a>   
### Post-uninstall task  
 If the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] setup fails to remove the adapter bindings while removing the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], you must remove them manually. The following section describes how to manually remove the bindings for the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  

<a name="BKMK_Remove_Binding"></a>   
#### Manually remove the bindings  
 Perform these steps *only* if the setup wizard fails to remove the adapter bindings from the machine.config file.  

1. Navigate to the machine.config file on the computer. For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.  

   - For Microsoft .NET Framework 3.5 SP1, \<*version*\> is the version v2.0.50727 of the .NET Framework.  

   - For Microsoft [!INCLUDE[netfx40_short](../../includes/netfx40-short-md.md)], \<*version*\> is the version v4.0.30319 of the .NET Framework.  

2. Open the file using a text editor.  

3. To remove the adapter binding registration:  

   1. Search for the element "system.serviceModel" and remove the following from under the element:  

      ```  
      <client>  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  

      ```  

   2. Search for the element "bindingElementExtensions" under system.serviceModel\extensions.  

   3. Remove the following section under the "bindingElementExtensions" node.  

       For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], remove:  

      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. Search for the element "bindingExtensions" under system.serviceModel\extensions.  

   5. Remove the following section under the "bindingExtensions" node.  

       For [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], remove:  

      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

4. Save and close the machine.config file.  

## See also
[Install the SQL adapter](../../adapters-and-accelerators/adapter-sql/install-the-sql-adapter.md)  
[Understand BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)