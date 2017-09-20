---
title: "How to Deploy BAM Definitions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, definitions [BAM]"
  - "managing [BAM definitions], deploying definitions"
  - "definitions [BAM], deploying"
  - "Deploy-All command [BAM]"
ms.assetid: 02b8888c-6f6c-45dd-8445-6e507a02f5f0
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Deploy BAM Definitions
Administrators use the **deploy-all** BAM Management utility command to deploy a BAM definition from the Excel workbook or the XML definitions file exported from the workbook. When you perform a complete installation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the Configuration Wizard automatically configures the BAM Configuration XML.  
  
> [!NOTE]
>  If multiple users are working with the BAM Add-In for Excel, we recommend that they have the same version of Microsoft Data Access Components (MDAC). Otherwise, compatibility issues may arise. Specifically, if you create a template on a computer with a newer version of MDAC and then attempt to open it on a computer with an older version of MDAC, a compiler error will occur.  
  
> [!NOTE]
>  You can use only one data item (for example, City) per data dimension (for example, Location). You cannot use City again in another data dimension, such as Region.  
  
> [!IMPORTANT]
>  We recommend that you verify the security of BAM Excel workbooks (.xls) before you deploy them. You use Excel on the administration computer to verify the security of BAM Excel workbooks. Before you deploy a workbook, open it and ensure the macro security is set to high, and that there are no warnings.  
  
> [!IMPORTANT]
>  In BAM databases, the “BAM_\<...>” naming convention is reserved for all SQL entities (tables, indexes, stored procedures, roles, etc...). *Do not* use this naming convention to create any SQL entities; such a usage might result in an undefined behavior.  
  
 Before you can deploy a BAM definition XML file, you must ensure that the locale used to create this file matches the locale of the computer on which you are deploying it. For example, if you create the file on a computer running a Japanese version of Microsoft Windows, the computer you deploy the file on must be set to the Japanese locale. If the file and the computer settings do not match, you must switch the computer you use to run the BAM Management utility to the correct locale and you must restart it before running the utility.  
  
> [!NOTE]
>  The BAM definition XML file cannot contain text in multiple languages unless the languages all use the same codepage, or only two languages are included and one of them is English.  
  
 For information about changing locale settings on your computer, see the Help for your operating system.  
  
### To deploy a BAM definition  
  
1.  Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2.  Navigate to the tracking folder by typing **C:\Program Files\Microsoft BizTalk Server \<version>\Tracking** at the command prompt. Press **ENTER**.  
  
3.  Type **bm deploy-all -DefinitionFile:\<BAM definition file>**.  
  
4.  Press **ENTER**.  
  
## See Also  
 [Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md)   
 [BAM Management Utility](../core/bam-management-utility.md)   
 [BAM Security Recommendations](../core/bam-security-recommendations.md)