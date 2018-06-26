---
title: "Install BizTalk Adapter Pack 2013 R2 and 2013 | Microsoft Docs"
description: Prerequisites and steps to install BAP 2013 R2 and BAP 2013 included with BizTalk Server
ms.custom: ""
ms.date: "2015-12-09"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9980953a-8d38-476f-af38-4f4214ba61f2
caps.latest.revision: 107
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install BizTalk Adapter Pack 2013 R2 and 2013
This document lists the software requirements, and the steps to install the Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] (BAP) included with BizTalk Server 2013 or [!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)].  

## Change Log  

|Date|Change|  
|---|---|  
|March 2016|In **After installing…**, added steps to configure Oracle Database adapter to use the newer Oracle.DataAccess.dll version.|  

<a name="BKMK_Prereqs"></a>   
## Software prerequisites  
 The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] can be consumed from:  

- A .NET application  

- Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  

- An ADO interface  

- A Microsoft SharePoint portal  

  Based on how you use the adapters, the required software varies.  

### Prerequisites when using a .NET application  
When using a .NET application to consume the adapters, the following software is required on your development computer (the computer where you're creating the .NET application). Install the software in the order listed.


|                                                             BizTalk Adapter Pack 2013 R2                                                              |                                                               BizTalk Adapter Pack 2013                                                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], Windows 8.1, Windows 7 SP1 | [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1, Windows 8, Windows 7 SP1 |
|                                                  [!INCLUDE[dotnet451](../includes/dotnet451-md.md)]                                                   |                                               Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]                                               |
|                                                                  Visual Studio 2013                                                                   |                                                                   Visual Studio 2012                                                                   |
|                                         [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]                                          |                                          [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]                                          |
|              The enterprise application clients and associated software. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).              |              The enterprise application clients and associated software. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).               |

### Prerequisites when using a BizTalk Server  
When using a BizTalk Server to consume the adapters, the following software is required on your BizTalk Server. Install the software in the order listed.


|                                                                                                                                                                                                                                             BizTalk Adapter Pack 2013 R2                                                                                                                                                                                                                                             |                                                                                                                                                                                                                                              BizTalk Adapter Pack 2013                                                                                                                                                                                                                                               |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                                                [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], Windows 8.1, Windows 7 SP1                                                                                                                                                                                 |                                                                                                                                                                                [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1, Windows 8, Windows 7 SP1                                                                                                                                                                                |
|                                                                                                                                                                                                                                  [!INCLUDE[dotnet451](../includes/dotnet451-md.md)]                                                                                                                                                                                                                                  |                                                                                                                                                                                                                              Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]                                                                                                                                                                                                                              |
|                                                                                                                                                                                                                                                  Visual Studio 2013                                                                                                                                                                                                                                                  |                                                                                                                                                                                                                                                  Visual Studio 2012                                                                                                                                                                                                                                                  |
| [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]<br /><br /> Install the [!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]. To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]. | [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]<br /><br /> Install the [!INCLUDE[consumeadapterservlong](../includes/consumeadapterservlong-md.md)] for [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] included with the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]. To install, do a **Custom** (select **BizTalk Server Addin**) or **Complete** installation of the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]. |
|                                                                                                                                                                                                                                                BizTalk Server 2013 R2                                                                                                                                                                                                                                                |                                                                                                                                                                                                                                                 BizTalk Server 2013                                                                                                                                                                                                                                                  |
|                                                                                                                                                                                             The enterprise application clients and associated software. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).                                                                                                                                                                                              |                                                                                                                                                                                             The enterprise application clients and associated software. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).                                                                                                                                                                                              |

### Prerequisites when using ADO  
 The **[!INCLUDE[adaptersap](../includes/adaptersap-md.md)]** and **[!INCLUDE[adaptersiebel](../includes/adaptersiebel-md.md)]** include an ADO layer (*[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]* and *[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]*). This ADO layer can be used to write an ADO.NET client to connect to an SAP system or Siebel system. You can also use the ADO layer with SQL Server Integration Services (SSIS) to import and export data from the LOB application, and SQL Server Reporting Services (SSRS) to generate reports to present data from the LOB systems.  

> [!NOTE]
>  Using the ADO Provider with SSRS is supported only for the *[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]*.  

The following software is required on the computer that uses the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] with an ADO interface. Install the software in the order listed.


|                                                             BizTalk Adapter Pack 2013 R2                                                              |                                                               BizTalk Adapter Pack 2013                                                                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], Windows 8.1, Windows 7 SP1 | [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1, Windows 8, Windows 7 SP1 |
|                                                  [!INCLUDE[dotnet451](../includes/dotnet451-md.md)]                                                   |                                               Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]                                               |
|                                                                  Visual Studio 2013                                                                   |                                                                   Visual Studio 2012                                                                   |
|                                         [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]                                          |                                          [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]                                          |
|                [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)], [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]                 |            [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)], [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]            |
|              The enterprise application clients and associated software. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).              |              The enterprise application clients and associated software. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).               |

### Prerequisites when using Microsoft SharePoint  
 The goal of using the adapters with Microsoft SharePoint is to show data from an LOB application on a SharePoint portal.  

A typical setup with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] and SharePoint can be a single computer or use different computers for different tasks. The following table summarizes the software prerequisites for each computer. If you are using a single computer, all the software is required on that computer. Install the software in the order listed.  


