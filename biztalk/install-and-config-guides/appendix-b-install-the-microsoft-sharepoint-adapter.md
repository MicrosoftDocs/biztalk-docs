---
description: "Learn more about: Appendix B: Install the Microsoft SharePoint Adapter"
title: "Appendix B: Install the SharePoint Adapter | Microsoft Docs"
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
BizTalk Server includes a SharePoint adapter that can receive messages or send messages to SharePoint.

The software requirements for [BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) and [BizTalk Server 2013 R2 / 2013](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) list the supported SharePoint versions.

## SharePoint adapter in BizTalk Server 2016

The BizTalk Server setup automatically installs the CSOM redistributable package, just like the File adapter, FTP adapter, and other out-of-the-box adapters.

The SSOM option is removed, and is not available.


## SharePoint adapter in BizTalk Server 2013 and R2
In BizTalk Server 2013 R2 and BizTalk Server 2013, there are two options for the SharePoint adapter.

|SharePoint object model|Description|
|-------------------------|-----------------|
|CSOM - SharePoint Adapter|**Recommended**. The BizTalk Server setup automatically installs the CSOM redistributable package, just like the File adapter, FTP adapter, and other out-of-the-box adapters. <br/><br/>There are no installation requirements on the SharePoint computer.|
|SSOM - SharePoint Web Service|**Deprecated**. On the SharePoint computer, run the BizTalk Server setup, and **only** select the SharePoint Adapter. This setup installs an IIS web service that handles the communication to the SharePoint adapter on BizTalk Server. <br/><br/>In most environments, BizTalk Server and SharePoint are on separate computers.|

##  <a name="BKMK_Before"></a> Before You Install

*  The SharePoint SSOM and CSOM components can both be installed if BizTalk Server 2013 R2 or 2013 and SharePoint are installed on the same computer.

* The BAM Portal only runs in 32-bit mode. If the BAM Portal is installed on a 64-bit machine, ensure that ASP.NET 2.0 32-bit is enabled and the IIS application pool is in 32-bit mode. To do this:

    -   **ASP.NET**: Open IIS Manager, click the **BAM Portal** web site, and then double-click **Handler Mappings**. In the **Enabled** list, confirm **PageHandlerFactory-ISAPI-2.0** is listed.

    -   **Application Pool**: Open IIS Manager, click **Application Pools**, click the **BAMAppPool**, and then click **Advanced Settings**. In **Enable 32-bit applications**, select **True**.

* When installing SharePoint, click the **Server Farm** option, even when you are creating a single-server BizTalk Server and SharePoint installation. A **Server Farm** installation allows you to configure the SharePoint databases.
* [CSOM: SharePoint Services Adapter](../core/csom-sharepoint-services-adapter.md) provides information on configuring a SharePoint receive location and send port.
* BizTalk Server 2010 and previous versions use the Server Side Object Model (SSOM) to connect to SharePoint 2010.

## CSOM and SSOM supported versions
SharePoint support is listed in the following table:

|Version|Supports CSOM|Supports SSOM|
|---|---|---|
|SharePoint 2016|Yes|No|
|SharePoint 2013|Yes|No|
|SharePoint Online|Yes|No|
|SharePoint 2010|Yes|Yes|
|SharePoint 2007 |No|Yes|

##  <a name="BKMK_CSOM"></a> Install the CSOM SharePoint adapter

1.  Use a SharePoint computer based on the following requirements:

    |Version|CSOM Support|
    |---|---|
    |SharePoint 2016<br /><br /> [Install SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)|Yes|
    |SharePoint 2013<br /><br /> [Install SharePoint 2013](https://technet.microsoft.com/library/cc262957.aspx)|Yes|
    |SharePoint Online<br /><br /> [SharePoint Online administration](https://technet.microsoft.com/library/gg132908.aspx)|Yes|
    |SharePoint 2010<br /><br /> [Installation and Deployment for SharePoint Server 2010](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)|Yes|
    |SharePoint 2007 |No|

2.  On the BizTalk Server, install Windows Identity Foundation:

    | Operating System | Info |
    |---|---|
    |Windows 10, Windows 8.1, Windows Server 2016, Windows Server 2012, and Windows Server 2012 R2|Windows Identity Foundation is included with the operating system as a Feature in **Turn Windows features on or off**.|
    |Windows Vista SP1|Download available at [Windows Identity Foundation](https://www.microsoft.com/download/details.aspx?id=17331).|

3.  Install BizTalk Server:

    | Version | Action |
    |---|---|
     | BizTalk Server 2016 | Run BizTalk setup. |
    | BizTalk Server 2013 R2 | Run BizTalk setup, and do **not** check **Windows SharePoint Services Adapter**. |
    | BizTalk Server 2013 | Run BizTalk setup, and do **not** check **Windows SharePoint Services Adapter**. |

##  <a name="BKMK_SSOM"></a> Install the SSOM SharePoint adapter (deprecated)

1.  Use a SharePoint computer based on the following SSOM requirements:

    |Version|SSOM Support|
    |---|---|
    |SharePoint 2016<br /><br /> [Install SharePoint 2016](https://technet.microsoft.com/library/cc262957(v=office.16).aspx)|No|
    |SharePoint 2013<br /><br /> [Install SharePoint 2013](https://technet.microsoft.com/library/cc303424.aspx)|No|
    |SharePoint Online<br /><br /> [SharePoint Online administration](https://technet.microsoft.com/library/gg132908.aspx)|No|
    |SharePoint 2010<br /><br /> [Installation and Deployment for SharePoint Server 2010](https://technet.microsoft.com/library/cc262957(v=office.14).aspx)|Yes|
    |SharePoint 2007<br /><br /> [Installation for SharePoint Server 2007](https://technet.microsoft.com/library/cc262957(v=office.12).aspx) |Yes|

2.  On the SharePoint computer, configure SharePoint, and extend the Default Web Site. When you extend the web site, a separate IIS web site is created that contains the same content but also provides a unique URL and authentication type.

     See [SharePoint 2010: Extend a Web Application](https://go.microsoft.com/fwlink/p/?LinkId=259124).

3.  On the SharePoint computer, run the BizTalk Server installation and **only** check **Windows SharePoint Services Adapter**. This installs the web service. **Do not run the BizTalk configuration**.

4.  On the BizTalk Server, install BizTalk Server. Do **not** check **Windows SharePoint Services Adapter**.

5.  The SharePoint Web Service (SSOM) only runs in 64-bit mode. ASP.NET and the IIS application pool must be in 64-bit mode on the SharePoint computer before installing SharePoint. To do this:

    -   **ASP.NET**: Open IIS Manager, click the web site, and then double-click **Handler Mappings**. In the **Enabled** list, confirm **PageHandlerFactory-ISAPI-2.0-64** is listed.

    -   **Application Pool**: Open IIS Manager, click **Application Pools**, select the application pool, and then click **Advanced Settings**. In **Enable 32-bit applications**, select **False**.

