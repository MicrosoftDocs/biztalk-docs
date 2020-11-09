---
title: "What's New in BizTalk Server 2020 | Microsoft Docs"
description: Changes and improvements, including feature packs, adapters, security, tracking, performance, and more in BizTalk Server 2020
ms.custom: "biztalk-2020"
ms.prod: biztalk-server
ms.date: "02/13/2020"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---

# What's New in BizTalk Server 2020

Read about what's new in BizTalk Server 2020.
  
## New in BizTalk Server 2020  

|Feature|Description|  
|-------------|-----------------|  
|Support for newer platforms|BizTalk Server 2020 adds support for the following Microsoft platforms:<br /><br /> -   Visual Studio 2019 (Enterprise and Professional editions are supported)<br />-   Windows Server 2019, Windows Server 2016, Windows 10<br />-   SQL Server 2019, SQL Server 2017, SQL Server 2016 SP2<br />-   Office 2019, Office 2016<br/><br/>[Hardware and Software Requirements for BizTalk Server 2020](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2020.md)|
| Analytics | Operational Data Monitoring and Analytics. <br/>Leveraging the power of Azure (Application Insight and Event Hub) for deep data storage and Power BI for reporting and viewing of data. <br/><br/>[Send tracking data to Azure](../core/send-tracking-data-to-azure-application-insights-using-biztalk-server.md)<br />[Configure data feed for Power BI](../core/operational-data-service.md)|
| Application Lifecycle Management with VSTS | Using Visual Studio Team Services, you can define multi-server deployments of BizTalk Server 2020, and then maintain those systems throughout the application lifecycle. <br/><br/>[Configure automatic deployment using VSTS](../core/configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)|
| Management APIs | Manage your environment remotely using the new REST APIs with full Swagger support. <br/><br/>[REST API reference](https://docs.microsoft.com/rest/api/biztalk/?view=rest-biztalk)|
|Support for Always Encrypted|Use the WCF-SQL adapter to connect to SQL Server secure Always Encrypted columns. <br/><br/>[Query Always Encrypted database in SQL Server](../adapters-and-accelerators/adapter-sql/key-features-in-biztalk-adapter-for-sql-server.md)|  
|Advanced Scheduling|New and improved scheduling capabilities in Adapters.<br/><br/>[Configure time zone and recurrence](../core/how-to-configure-scheduling-for-a-receive-location.md)|  
|Backup to Azure Blob Storage|When deploying BizTalk Server to Azure VMs, you can backup BizTalk Server databases to Azure blob storage.<br/><br/>[Configure the Backup Job](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
| Adapter for Service Bus v2 | 	When using the Service Bus Adapter, you can utilize Azure Service Bus Premium for enterprise-scale workloads. <br/><br/>[SB-Messaging Adapter](../core/sb-messaging-adapter.md)|
| Transport Layer Security 1.2 | Securely deploy BizTalk Server using industry-standard TLS 1.2 authentication and encryption.|
| FIPS Compliance | Configure, deploy and run BizTalk Server on machines where [FIPS security policy](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing) is enabled.|
|API Management| 	Publish Orchestration endpoints using Azure API Management, enabling organizations to publish APIs to external, partner and internal developers to unlock the potential of their data and services.<br/><br/>[Connect to Azure API Management](../core/connect-to-azure-api-management.md)|  
| Event Hubs Adapter | 	Using the new Event Hub Adapter, BizTalk Server can send and receive messages with Azure Event Hubs, where BizTalk Server can function as both an event publisher and subscriber, as part of a new Azure cloud-based event-driven application.<br/><br/>[Event Hubs adapter](../core/event-hubs-adapter.md)|
| Office 365 Adapters | Leverage the power of BizTalk in newer office automation workflows by integrating with Adapters that allows you to send or receive Office 365 emails, receive or transmit Office 365 calendar events and create Office 365 contacts.<br/><br/>[Office 365 Outlook Email adapter](../core/office365-mail-adapter.md)<br/>[Office 365 Outlook Calendar adapter](../core/office365-calendar-adapter.md)<br/>[Office 365 Outlook Contact adapter](../core/office365-contact-adapter.md)|
|Group Managed Service Accounts|Extend windows GMSA support to BizTalk operations and services. <br/><br/>[Using Group Managed Service Account](../core/gmsa-config.md)|  
|Blob Adapter|Send and Receive messages to/from Azure Blob Storage. <br/><br/>[Azure Blob storage adapter](../core/azure-blob-adapter.md)|  
|Audit Log|Making BizTalk further secure by maintaining audit trails of all management operation.<br/><br/>[Configuring and Viewing Audit Logs](../core/audit-management-operations.md)||  
|New Read Only Operator role|Brand new read only operator role to facilitate dev ops model, where access to production stamp is provided without the ability to update anything. <br/><br/>[BizTalk Server Read Only Users group](../core/managing-biztalk-server-security.md#biztalk-server-groups)|  
|XSLT 3.0|New extensible model for runtime map execution, out of box wiring to work with Saxon XSLT3.0. <br/><br/>[XSLT Transform Engine](https://docs.microsoft.com/biztalk/core/technical-reference/xslt-transform-engine-grid-property)<br/>[XSLT custom transform implementation](https://docs.microsoft.com/biztalk/core/technical-reference/xslt-custom-transform-implementation)|  
|Additional updates|<ul><li>Move to new long term supported Microsoft OLEDB Driver for SQL Server. </li><br/><li>Support for SSO Affiliate applications in SFTP adapter.</li><br/><li>SQL Availability Group support for BAM DTS Package via SSIS Catalog.</li><br/><li>Partially disabled receive locations.<br/>[How to Enable Receive Location Fault Tolerance](../core/how-to-enable-receive-location-fault-tolerance.md)</li><br/><li>Throughput improvements for Dynamic Send Ports with Ordered Delivery.</li></ul>|   
  
## Deprecated & Removed List  
  
| Program |   Status   |  Replacement |
|---|---|---|
| Samples |  Removed   | Removed from BizTalk Server installation.|
| POP3 and SMTP adapters |  Deprecated   | Office 365 adapters |
| Support for ACS authentication in adapters |  Removed   | SAS authentication |
| SOAP adapter | Deprecated | [WCF-BasicHttp Adapter](../core/wcf-basichttp-adapter.md) |
| Old SQL adapter | Removed | [WCF-SQL Adapter](../adapters-and-accelerators/adapter-sql/microsoft-biztalk-adapter-for-sql-server-documentation.md) |
| BPEL support |  Deprecated   | None  |
| JDE OneWorld adapter  |  Deprecated   | None |
| OWC redist |  Removed   | None  |
| BAM Portal |  Deprecated   | None |
| WCF-NetTcpRelay adapter |  Deprecated   | None |
  
> [!IMPORTANT]
> Some of these deprecated features may be found in newer versions of BizTalk. In these scenarios, consider the following:  
>
> - The feature may be used internally within BizTalk, and is not meant to be used by customer solutions. It is not supported in customer solutions.  
> - The interfaces may have been modified by Microsoft, and may not be publicly available.

## Next steps

[Hardware & software requirements](hardware-and-software-requirements-for-biztalk-server-2020.md)  
[Setup & install prerequisites](set-up-and-install-prerequisites-for-biztalk-server-2020.md)  
[Install BizTalk](install-biztalk-server-2020.md)