|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Computer where you run the WCF Adapter Service Development Wizard                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      Computer where you host the WCF service                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Computer where you can use the SharePoint Designer to define your External Content Types |                                    Computer where you use SharePoint to present the information from an LOB application                                     |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **BAP 2013 R2**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2<br/>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>Windows 8.1<br/>Windows 7 SP1</li><li>[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]</li><li> Visual Studio 2013</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>Respective enterprise application clients and associated software. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</li></ul> **BAP 2013**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1<br/>Windows 8<br/>Windows 7 SP1</li><li>Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</li><li>Visual Studio 2012</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>Respective enterprise application clients and associated software. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</li></ul> | **BAP 2013 R2**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2<br/>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>Windows 8.1<br/>Windows 7 SP1</li><li>[!INCLUDE[dotnet451](../includes/dotnet451-md.md)]</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>Respective enterprise application clients and associated software. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</li><li>Internet Information Services (IIS) version that comes with the operating system. KB 224609 lists the versions.</li></ul>**BAP 2013**:<ul><li>[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]<br/>[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] SP1<br/>Windows 8<br/>Windows 7 SP1</li><li>Microsoft [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]</li><li>[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</li><li>Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]</li><li>Respective enterprise application clients and associated software. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).</li><li>Internet Information Services (IIS) version that comes with the operating system. KB 224609 lists the versions.</li></ul> |            Microsoft Office SharePoint Server Software Development Kit (SDK)             | Microsoft Office Servers Infrastructure Update. Download at [http://go.microsoft.com/fwlink/?LinkId=128344](http://go.microsoft.com/fwlink/?LinkId=128344). |

<a name="BKMK_SuppLOB"></a>   
## Supported enterprise application versions  

To see the specific LOB system versions that are supported by the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], see **[Supported Line-of-Business (LOB) systems](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-systems.aspx)**. 

This section lists any extra info for each adapter, such as any client DLLs required for each adapter.  

### Oracle Database adapter  

-   Optional: If you use distributed transactions with the Oracle database, install **Oracle Services for Microsoft Transaction Server** (part of the Oracle client installation) on the computer running the adapter client.  

