---
title: "Install and configure the management REST APIs | Microsoft Docs"
description: Query the status of the artifacts in your BizTalk environment using management data REST APIs with Feature Pack 1 in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
 ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 39442756-5886-4ddd-b700-3800a237de4a
caps.latest.revision: 8
author: "tordgladnordahl"
ms.author: "tonordah"
manager: "anneta"
---
# Install and configure the management REST APIs in BizTalk Server
Use a Windows PowerShell script to enable REST APIs that remotely manage your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].

## What are Management data APIs
Management data APIs are the endpoints that let you remotely update, add, and query the status of different artifacts in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment. The endpoints are added using REST, and come with a Swagger definition. 

**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, there's a Windows PowerShell script that installs these REST APIs, and their swagger definitions. These APIs make REST calls to remotely manage ports, orchestrations, partners, agreements, pipelines, and more. 

This topic shows you how to install the REST APIs.

## Prerequisites
* Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

* Install IIS on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. In most [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments, IIS is already installed. See [Hardware and Software Requirements for BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).

## Enable the REST APIs

1. Run Windows PowerShell as Administrator (**Start** menu, type **PowerShell**, right click, and select **Run as administrator**). 
2. Browse to the BizTalk folder under **Program Files (x86)/Microsoft BizTalk Server 2016**
3. Run the following command. Be sure to update your `website`, `domain/user`, `password`, and `domain\group` with your values: 

    ```Powershell
    FeaturePack.ConfigureServices.ps1 -Service management -WebSiteName '<Default Web Site>' -ApplicationPool <mgmtServiceAppPool> -ApplicationPoolUser <domain>\<user> -ApplicationPoolUserPassword <password> -AuthorizationRoles '<domain>\<group>, <domain>\<group>'
    ```
4. After you run the script, browse the new IIS application:  
    1. Open your web browser
    2. Browse to **http://localhost/OperationalDataService/swagger**

5. The Swagger definitions loads. You can also change who has access by updating the **web.config** file in the root folder of the Management Application.

The REST APIs are exposed through the machine, and can be accessed and executed by other applications. 


## See also
 [Configure the Feature Pack](../core/configure-the-feature-pack.md)