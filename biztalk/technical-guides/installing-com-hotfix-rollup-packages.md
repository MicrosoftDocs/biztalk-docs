---
title: "Installing COM+ Hotfix Rollup Packages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 587ae3da-db65-4da8-9d3b-89effb91b197
caps.latest.revision: 2
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing COM+ Hotfix Rollup Packages
> [!NOTE]  
>  This topic is applicable only for Windows Server 2003.  
  
 You should install the last version of the Windows Server 2003 COM+ hotfix rollup package and latest version of the Distributed Transaction Coordinator (DTC) rollup package. This is because the packages include many performance and stability fixes.  
  
 You should install these rollups on all computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and on all computers running SQL Server. The rollups are especially important for your BizTalk solution to perform well in high-throughput scenarios.  
  
 The DTC issues that have been fixed are as follows:  
  
- Unexpected DTC shutdown  
  
- Memory fragmentation issues  
  
- DTC may stop responding under load  
  
- DTC may leak memory or stop responding when used with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
- Performance of DTC under load has been improved  
  
## Installing the COM+ Rollup Package  
 COM+ is no longer releasing rollup packages. Follow this information to install the last COM+ package:  
  
-   The final version of the COM+ rollup is the “Windows Server 2003 Post-Service Pack 2 COM+ 1.5 Hotfix Rollup Package 12”. This hotfix will install on any version of Windows Server 2003, even those without a service pack installed. More information about this hotfix can be found in Microsoft Knowledge Base article 934016, ["Availability of Windows Server 2003 Post-Service Pack 2 COM+ 1.5 Hotfix Rollup Package 12"](http://go.microsoft.com/fwlink/?LinkId=158756) (http://go.microsoft.com/fwlink/?LinkId=158756).  
  
## Installing the DTC Rollup Package  
 DTC will be releasing rollup packages independent of COM+. Follow this information to install the latest DTC package:  
  
-   As of this writing, the latest DTC hotfix rollup is “Package 16”. More information about this hotfix can be found in Microsoft Knowledge Base article 958013, ["List of the MS DTC issues that are fixed in Windows Server 2003 MS DTC Hotfix Rollup Package 16"](http://support.microsoft.com/kb/979919) (http://support.microsoft.com/kb/979919).  
  
     The KB article about the latest DTC hotfix rollup package can be found by searching [http://support.microsoft.com](http://support.microsoft.com/) for the phrase (including the quotes):  
  
    ```  
    "MS DTC Hotfix Rollup Package"  
    ```  
  
     The following query does this search for you. Choose the latest one:  
  
     [http://support.microsoft.com/search/default.aspx?query="MS+DTC+Hotfix+Rollup+Package"](http://support.microsoft.com/search/default.aspx?query=%22MS+DTC+Hotfix+Rollup+Package%22)