-   For your application to work with the most recent version of ODP.NET, install the **policy DLLs** and register the DLLs in the GAC. See [Oracle Data Provider for .NET FAQ](http://www.oracle.com/technetwork/database/windows/faq-093106.html).  

### Oracle E-Business adapter  

-   Optional: To use distributed transactions with the Oracle database, install **Oracle Services for Microsoft Transaction Server** (part of the Oracle client installation) on the computer running the adapter client.  

-   For your application to work with the most recent version of ODP.NET, install the **policy DLLs** and register the DLLs in the GAC. See [Oracle Data Provider for .NET FAQ](http://www.oracle.com/technetwork/database/windows/faq-093106.html).  

### SAP adapter  

- The [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] requires Unicode version of the RFC SDK irrespective of whether the SAP system is Unicode or non-Unicode.  

- **Required drivers**: The following table lists the DLLs required by the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] to interface with the SAP system. Most of the packages that contain these DLLs must be downloaded from the SAP Service Marketplace. To get downloads from the SAP Service Marketplace: 

  1. Install the Download Manager available from the SAP Service Marketplace.  

  2. Configure the Download Manager by using your credentials for the SAP Service Marketplace.  

  3. Be authorized by the SAP administrator in your organization to download software from the SAP service website. This is required because access to the SAP Software Distribution Center is restricted by a 'Download Software' authorization object. This ensures that software is downloaded only by authorized users.  

  4. Install the SAPCAR program, which is required to extract the files from the packages that you download from the SAP Service Marketplace. SAPCAR is also available from the SAP Service Marketplace.  

     For the 32-bit and 64-bit version of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], you must have the respective 32-bit and 64-bit versions of these DLLs.  

  -   On a 32-bit computer, the 32-bit version of the DLLs must be added to the C:\Windows\System32 folder.  

  -   On a 64-bit computer, the 32-bit version of the DLLs must be added to the C:\Windows\SysWow64 folder. The 64-bit version of the DLLs must be added to the C:\Windows\System32 folder.  

  | SAP client version |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  Required drivers                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |        6.4         |                                                                                                                                                                                                                       **BizTalk Adapter Pack 2013 Only**<br /><br /> - **SAP RFC SDK 6.40 UNICODE**. This is available as part of SNOTE<sup>*</sup> 27517. The instructions to download the SDK are available at [http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691). After you have downloaded and extracted the SDK, copy all the DLLs from the \rfcsdk\bin and \rfcsdk\lib folders to the relevant location mentioned preceding this table.<br /><br /> - DLLs are available from SAP as part of \*\*R3DLLINST.zip*<em>. This contains Microsoft run-time DLLs and can be downloaded from the SAP site. See SNOTE<sup></em></sup> 684106 for more information. You can download the .zip file from [http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693). This link has an “Attachments” option from where you can download the package.<br /><br /> - If you use SAP Secure Network Communications (SNC) to connect to an SAP system, you must also have the relevant DLLs from SAP. These DLLs are different for 32-bit and 64-bit platforms and are available with SNOTE<sup>*</sup> 352295. You can download the DLLs from [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032). This link has an “Attachments” option from where you can download the package. The names of the DLLs are:<br /><br /> - \*\*For 32-bit*<em>: gsskrb5.dll, gssntlm.dll<br /><br /> -  \*\*For 64-bit x86</em>\*: gx64krb5.dll, gx64ntlm.dll                                                                                                                                                                                                                       |
  |        7.0         |                                                                                                                                                                                                                                             - **SAP RFC SDK 7.00 UNICODE**. This is available as part of SNOTE<sup>*</sup> 27517. The instructions to download the SDK are available at [http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691). After you have downloaded and extracted the SDK, copy all the DLLs from the \rfcsdk\bin and \rfcsdk\lib folders and to the relevant location mentioned preceding this table.<br /><br /> - DLLs are available from SAP as part of \*\*R3DLLINST.zip*<em>. This contains Microsoft run-time DLLs and can be downloaded from the SAP site. See SNOTE<sup></em></sup> 684106 for more information. You can download the .zip file from [http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693). This link has an “Attachments” option from where you can download the package.<br /><br /> - If you use SAP Secure Network Communications (SNC) to connect to an SAP system, you must also have the relevant DLLs from SAP. These DLLs are different for 32-bit and 64-bit platforms and are available with SNOTE<sup>*</sup> 352295. You can download the DLLs from [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032). This link has an “Attachments” option from where you can download the package. The names of the DLLs are:<br /><br /> - \*\*For 32-bit*<em>: gsskrb5.dll, gssntlm.dll<br /><br /> - \*\*For 64-bit x86</em>\*: gx64krb5.dll, gx64ntlm.dll                                                                                                                                                                                                                                             |
  |        7.1         | - **SAP RFC SDK 7.10 UNICODE**. This is available as part of SNOTE<sup>*</sup> 27517. The instructions to download the SDK are available at [http://go.microsoft.com/fwlink/?LinkId=94691](http://go.microsoft.com/fwlink/?LinkId=94691). After you have downloaded and extracted the SDK, copy all the DLLs from the \rfcsdk\bin and \rfcsdk\lib folders to the relevant location mentioned preceding this table.<br /><br /> - DLLs are available from SAP as part of \*\*R3DLLINST.zip*<em>. This contains Microsoft run-time DLLs and can be downloaded from the SAP site. See SNOTE<sup></em></sup> 684106 for more information. You can download the .zip file from [http://go.microsoft.com/fwlink/?LinkId=94693](http://go.microsoft.com/fwlink/?LinkId=94693). This link has an “Attachments” option from where you can download the package.<br /><br /> - Microsoft Visual C++ run-time DLLs required for SAP 7.1 client are available from the following links:<br /><br /> - **For 32-bit SAP 7.1 client**:  Vcredist_x86.exe from [http://go.microsoft.com/fwlink/?LinkId=107086](http://go.microsoft.com/fwlink/?LinkId=107086).<br /><br /> -                                 **For 64-bit SAP 7.1 client**: Vcredist_x64.exe from [http://go.microsoft.com/fwlink/?LinkId=107087](http://go.microsoft.com/fwlink/?LinkId=107087).<br /><br /> - If you use SAP Secure Network Communications (SNC) to connect to an SAP system, you must also have the relevant DLLs from SAP. These DLLs are different for 32-bit and 64-bit platforms and are available with SNOTE<sup>*</sup> 352295. You can download the DLLs from [http://go.microsoft.com/fwlink/?LinkId=104032](http://go.microsoft.com/fwlink/?LinkId=104032). This link has an “Attachments” option from where you can download the package. The names of the DLLs are:<br /><br /> - \*\*For 32-bit*<em>: gsskrb5.dll, gssntlm.dll<br /><br /> - \*\*For 64-bit x86</em>\*: gx64krb5.dll, gx64ntlm.dll |

   * SNOTEs are release notes that accompany fixes released by SAP.  

### Siebel adapter  
No extra steps.

### SQL adapter  

**Required drivers**:  

-   **For SQL Server 2005**: If you create User Defined Types (UDTs) in SQL Server, make sure the respective assemblies for the UDTs are added to the GAC.  

-   **For SQL Server 2014, SQL Server 2012, SQL Server 2008 R2,SQL Server 2008 SP1**:  

    -   If you use the UDTs shipped with the SQL Server versions, for example, Geography, make sure the following DLLs are present on the computer where you use the adapter to perform operations on SQL Server. For example, if you create BizTalk projects to perform operations on SQL Server, these DLLs must be present on the computer where BizTalk Server is running.  

        -   Make sure Microsoft.SqlServer.Types.dll is added to the GAC.  

        -   Make sure SqlServerSpatial.dll is available in the System32 folder.    

        You can install these DLLs on the computer by running the SQL Server setup and selecting **Management Tools – Basic** and **Management Tools – Complete** in the **Feature Selection** page of the wizard.          

    -   If you use the adapter to perform operations on columns of FILESTREAM data types, make sure you have SQL Client Connectivity SDK installed. You can install the SQL Client Connectivity SDK by running the SQL Server setup and selecting **SQL Client Connectivity SDK** in the **Feature Selection** page of the wizard. The adapter uses the sqlncli10.dll, installed with the SQL Client Connectivity SDK, to perform FILESTREAM operations.  

    -   If you create your own UDTs in SQL Server, make sure the respective assemblies for the UDTs are added to the GAC.

## 64-bit support

The Siebel adapter is supported in a 32-bit host instance. It is not supported to run the Siebel adapter in a 64-bit host instance. 

All the other adapters can run in a 32-bit or 64-bit host instance. 



 For more information about the supported installation scenarios for installing the 32-bit and 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], see [Scenarios for Installing the BizTalk Adapter Pack on 32-bit and 64-bit Platforms](#BKMK_Install_Scenarios).  

<a name="BKMK_Install_Adap"></a>   
## Installing the BizTalk Adapter Pack  
 Make sure all the [software prerequisites](#BKMK_Prereqs) are installed before installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. You can install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in the following two ways:  

- **In interactive mode**: Run the setup wizard  

- **In silent mode**: Use the command line  

  > [!IMPORTANT]
  >  You must have administrative privileges on the computer where you install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], irrespective of whether you are installing using the wizard or the command line.  

### Typical vs custom installation  
This section lists the installation types, and the features that are installed with each option:  

- The **Typical** and **Complete** options install all the adapters, with the associated data providers. You do not have the option of choosing a specific adapter to install.  

- The **Custom** option installs one or more adapters, with the associated data providers. You can choose which adapters to install. If you choose to install a data provider, you must also install the corresponding adapter. However, you can install an adapter without installing the corresponding data provider. Do this by expanding the **ADO Providers** node, and then selecting the providers that you don't want to install. See [Installing the BizTalk Adapter Pack in Interactive Mode](#BKMK_Install_wizard).  

   For example, if you install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], you must also install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]. However, you can install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] without installing the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].  

