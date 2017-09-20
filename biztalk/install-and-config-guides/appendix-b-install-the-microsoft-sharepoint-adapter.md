---
title: "Appendix B: Install the Microsoft SharePoint Adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f44c6e0a-dcce-4444-8cac-bd403c81a233
caps.latest.revision: 19
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Appendix B: Install the Microsoft SharePoint Adapter
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes a [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] adapter that can receive messages or send messages to [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]. 

This topic describes the SharePoint adapter.  The software requirements for [BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) and [BizTalk Server 2013 R2 / 2013](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) list the supported SharePoint versions.

## SharePoint adapter in BizTalk Server 2016

The BizTalk Server setup automatically installs the CSOM redistributable package, just like the File adapter, FTP adapter, and other out-of-the-box adapters. 

The SSOM option is removed, and is not available.


## SharePoint adapter in BizTalk Server 2013 and R2
In [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013, there are two options for the SharePoint adapter.

|SharePoint object model|Description|  
|-------------------------|-----------------|  
|CSOM - [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Adapter|**Recommended**. The BizTalk Server setup automatically installs the CSOM redistributable package, just like the File adapter, FTP adapter, and other out-of-the-box adapters. <br/><br/>There are no installation requirements on the SharePoint computer.|  
|SSOM - [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Web Service|**Deprecated**. On the SharePoint computer, run the BizTalk Server setup, and **only** select the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Adapter. This setup installs an IIS web service that handles the communication to the SharePoint adapter on BizTalk Server. <br/><br/>In most environments, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] are on separate computers.|  

##  <a name="BKMK_Before"></a> Before You Install  

*  The [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] SSOM and CSOM components can both be installed if [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] or 2013 and [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] are installed on the same computer.  
  
* The BAM Portal only runs in 32-bit mode. If the BAM Portal is installed on a 64-bit machine, ensure that ASP.NET 2.0 32-bit is enabled and the IIS application pool is in 32-bit mode. To do this:  
  
    -   **ASP.NET**: Open IIS Manager, click the **BAM Portal** web site, and then double-click **Handler Mappings**. In the **Enabled** list, confirm **PageHandlerFactory-ISAPI-2.0** is listed.  
  
    -   **Application Pool**: Open IIS Manager, click **Application Pools**, click the **BAMAppPool**, and then click **Advanced Settings**. In **Enable 32-bit applications**, select **True**.  
  
* When installing [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], click the **Server Farm** option, even when you are creating a single-server [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] installation. A **Server Farm** installation allows you to configure the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] databases.  
* [CSOM: SharePoint Services Adapter](../core/csom-sharepoint-services-adapter.md) provides information on configuring a SharePoint receive location and send port.  
* BizTalk Server 2010 and previous versions use the Server Side Object Model (SSOM) to connect to SharePoint 2010. 

## CSOM and SSOM supported versions  
The [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] support is listed in the following table:  
  
||Supports CSOM|Supports SSOM|  
|-|-------------------|-------------------|  
|[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2016|Yes|No|  
|[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2013|Yes|No|  
|[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Online|Yes|No|  
|[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2010|Yes|Yes|  
|[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2007 |No|Yes|  
  
##  <a name="BKMK_CSOM"></a> Install the CSOM SharePoint adapter  
  
1.  Use a SharePoint computer based on the following requirements:  
  
    ||CSOM Support|  
    |-|------------------|  
        |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2016<br /><br /> [Install SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)|Yes|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2013<br /><br /> [Install SharePoint 2013](https://technet.microsoft.com/library/cc262957.aspx)|Yes|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Online<br /><br /> [SharePoint Online administration](https://technet.microsoft.com/library/gg132908.aspx)|Yes|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2010<br /><br /> [Installation and Deployment for SharePoint Server 2010](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)|Yes|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2007 |No|  
  
2.  On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], install Windows Identity Foundation:  
  
    | Operating System | Info |  
    |-|-|  
    |[!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 10, [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 8.1, [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] Server 2016, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], and [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2|Windows Identity Foundation is included with the operating system as a Feature in **Turn Windows features on or off**.|  
    |[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] SP1|Download available at [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331).|  
  
3.  Install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:

    | |  |  
    |-|-|  
     | [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] | Run BizTalk setup. |
    | [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] | Run BizTalk setup, and do **not** check **Windows SharePoint Services Adapter**. |  
    | BizTalk Server 2013 | Run BizTalk setup, and do **not** check **Windows SharePoint Services Adapter**. |
  
##  <a name="BKMK_SSOM"></a> Install the SSOM SharePoint adapter (deprecated)  
  
1.  Use a [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer based on the following SSOM requirements:  
  
    ||SSOM Support|  
    |-|------------------|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2016<br /><br /> [Install SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)|No| 
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2013<br /><br /> [Install SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)|No|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Online<br /><br /> [SharePoint Online administration](https://technet.microsoft.com/library/gg132908.aspx)|No|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2010<br /><br /> [Installation and Deployment for SharePoint Server 2010](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)|Yes|  
    |[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] 2007<br /><br /> [Installation for SharePoint Server 2007](https://technet.microsoft.com/library/cc262957(v=office.12).aspx) |Yes|  
  
2.  On the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer, configure SharePoint, and extend the Default Web Site. When you extend the web site, a separate IIS web site is created that contains the same content but also provides a unique URL and authentication type.  
  
     See [SharePoint 2010: Extend a Web Application](http://go.microsoft.com/fwlink/p/?LinkId=259124).  
  
3.  On the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] computer, run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation and **only** check **Windows SharePoint Services Adapter**. This installs the web service. **Do not run the BizTalk configuration**.  
  
4.  On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Do **not** check **Windows SharePoint Services Adapter**.  
  
5.  The [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Web Service (SSOM) only runs in 64-bit mode. ASP.NET and the IIS application pool must be in 64-bit mode on the SharePoint computer before installing SharePoint. To do this:  
  
    -   **ASP.NET**: Open IIS Manager, click the web site, and then double-click **Handler Mappings**. In the **Enabled** list, confirm **PageHandlerFactory-ISAPI-2.0-64** is listed.  
  
    -   **Application Pool**: Open IIS Manager, click **Application Pools**, select the application pool, and then click **Advanced Settings**. In **Enable 32-bit applications**, select **False**.  

