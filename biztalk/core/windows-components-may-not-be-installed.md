---
title: "Windows components may not be installed | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc78ac0a-ee21-4633-afb3-1357efd29903
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Windows components may not be installed
## Details  

|                 |                                                                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                           |
| Product Version |                                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                       |
|    Event ID     |                                                                   0                                                                    |
|  Event Source   |                                                                   0                                                                    |
|    Component    |                                                                   0                                                                    |
|  Symbolic Name  |                                                                   0                                                                    |
|  Message Text   | The following Windows component may not be installed: Application Server -&gt; Internet Information Services (IIS) -&gt; Common Files. |

## Explanation  
 This error will occur when publishing is attempted without Internet Information Services (IIS) installed on the local computer.  

## User Action  
 For Windows 7 and Windows Vista SP2, Install IIS on the local machine and configure IIS as follows:  

1. Click **Start**, click **Control Panel**, and click **Programs**.  

2. Click **Turn Windows features on and off**. The Windows Features Wizard appears.  

3. To add, check the IIS component.  

   For [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], Install IIS on the local machine and configure IIS as follows:  

4. Click **Start**, click **Control Panel**, and click **Administrative Tools**.  

5. Click **Server Manager**. The Server Manger window appears.  

6. Click **Add Roles**, Add Roles Wizard appears.  

7. To add, Select IIS component.