<a name="BKMK_Install_Scenarios"></a>   
### Scenarios for installing the BizTalk Adapter Pack on 32-bit and 64-bit platforms  
 With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] can be used for: 

- [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] design time (when generating metadata for operations on LOB applications)

- BizTalk Server Administration console design time (for creating physical ports)

  > [!NOTE]
  >  BizTalk Server Administration console runs as a 32-bit Microsoft Management Console (MMC) application.  

- BizTalk run time (when sending and receiving messages from LOB applications)

You can use a single computer for all these taks, or use different computers. Because both [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and BizTalk MMC are 32-bit processes, you must install the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] on the computer where you complete the design-time tasks. 

#### Scenarios for installing the BizTalk Adapter Pack on a 32-bit platform  
 The supported scenarios on a 32-bit platform include:  


|                                                                                                                 For Visual Studio design time                                                                                                                  |                                                                                                                  For BizTalk MMC design time                                                                                                                   |                                                                                                                      For BizTalk run time                                                                                                                      |                                                                                        For Visual Studio design time and/or BizTalk MMC design time + BizTalk run time                                                                                         |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| - Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs. | - Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs. | - Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs. | - Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs. |

#### Scenarios for installing the BizTalk Adapter Pack on a 64-bit platform  
 The supported scenarios on a 64-bit platform include:  


|                                                                                                                 For Visual Studio design time                                                                                                                  |                                                                                                                  For BizTalk MMC design time                                                                                                                   |                                                                                                                                                                                                                                                                                                         For BizTalk run time                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                For Visual Studio design time and/or BizTalk MMC design time + BizTalk run time                                                                                                                                                                                                                                                                                                                                                                |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs. | - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs. | **For a 32-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs.<br /><br /> **For a 64-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 64-bit LOB client and other required DLLs. | **For a 32-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs.<br /><br /> **For a 64-bit BizTalk process**:<br /><br /> - Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].<br /><br /> - Install 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 64-bit LOB client and other required DLLs.<br /><br /> - Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].<br /><br /> - Install 32-bit LOB client and other required DLLs. |

> [!NOTE]
>  On any computer where you want to do design-time tasks, using either [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] or BizTalk MMC, you must install the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  

<a name="BKMK_Install_wizard"></a>   
### Installing the BizTalk Adapter Pack in interactive mode  
Complete the following steps to install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] using the setup wizard.  

1. From the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation media, run **Setup.exe**.  

2. Select **Install Microsoft BizTalk Adapters**. In the next window, select **Install Microsoft BizTalk Adapter Pack** or **Install Microsoft BizTalk Adapter Pack (x64)**, depending on your platform.  

   > [!NOTE]
   >  If you are installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] on a virtual machine, the setup wizard might not proceed beyond a dialog box informing that the setup is checking for available disk space. In such cases, we recommend that you use the silent installation option. See [Installing the BizTalk Adapter Pack in Silent Mode](#BKMK_SilentInst) (in this topic).  

3. On the Welcome screen, select **Next**.  

4. Accept the end-user license agreement (EULA), and then select **Next**.  

5. In **Choose Setup Type**:  

   -   To install the most common features, select **Typical**.  

   -   To select the adapters you want to install, select **Custom**, and then proceed to the next step.  

   -   To install all the features, select **Complete**.  

       > [!IMPORTANT]
       >  To install only the adapter that you use to interface with your enterprise application, select the **Custom** installation.  

6. **Required** only if you chose the Custom installation. If you chose the **Typical** or **Complete** installation, then skip this step, and go to step 7.  

    1.  In **Custom Setup**, expand **Base Adapters** to see the available adapters.  

    2.  For the adapters that you don't want, select the icon next to the adapter, and then select **Entire feature will be unavailable**.  

    3.  Expand **ADO Providers**, and then select the providers that you don't want to install.  

    4.  Select **Next**.  

7. Select **Install**.  

8. In **Customer Experience Improvement Program**, you can choose to enroll. If you enroll, you can share the following data with Microsoft:  

   - Data related to the computer hardware on which you are installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  

   - Data related to the enterprise application versions you are using with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  

     Select **OK**. [CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699) provides more information.  

   > [!NOTE]
   >  You can always change this setting by running the Setup in Repair mode from **Programs**.  

9. Select **Finish**.  

<a name="BKMK_SilentInst"></a>   
### Installing the BizTalk Adapter Pack in silent mode  
 Use the **msiexec** command to do a silent installation. As part of the msiexec command, enter the individual components that you want to install. The following table lists the values for each component in the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Use these values to install (or remove) specific components. To install (or remove) more than one component, you can use a combination of these values separated by a comma.  


|                                    Component name                                    |                                                                Corresponding value for command-line properties                                                                 |
|--------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]        |                                                                                   DbFeature                                                                                    |
| [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)] |                                                                                OracleEBSFeature                                                                                |
|           [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]           |                                                                             SapBaseAdapterFeature                                                                              |
|        [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]        |                                                                            SiebelBaseAdapterFeature                                                                            |
|            [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]            |                                                                                   SqlFeature                                                                                   |
|        [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]        |     SapAdoFeature<br /><br /> **Note**: You must provide this value only if you are installing the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] also.      |
|     [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]     | SiebelAdoFeature<br /><br /> **Note**: You must provide this value only if you are installing the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] also. |
|                                    All components                                    |                                                                                      ALL                                                                                       |

