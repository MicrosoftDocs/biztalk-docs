---
title: Upgrade RosettaNet Accelerator (BTARN) in BizTalk Server | Microsoft Docs"
description: Follow the upgrade steps to update BTARN to the current version in BizTalk Server
author: MandiOhlinger
manager: anneta

ms.date: "06/08/2017"
ms.prod: "biztalk-server"

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 
ms.author: mandia
---

# Upgrade the RosettaNet accelerator

## Upgrade overview
You can upgrade the previous version of the BizTalk Accelerator for RosettaNet (BTARN) installation to the current version. The upgrade process involves upgrading BizTalk Server, and then upgrading BTARN.  
  
 You can upgrade from the previous version of BTARN to a by running the BTARN installation program. The setup migrates the BTRAN configuration information to the current version.  
  
 In a multi-server BTARN environment, you should upgrade all BizTalk Servers first, and then to BTARN. Migrate your servers in the following order:  
  
- The server hosting the BizTalk Group  
  
- Each processing node  
  
- The BAM portal server  
  
  In the BTARN upgrade process, ensure you do the following:  
  
- Check if the SQL Server (MSSQLSERVER) service is running.  
  
- Do not run a silent installation.  
  
## Upgrade steps  
  
1.  Upgrade BizTalk Server. See [BizTalk Server What's New, Installation, Configuration, and Upgrade](../../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).
  
2.  Back up the BTARN database and BTARN message schemas.  
  
    > [!NOTE]
    >  You should back up the BTARN database for safety reasons. The installation program migrates the BTRAN database to the newer version.  
  
3.  Back up any files under the *<drive\>*:\Program Files\\Microsoft BizTalk Accelerator for RosettaNet folder that you have made changes to, for example, files in the SDK.  
  
4.  Undeploy any projects or assemblies that have references to one or more of the previous versions of BTARN assemblies.  
  
5.  In Visual Studio, manually undeploy all BTARN assemblies, in the following order:  
  
    -   Microsoft.Solutions.BTARN.CommonTypes  
  
    -   Microsoft.Solutions.BTARN.GlobalSchemas  
  
    -   Microsoft.Solutions.BTARN.PipelineReceive  
  
    -   Microsoft.Solutions.BTARN.PipelineSend  
  
    -   Microsoft.Solutions.BTARN.PrivateInitiator  
  
    -   Microsoft.Solutions.BTARN.PrivateResponder  
  
    -   Microsoft.Solutions.BTARN.PublicInitiator  
  
    -   Microsoft.Solutions.BTARN.PublicResponder  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv11  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv20  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNPIPs  
  
6.  Run the BTARN installation. See [Install and configure the RosettaNet accelerator](install-configure-biztalk-accelerator-for-rosettanet.md).
  
7.  Use **BTSTask.exe** (\Program Files\Microsoft BizTalk Server) to manually redeploy the BTARN assemblies in the following order:  
  
    -   Microsoft.Solutions.BTARN.CommonTypes  
  
    -   Microsoft.Solutions.BTARN.GlobalSchemas  
  
    -   Microsoft.Solutions.BTARN.PipelineReceive  
  
    -   Microsoft.Solutions.BTARN.PipelineSend  
  
    -   Microsoft.Solutions.BTARN.PrivateInitiator  
  
    -   Microsoft.Solutions.BTARN.PrivateResponder  
  
    -   Microsoft.Solutions.BTARN.PublicInitiator  
  
    -   Microsoft.Solutions.BTARN.PublicResponder  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv11  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv20  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNPIPs  
  
    > [!NOTE]
    >  For more information about **BTSTask.exe**, see the "BTSTask Command-line Reference" topic in BizTalk Server Help.  
  
8.  Rebuild any projects or assemblies that have a reference to one or more of the [BTARN assemblies. Use **BTSTask.exe** to manually redeploy these projects.  
  
9. Upgrade the virtual folders in IIS from ASP.NET 2.0 to ASP.NET 4.0 for the following:  
  
    -   BTARNApp  
  
    -   BTARNHttpReceive  
  
10. Restart the computer to apply any modifications done.  
  
