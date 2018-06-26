---
title: "Migration and Upgrade Troubleshooting | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "upgrading, troubleshooting"
  - "troubleshooting, upgrading"
  - "troubleshooting, migrating"
  - "migrating, troubleshooting"
ms.assetid: 6e6c0ff9-7897-4de6-9e9b-b502b3a1785b
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Migration and Upgrade Troubleshooting
## Assemblies need to be undeployed before an upgrade  
  
### Symptom  
 When you attempt to upgrade A4SWIFT, the upgrade process fails.  
  
### Possible Cause  
 The following A4SWIFT assemblies are still deployed when the upgrade is done:  Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration, Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas, Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.  
  
> [!NOTE]
>  You do not have to redeploy Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas. The installation program redeploys that assembly.  
  
### Solution  
 Manually undeploy the four A4SWIFT assemblies in the following order:  
  
- Microsoft.Solutions.FinancialServices.SWIFT.FrrOrchestration  
  
- Microsoft.Solutions.FinancialServices.SWIFT.FrrSchemas  
  
- Microsoft.Solutions.FinancialServices.SWIFT.MrsrService.  
  
  After you have upgraded, redeploy these assemblies (using **BTSTask.exe**) in the reverse order.  
  
## An upgrade removes access permissions for the Service folder  
  
### Symptom  
 After an upgrade to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], the access permission for the %programfiles%\Microsoft BizTalk Accelerator for SWIFT\Service folder is incorrect.  
  
### Possible Cause  
 When you upgrade to [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)], the upgrade process removes access permissions for the A4SWIFT Administrators and A4SWIFT Users groups from the %programfiles%\Microsoft BizTalk Accelerator for SWIFT\Service folder.  
  
### Solution  
 If you encounter this problem, manually set the following access permissions for the Service folder:  
  
|Group or User Name|Permission|  
|------------------------|----------------|  
|A4SWIFT Administrators|Full Control|  
|A4SWIFT Users|Read & Execute|  
  
 To set these permissions, proceed as follows:  
  
 In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, move to *%programfiles%*\Microsoft BizTalk Accelerator for SWIFT\Service.  
  
1.  Right-click the Service folder, click **Properties**, and then click the **Security** tab.  
  
2.  In the Group or user names pane of the Service Properties dialog box, click **Add**, enter ***\<server name\>*\A4SWIFT Administrators**, and then click **OK**.  
  
    > [!NOTE]
    >  If the A4SWIFT Administrators group is a domain group, enter ***\<domain name\>*\A4SWIFT Administrators**.  
  
3.  Repeat step 2 for ***\<server name\>*\A4SWIFT Users**, or **\<*domain name*\>\A4SWIFT Users** if the A4SWIFT Users group is a domain group.  
  
4.  In the Group or user names pane, select **A4SWIFT Administrators**. In the Permissions pane, select **Allow** for **Full Control**.  
  
5.  In the Group or user names pane, select **A4SWIFT Users**. In the Permissions pane, click **Allow** for **Read & Execute**, **List Folder Contents**, and **Read**.  
  
6.  Click **OK**.  
  
## See Also  
 [Troubleshooting: Issues and Resolutions](../../adapters-and-accelerators/accelerator-swift/troubleshooting-issues-and-resolutions1.md)