> [!IMPORTANT]
>  The feature names are case-sensitive.  

 The following steps show you how to complete a silent installation of [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] for different components.  

##### Install in silent mode  

1. Open a command prompt, and go to the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] root in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.  

2. Run the following commands based on what you want to install:  

   > [!NOTE]
   >  To do silent installation on an x64-based platform, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi` in the following commands.  

   - To perform a complete installation, which installs all the adapters including the .NET Framework Data Providers, type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=ALL  
     ```  

   - To install only the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=DbFeature  
     ```  

   - To install only the [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=OracleEBSFeature  
     ```  

   - To install only the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature  
     ```  

   - To install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] along with [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature  
     ```  

   - To install only the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature  
     ```  

   - To install the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] along with [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature,SiebelAdoFeature  
     ```  

   - To install only the [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SqlFeature  
     ```  

   - To install all the base adapters, type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SiebelBaseAdapterFeature,DbFeature,OracleEBSFeature,SqlFeature  
     ```  

   - To install the two .NET Framework Data Providers, type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapAdoFeature,SiebelAdoFeature  
     ```  

   - Any type of custom installation by separating the components by a comma. For example, to install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] with the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], and the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature,SiebelBaseAdapterFeature  
     ```  

   - You can also opt to enroll for CEIP as part of the silent installation. Type:  

     ```  
     msiexec /i AdaptersSetup.msi /qn CEIP_OPTIN=true  
     ```  

      By default the option is false. 

     > [!IMPORTANT]
     >  While installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] Evaluation version in silent mode, the default option for CEIP is true.  

     For more information about the msiexec command type `msiexec` on the command line and press `ENTER`. Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).

<a name="BKMK_PostInst"></a>   
### After installing the BizTalk Adapter Pack  
 You may need to do the following tasks after installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], based on what operations you want to do with each adapter:  

