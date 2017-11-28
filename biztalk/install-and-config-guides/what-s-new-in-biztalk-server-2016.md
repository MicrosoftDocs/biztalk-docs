---
title: "What's New in BizTalk Server 2016 | Microsoft Docs"
description: Changes and improvements, including feature packs, adapters, security, tracking, performance, and more in BizTalk Server 2016
ms.custom: ""
ms.prod: biztalk-server
ms.date: "11/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3fce1fe8-f515-462d-bf6d-19408d515479
caps.latest.revision: 28
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What's New in BizTalk Server 2016
Read about what's new in [!INCLUDE[bts2016](../includes/bts2016-md.md)]. 
  
## New in BizTalk Server 2016  
  
|Feature|Description|  
|-------------|-----------------|  
|Support for newer platforms|[!INCLUDE[bts2016](../includes/bts2016-md.md)] adds support for the following Microsoft platforms:<br /><br /> -   Visual Studio 2015<br />-   Windows Server 2016<br />-   [!INCLUDE[sqlserver2016](../includes/sqlserver2016-md.md)]<br />-   Office 2016<br/><br/>[Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)|  
| Feature Pack 2 | Improvements include closer integration with API Management, an Azure Event Hubs adapter, backup to Azure blob storage account, support for Service Bus partitions, and more. <br/><br/>[Install the feature pack](https://www.microsoft.com/download/details.aspx?id=55100)<br/>[See what's included, and configure its features](../core/configure-the-feature-pack.md) |
| Feature Pack 1 | Includes support for automatic deployment using VSTS, send tracking data to Azure Application Insights and Power BI, advanced scheduling options on receive locations, and more.<br/><br/>[Install the feature pack](https://www.microsoft.com/download/details.aspx?id=55100)<br/>[See what's included, and configure its features](../core/configure-the-feature-pack.md) |
|[!INCLUDE[sqlserver2016](../includes/sqlserver2016-md.md)] AlwaysOn Availability Groups|Support includes:<br /><br /> -   Using on-premises and in [!INCLUDE[winazure](../includes/winazure-md.md)] IaaS virtual machines<br />-   Using for  production workloads<br />-   Provides a high available (HA) solution in [!INCLUDE[winazure](../includes/winazure-md.md)] <br/><br/>[High Availability using SQL Server AlwaysOn](../core/high-availability-using-sql-server-always-on-availability-groups.md)<br/><br/> See [distributed transactions for Always On AG](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring) for any SQL-specific requirements and features.|  
|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Azure VMs in production|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Azure virtual machines are now fully supported for production environments. Using [!INCLUDE[sqlserver2016](../includes/sqlserver2016-md.md)] AlwaysOn, a highly available solution is now possible.<br/><br/>[High Availability using SQL Server AlwaysOn](../core/high-availability-using-sql-server-always-on-availability-groups.md)|  
|Logic App adapter|Connect to your Logic Apps hosted in Azure, and get access to all the connectors including Salesforce, SharePoint, CRM Online, and more. For example, you can receive an order in BizTalk Server, connect to your Logic App, and update Salesforce.<br/><br/>[Logic App adapter](../core/logic-app-adapter.md)|  
| File adapter | Connect to an Azure storage file share. You can receive files from the Azure file share, and send messages to an Azure file share. <br/><br/>[Configure the File adapter](../core/configure-the-file-adapter.md)|
| FTP adapter | SYST command is no longer required. When you configure the FTP adapter on a receive location or send port, there is a property called **FTP Server Type**. Using this property, you choose the FTP server you want; which determines if SYST is required. <br/><br/>As a result of this change, there are more "supported" FTP servers. <br/><br/> [Configuring the FTP adapter](../core/configuring-the-ftp-adapter.md)|
|SFTP adapter| SFTP adapter is re-engineered to use WinSCP to connect to SFTP; which allows support for more SFTP servers. Client-side logging and additional encryption ciphers are also new. <br/><br/>[SFTP adapter](../core/sftp-adapter.md)|  
| Allow import of tracking settings | When importing a binding a file, you can choose to import (or not import) the tracking properties enabled on your orchestrations, send ports, and so on. This is a global setting (set at the Group level) so you can set this feature in your different environments. For example, you can import the existing tracking properties for your Development environments, and don't import the tracking properties for your Production environments.<br/><br/>See **BizTalk Settings Dashboard, Group Page** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|
| Shared Access Signature (SAS) | You can use SAS authentication for the Service Bus connection with the *BasicHttpRelay*, *NetTcpRelay*, *BasicHttp*, and *WebHttp* adapters.<br/><br/>[WCF-BasicHttpRelay adapter](../core/wcf-basichttprelay-adapter.md)<br/>[WCF-NetTcpRelay adapter](../core/wcf-nettcprelay-adapter.md)<br/>[WCF-BasicHttp adapter](../core/wcf-basichttp-adapter.md)<br/>[WCF-WebHTTP adapter](../core/wcf-webhttp-adapter.md)<br/><br/> [SB-Messaging adapter](../core/sb-messaging-adapter.md) now includes the steps to get Access Control (ACS) values using PowerShell.|
|Ordered delivery on dynamic ports|Applies to the adapters that support ordered delivery on static send ports. You can enable the ordered delivery option in the BizTalk Administration console.<br /><br />[How to Configure Transport Advanced Options for a Send Port](../core/how-to-configure-backup-transport-options-for-a-send-port.md)<br />[Ordered Delivery of Messages](../core/ordered-delivery-of-messages.md)|  
|SHA-2 hash functions|SHA-2 is fully supported, including:<br /><br /> <ul><li>BizTalk can consume SHA2-signed certificates across all of its components, including SSL messaging in the HTTPS, FTPS, POP3, and the WCF adapters </li><li>Supports the following Advanced Encryption Standard (AES) exchange system for signature keys in AS2, RosettaNet, and the MIME/SMIME encoder:<ul><li>AES128 (default)</li><li>AES192</li><li>AES256</li><br /></ul></li><li>Supports the following SHA2-based MIC calculations for AS2:<ul><li>SHA256 (default)</li><li>SHA384</li><li>SHA512</li><br /></ul></li><li>Supports the following SHA2-based digest methods in RosettaNet:<ul><li>SHA256 (default)</li><li>SHA384</li><li>SHA512</li><br /></ul></li><li>SHA1 certificates continue to work for backward compatibility</li></ul><br />[Configuring Validation (AS2)](../core/configuring-validation-as2.md)<br />[Configuring Acknowledgements (MDNs) (AS2)](../core/configuring-acknowledgements-mdns-as2.md)<br />[How to Configure the MIME-SMIME Encoder Pipeline Component](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)|  
|Compile your maps|Choose to compile your maps using XslTransform or XslCompiledTransform<br/><br/>[Set map compilation and output settings](../core/how-to-specify-xslt-output-settings.md)|  
|Schema window|In the BizTalk mapper, you add/replace a source schema and a destination schema. When you do this, the Type Picker window is now resizable. This change allows you to expand the window, and see the full name of your schema.<br/><br/>[How to resize the schema picker, and expand and collapse the schema trees](../core/how-to-resize-the-schema-picker-and-expand-and-collapse-the-schema-trees.md)|  
|Adapters and Accelerators|Improvements and changes include:<ul><li>The SAP adapter supports classic RFC SDK, and the .NET Connector in the SAP binding properties. <br/><br/>Install the **SAP Connector for .NET**, which is available at the SAP Service Marketplace (service.sap.com/connectors). During the install, be sure to select **Install Assemblies to GAC**.<br/><br/>[WCF-SAP adapter support for the SAP .NET Connector](https://support.microsoft.com/kb/3100811) provides additional details.  </li><br /><li>BizTalk Accelerator for HL7: The MLLP adapter on a receive location now supports the  option to initiate an outbound connection to a remote LOB listener.</li></ul>|  
|Import/export parties|Changes include:<br /><br /> -   The import and export option is separated from the  Application. For example, you can export a party without exporting the application. You can import a party without importing the application.<br />-   Can choose which parties, business profiles, and agreements you want to import or export<br />-   Can continue to import/export the business-to-business artifacts as you do in [!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)], [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013, and  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010.<br/><br/>[Use binding files to import or export](../core/use-binding-files-to-import-or-export.md)|  
|BizTalk Administration|In addition to a more modern look and feel, some additional changes include:<br /><br /> -   Configure the settings for multiple hosts/host instances simultaneously. For example, you can set the .NET CLR settings for multiple host instances simultaneously.<br />-   Use the new Search feature to filter and find artifacts in your application, such as schemas, resources, and more.<br />-   When troubleshooting suspended messages, you can save multiple suspended messages simultaneously to a file.<br /><br />[Using the BizTalk Server Administration console](../core/using-the-biztalk-server-administration-console.md)|  
|Additional updates|<ul><li>The [!INCLUDE[HL7_CurrentVersion_FirstRef_md](../includes/hl7-currentversion-firstref-md.md)] starts the connection to a Line of Business server (LOB), and pushes messages over the connection. The LOB waits for the connection, and then sends the messages. <br/><br/>In previous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versions, the HL7 MLLP receive adapter waits for the LOB server to connect to HL7, and then send messages. The LOB connects to HL7, and then sends messages. </li><br/><li>Office web components (OWC) is now optional in the installation, and listed separately in Programs</li><br/><li>The orchestration instance ID is added to the XLANG FireEvent trace output</li></ul>|   
  
## Deprecated & Removed List  
  
|Program|Status|Replacement|  
|-------------|------------|-----------------|  
|RFID Mobile|Removed|None|  
|RFID Server|Removed|None|  
|SharePoint SSOM/Web Service adapter|Removed|Use the CSOM (Client Side Object Model) option.<br /><br /> [Windows SharePoint Services Adapter](../core/windows-sharepoint-services-adapter.md)<br /><br /> [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)|  
|SOAP adapter|Deprecated|[WCF-BasicHttp Adapter](../core/wcf-basichttp-adapter.md)|  
|Old SQL adapter|Deprecated|WCF-based SQL adapter in the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]|  
|UDDI|Removed|None|  
  
> [!IMPORTANT]
>  Some of these deprecated features may be found in newer versions of BizTalk. In these scenarios, consider the following:  
>   
> -   The feature may be used internally within BizTalk, and is not meant to be used by customer solutions. It is not supported in customer solutions.  
> -   The interfaces may have been modified by Microsoft, and may not be publicly available.

## Next steps
[Hardware & software requirements](hardware-and-software-requirements-for-biztalk-server-2016.md)  
[Setup & install prerequisites](set-up-and-install-prerequisites-for-biztalk-server-2016.md)  
[Install BizTalk](install-biztalk-server-2016.md)