- [Configure the Oracle Database adapter to use a newer Oracle.DataAccess.dll version](#BKMK_ConfigNewOracleDLL) in the OracleDB configuration file.  

- [Create SQL Server Database Objects (Only for the SAP Adapter)](#BKMK_CreateSQLServer) to invoke transactional RFCs (tRFCs) in an SAP system.  

- [Register the adapter bindings](#BKMK_Register_Bindings) and the .NET Framework Data Providers if the setup wizard fails to do so.  

- [Determine the Public Key and Version](#BKMK_PubKey) of the different adapter files.  

- [Install the Custom RFCs](#BKMK_InstallCustomRFC) if you chose to install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].  

<a name="BKMK_ConfigNewOracleDLL"></a>   
#### Configure the Oracle Database adapter to use a newer Oracle.DataAccess.dll version  
 When you configure a port to use the WCF-OracleDB adapter or use Visual Studio to consume a generated adapter, a message displays that the adapter needs Oracle.DataAccess.dll version 2.111.7.0. To resolve this message, install a supported Oracle.DataAccess.dll version (see [supported version list](https://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)), and then update the `bindingRedirect` element in the OracleDB configuration file. Steps:  

1.  On the BizTalk Server, go to the following folders:  

     *drive*:\Program Files\Microsoft BizTalk Adapter Pack(x64)\bin  

     *drive*:\Program Files (x86)\Microsoft BizTalk Adapter Pack\bin  

2.  Open the Microsoft.Adapters.OracleDB.config file.  

3.  Find the following section, and copy/paste the following:  

    ```  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
              <dependentAssembly>  
                        <assemblyIdentity name="Oracle.DataAccess" publicKeyToken="89b483f429c47342" culture="neutral" />  
                        <bindingRedirect oldVersion="2.111.7.00" newVersion="2.112.1.00"/>  
              </dependentAssembly>  
    </assemblyBinding>  

    ```  

    > [!NOTE]
    >  In this example, we set *newVersion* to 2.112.1.00. Set this value to the version you have installed.  

> [!IMPORTANT]
> - If there are multiple BizTalk Servers in this group, make this change on all the BizTalk servers in the group.  
>   -   The *newVersion* value needs to be updated based on the version of the Oracle.DataAccess.dll file installed on the computer.  Oracle.DataAccess.dll is included with the Oracle Client you install from Oracle.  You must only install an Oracle Client version that is [supported by the BizTalk Adapter Pack](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx).  

<a name="BKMK_CreateSQLServer"></a>   
#### Create SQL Server Database objects (only for the SAP adapter)  
 To invoke tRFCs in an SAP system, run the *SapAdapter-DbScript-Install.sql* SQL script. This script is installed with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, and creates database objects in SQL Server. The script is typically installed at \<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. You can run this script against any SQL Server database, as long as you enter that database name while using the adapter to invoke tRFCs.  

<a name="BKMK_Register_Bindings"></a>   
#### Register the adapter bindings  
 During the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, the setup wizard may fail to register the adapter bindings or the .NET Framework Data Provider for mySAP Business Suite, but setup proceeds with the adapter installation. This might result due to problems with Windows Communication Foundation (WCF) installation, [!INCLUDE[afproductnamelong](../includes/afproductnamelong-md.md)] installation, or the machine.config file being corrupt.  

Complete these steps *only* if the setup wizard fails to register the adapter bindings or .NET Framework Data Providers in the machine.config file.  

###### Register the adapter bindings or the .NET Framework data providers  

1. Go to the machine.config file on the computer. For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.  

2. Open the file using a text editor.  

3. Register the adapter bindings:  

   1. Search for the `system.serviceModel` element, and add the following under it:  

      ```  
      <client>  
        <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
        <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
        <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
        <endpoint binding="oracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  
      ```  

   2. Search for the `bindingElementExtensions` element under system.serviceModel\extensions.  

   3. Look for the missing adapter binding. Add the following sections under the `bindingElementExtensions` node, depending on the missing adapter binding. You must register all the bindings if the setup wizard fails to register any.  

       For the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], add:  

      ```  
      <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], add:  

      ```  
      <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], add:  

      ```  
      <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For the [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], add:  

      ```  
      <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For the [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], add:  

      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. Search for the `bindingExtensions` element under system.serviceModel\extensions.  

   5. Look for the missing adapter binding. Add the following sections under the `bindingExtensions` node, depending on the missing adapter binding. You must register all the bindings if the setup wizard fails to register any.  

       For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], add:  

      ```  
      <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], add:  

      ```  
      <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], add:  

      ```  
      <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], add:  

      ```  
      <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS,Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], add:  

      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   > [!NOTE]
   >  For information about how to determine the public key, see [Determine the Public Key and Version](#BKMK_PubKey).  

4. Register the .NET Framework data providers:  

   1. Search for the `DbProviderFactories` element under the system.data node.  

   2. Look for the missing .NET Framework Data Providers. Add the following sections under the `DbProviderFactories` node, depending on the missing provider. You must register all the providers if the setup wizard fails to register any.  

       For the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], add:  

      ```  
      <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
          description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For the [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], add:  

      ```  
      <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
          description=".NET Framework Data Provider for Siebel eBusiness Applications"  
          type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

5. Save and close the machine.config file.  

<a name="BKMK_PubKey"></a>   
#### Determine the Public Key and Version  
 Complete the following steps to determine the public key and version for an adapter or the .NET Framework Data Provider.  

###### Determine the public key  

1. Go to the Windows directory, typically C:\WINDOWS\assembly.  

2. Right-click the DLL for which you want the public key, and then select **Properties**. The following table lists the name of the DLLs for each adapter and provider:  


   |                         Adapter/.NET Framework Data Provider                         |       Name of the DLL        |
   |--------------------------------------------------------------------------------------|------------------------------|
   |           [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]           |    Microsoft.Adapters.SAP    |
   |        [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]        |  Microsoft.Adapters.Siebel   |
   |        [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]        | Microsoft.Adapters.OracleDB  |
   | [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)] | Microsoft.Adapters.OracleEBS |
   |            [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]            |  Microsoft.Adapters.Sql.dll  |
   |        [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]        |   Microsoft.Data.SAPClient   |
   |     [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]     | Microsoft.Data.SiebelClient  |


3. On the **General** tab, the **Public Key Token** values is the public key for the DLL. The **Version** value is the version number for the DLL.  

4. Copy the public key, and then select **Cancel**.  

<a name="BKMK_InstallCustomRFC"></a>   
#### Install the custom RFCs  
 You only need to do this task if you want to use the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]. For instructions on installing custom RFCs, see [Install Custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md) in the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] documentation. 

> [!IMPORTANT]
>  If you are using an earlier version of the custom RFCs provided with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], then you must upgrade them to the RFCs provided with this release. Do this by removing the earlier RFCs, and then installing the RFCs shipped with this release.  

## Installing the Enterprise Applications  
For the steps and guidance to install the different enterprise LOB systems, we recommendnd you use their specific installation guides. Also refer to its adapter documentation for specific configuration changes, if any.   

## Installation and post-installation checklist  

- Make sure you installed all the [software prerequisites](#BKMK_Prereqs) with the correct installation option.

- Make sure you have the supported version of the enterprise LOB applications installed on your computer where you installed the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. See [Supported Enterprise Application Versions](#BKMK_SuppLOB).  

- To install only the adapter for the enterprise LOB system you want to connect, make sure you installed the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] using the **Custom** installation option. Make sure you have not installed the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] using the **Complete** installation option. See [Installing the BizTalk Adapter Pack](#BKMK_Install_Adap).  

- If you want to make tRFC calls to the SAP system using the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], make sure you create the required tables in a SQL Server database. See [After Installing the BizTalk Adapter Pack](#BKMK_PostInst).

- While running the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] setup wizard, you may get an error message that states the setup failed to register the bindings. If so, register them manually. See [After Installing the BizTalk Adapter Pack](#BKMK_PostInst).  

- If you chose to install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)] as part of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation, make sure you install the custom RFCs on the SAP system. See [After Installing the BizTalk Adapter Pack](#BKMK_PostInst).  

<a name="BKMK_Modify_Adap"></a>   
## Change the BizTalk Adapter Pack installation  
 Complete the following steps to change the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation. Make sure you have the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installed before you run the setup wizard to modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.  

 You can modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in interactive mode (the setup wizard), or in silent mode (the command line).

#### Change the BAP installation in interactive mode  

1. Sign in using an account that is a member of the BizTalk Server Administrators group.  

2. In **Programs and features**, select **Uninstall a program**.  

3. Right-click **Microsoft BizTalk Adapter Pack**, and then select **Change**.  

4. On the Welcome screen, select **Next**.  

5. In **Change, repair, or remove installation**:  

   - To select the components you want to install, select **Change** and go to Step 6.  

   - To repair errors in the most recent installation, select **Repair** and go to Step 7.  

   - To remove Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from the computer, select **Remove** and then go to Step 10.  

6. If you chose to modify the installation:  

   -   Expand the **Microsoft BizTalk Adapter Pack** node to choose to install the base adapters, the .NET Framework Data Providers, or both.  

   -   Expand the **Base Adapters** node to choose to install all the adapters or specific adapters.  

   -   Expand the **ADO Providers** node to choose to install all the providers or specific providers.  

   -   Select **Next**.  

   -   Select **Change**, and then select **Finish**.  

7. If you chose to repair the installation, in the **Ready to repair Microsoft BizTalk Adapter Pack** dialog box, select **Repair**. The wizard starts repairing the installation.  

8. If required, change your preferences regarding opting for CEIP, and then select **OK**. 

9. Select **Finish**.  

10. If you chose to remove the adapters, in the **Ready to remove Microsoft BizTalk Adapter Pack** dialog box, select **Remove**, and then select **Finish**.  

#### Change the BAP installation in silent mode  

1. Open a command prompt, and go to the root directory of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installer.  

2. Run a command similar to the following:  

   > [!NOTE]
   >  To modify the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in a silent mode on an x64-based platform, in the following commands, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi`.  

   ```  
   msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature ADDLOCAL=SapBaseAdapterFeature  
   ```  

    This command removes the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], and installs the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].  

    By using different values for the `REMOVE` and `ADDLOCAL` properties, you can add or remove specific components. Refer to the table in [Installing the BizTalk Adapter Pack in Silent Mode](#BKMK_SilentInst) (in this topic) for information about the values that you can use for these properties.  

    You can also do a silent repair by using the /f option as part of the msiexec command. For example:  

   ```  
   msiexec /i AdaptersSetup.msi /qn /f  
   ```  

    You can use various different combinations with the /f option. For more information about the msiexec command type `msiexec` on the command line, and press `ENTER`. Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).  

   > [!IMPORTANT]
   >  While modifying the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation in the silent mode, you cannot change your preferences for opting in or out of CEIP. The preferences you chose during the installation remains, even if you explicitly set the CEIP_OPTIN to true or false.  

<a name="BKMK_Remove_Adap"></a>   
## Removing the BizTalk Adapter Pack  

> [!IMPORTANT]
>  If you created tables in the SQL Server database to work with the tRFC feature of the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], you must manually remove them before removing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation copies a SapAdapter-DbScript-Uninstall.sql file typically at \<installation drive\>:\Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. Run this file to remove the tables you created.  

Complete the following steps to remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] from your computer. Make sure you have the [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)] installed before you run the setup wizard to remove the adapters.  

 You can remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in interactive mode (setup wizard), or in silent mode (command line).

#### Uninstall the BizTalk Adapter Pack in interactive mode  

1.  In **Programs and features**, select **Uninstall a program**.  

2.  Right-click **Microsoft BizTalk Adapter Pack**, and then select **Uninstall**.  

#### Uninstall the BizTalk Adapter Pack in silent mode  

1. Open a command prompt, and go to the root directory of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installer.  

2. Run the following command:  

   > [!NOTE]
   >  To remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in silent mode on an x64-based platform, in the following commands, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi`.  

   ```  
   msiexec /i AdaptersSetup.msi /qn REMOVE=DbFeature  
   ```  

    This command removes the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)] from the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation.  

    By providing different values for the `REMOVE` property, you can remove specific components from the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] installation. Refer to the table in [Installing the BizTalk Adapter Pack in Silent Mode](#BKMK_SilentInst) (in this topic) for information about the values that you can use for this property.  

    To completely remove the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], execute the following command:  

   ```  
   msiexec /x AdaptersSetup.msi /qn  
   ```  

    For more information about the msiexec command type `msiexec` on the command line, and press `ENTER`. Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).

<a name="BKMK_PostRemove"></a>   
### After removing the BizTalk Adapter Pack  
 You may need to perform the following steps after removing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]:  

- Remove the adapter bindings or the .NET Framework Data Provider registration, if the setup wizard failed to do so

- Remove the custom RFCs, if you chose to install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]

<a name="BKMK_Remove_Binding"></a>   
#### Remove the bindings or the .NET Framework Data Provider registration  
 Complete these steps *only* if the setup wizard fails to remove the adapter bindings or .NET Framework Data Provider registration from the machine.config file.  

###### Remove the adapter bindings or .NET Framework Data Provider registration  

1. Go to the machine.config file on the computer. For example, on a 32-bit platform, the machine.config is available under \<system drive\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.  

2. Open the file using a text editor.  

3. Remove the adapter binding registration:  

   1. Search for the `system.serviceModel` element, and remove the following from under the element:  

      ```  
      <client>  
        <endpoint binding="sapBinding" contract="IMetadataExchange" name="sap" />  
        <endpoint binding="siebelBinding" contract="IMetadataExchange" name="siebel" />  
        <endpoint binding="oracleDBBinding" contract="IMetadataExchange" name="oracleDb" />  
        <endpoint binding="OracleEBSBinding" contract="IMetadataExchange" name="oracleEBS" />  
        <endpoint binding="sqlBinding" contract="IMetadataExchange" name="mssql" />  
      </client>  

      ```  

   2. Search for the `bindingElementExtensions` element under system.serviceModel\extensions.  

   3. Remove the following sections under the `bindingElementExtensions` node, depending on the available adapter binding. You must remove all the bindings if the setup wizard fails to remove any.  

       For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], remove:  

      ```  
      <add name="sapAdapter" type="Microsoft.Adapters.SAP.SAPAdapterExtensionElement,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], remove:  

      ```  
      <add name="siebelAdapter" type="Microsoft.Adapters.Siebel.SiebelAdapterExtensionElement,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], remove:  

      ```  
      <add name="oracleDBAdapter" type="Microsoft.Adapters.OracleDB.OracleDBAdapterExtensionElement,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], remove:  

      ```  
      <add name="OracleEBSAdapter" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingElementExtensionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], remove:  

      ```  
      <add name="sqlAdapter" type="Microsoft.Adapters.Sql.SqlAdapterBindingElementExtensionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

   4. Search for the `bindingExtensions` element under system.serviceModel\extensions.  

   5. Remove the following sections under the `bindingExtensions` node, depending on the available adapter binding. You must remove all the bindings if the setup wizard fails to remove any.  

       For [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], remove:  

      ```  
      <add name="sapBinding" type="Microsoft.Adapters.SAP.SAPAdapterBindingSection,Microsoft.Adapters.SAP, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], remove:  

      ```  
      <add name="siebelBinding" type="Microsoft.Adapters.Siebel.SiebelAdapterBindingSection,Microsoft.Adapters.Siebel, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], remove:  

      ```  
      <add name="oracleDBBinding" type="Microsoft.Adapters.OracleDB.OracleDBAdapterBindingSection,Microsoft.Adapters.OracleDB, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], remove:  

      ```  
      <add name="OracleEBSBinding" type="Microsoft.Adapters.OracleEBS.OracleEBSBindingCollectionElement, Microsoft.Adapters.OracleEBS, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

       For [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], remove:  

      ```  
      <add name="sqlBinding" type="Microsoft.Adapters.Sql.SqlAdapterBindingCollectionElement,Microsoft.Adapters.Sql, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
      ```  

4. Remove the .NET Framework Data Provider registration:  

   - Search for the `DbProviderFactories` element under the system.data node.  

   - Look for the .NET Framework Data Providers that are still registered. Remove the following sections under the `DbProviderFactories` node, depending on the existing .NET Framework Data Providers. You must remove all the providers if they exist.  

      For [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], remove:  

     ```  
     <add name="SAPClient Data Provider" invariant="Microsoft.Data.SAPClient"   
         description=".NET Framework Data Provider for mySAP Business Suite"    type="Microsoft.Data.SAPClient.SAPClientFactory,Microsoft.Data.SAPClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
     ```  

      For [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], remove:  

     ```  
     <add name="SiebelClient Data Provider" invariant="Microsoft.Data.SiebelClient"  
         description=".NET Framework Data Provider for Siebel eBusiness Applications"  
         type="Microsoft.Data.SiebelClient.SiebelProviderFactory,Microsoft.Data.SiebelClient, Version=<version>, Culture=neutral, PublicKeyToken=<public key>" />  
     ```  

5. Save and close the machine.config file.  

<a name="BKMK_Remove_SAP_Pro"></a>   
#### Remove the custom RFCs  
Complete this step to remove the custom RFCs that you installed in the SAP system. See [Install or remove custom RFCs](../adapters-and-accelerators/adapter-sap/install-custom-rfcs-for-the-data-provider-for-sap.md).  

## Troubleshoot BizTalk Adapter Pack installation  
 Following are some issues that you might face when installing [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]. For a comprehensive list of installation-related issues, refer to **Troublehsooting** topics for each adapter.  

- **Running setup on a 64-bit computer might throw an error while accessing schema file**  

   The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] setup throws an error while accessing the **Microsoft.Adapters.*\<AdapterName\>*_schema.xml** file, but proceeds with the adapter installation.  

   **Cause**  

   If both 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] are installed on the same computer, the target schema file used by both is the same. As a result, the file installed by the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] might be in use by IIS when the 64-bit installer tries to access it.  

   **Resolution**  

   Manually copy the **Microsoft.Adapters.*\<AdapterName\>*_schema.xml** file from `C:\Program Files\Microsoft BizTalk Adapter Pack(x64)\IIS Schemas`" to `C:\Windows\System32\inetsrv\config\schema`.  