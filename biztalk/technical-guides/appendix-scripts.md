---
title: "Appendix: Scripts | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server-2013"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6394321-13c9-4b1d-b529-eba3d53b33c4
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Appendix: Scripts
The following scripts are included in this management pack.  
  
|Script|Purpose|  
|------------|-------------|  
|Microsoft.BizTalk.Server.2013.ArtifactsDiscovery.vbs|This script discovers application artifacts based on $Config/Option$ parameter. Options include<br /><br /> -   All send ports, send port groups in an application, their hosting relations to an application and 'send port group contains send port' relations.<br />-   All orchestrations in an application, their hosting relations to application.<br />-   All receive ports, receive locations in an application, their hosting relation' to an application and 'receive port contains receive location' relations.|  
|Microsoft.BizTalk.Server.2013.ApplicationDiscovery.vbs|This script discovers the following:<br /><br /> -   All applications in a group and 'group hosts application' relations.<br />-   All hosts in a group and 'group hosts host' relations.|  
|Microsoft.BizTalk.Server.2013.BAMAnalysisDiscovery.vbs|This script discovers BAM analysis and alerts components on a computer where BAM runtime component is discovered.|  
|Microsoft.BizTalk.Server.2013.BAMPortalDiscovery.vbs|This script discovers BAM portal configured on a machine having IIS. This also discovers BAM role and the containment of BAM portal in it.|  
|Microsoft.BizTalk.Server.2013.BAMRuntimeDiscovery.vbs|This script discovers BAM runtime component on a computer passed as parameter $Config/ComputerName$. If computer name is not passed then it discovers BAM on a runtime computer with lowest server ID in the management database. This also discovers BAM role and the containment of BAM runtime in it.|  
|Microsoft.BizTalk.Server.2013.BizTalkApplicationServiceDiscovery.vbs|This script discovers all BizTalk application services on a computer along with its hosting relations with runtime role.|  
|Microsoft.BizTalk.Server.2013.BizTalkGroupDiscovery.vbs|This script discovers BizTalk group on a computer passed as parameter $Config/ComputerName$. If computer name is not passed then it discovers group on a runtime computer with lowest server ID in the management database.|  
|Microsoft.BizTalk.Server.2013.BizTalkRoleDiscovery.vbs|This script discovers the BizTalk server roles in a specified computer based on parameter. $Config/Option$. Options include the following:<br /><br /> -   BizTalk runtime role, BizTalk group deployment and containment of runtime in group deployment.<br />-   BizTalk rules engine role, BizTalk group deployment and containment of rules engine in group deployment. BAM role is always discovered with any of the options, and its containment in group deployment.|  
|BizTalkAnalysisDatabaseMonitor.vbs|This script generates monitoring data for availability of SQL analysis database based on connectivity. The monitor states can be either success or error.|  
|BizTalkArtifactConfigurationMonitor.vbs|This script generates monitoring data for BizTalk application artifact configuration. Each artifact will be in one of the three monitoring states success, warning and error.|  
|BizTalkArtifactSuspendedInstancesMonitor.vbs|This script generates monitoring data for BizTalk application artifact runtime state based on number of suspended instances per artifact. Each artifact will be in one of the three monitoring states success, warning, and error.|  
|BizTalkBAMPortalMonitor.vbs|This script generates monitoring data for availability of BAM portal. The monitor states can be either success or error.|  
|BizTalkHostConfigurationMonitor.vbs|This script generates monitoring data for BizTalk host based on the availability of all its host instances (BTSNTSvc.exe). The monitor states can be either success (running >= success limit), warning (running >= warning limit and running < success limit) or error.|  
|BizTalkDatabaseMonitor.vbs|This script generates monitoring data for availability of an SQL database based on connectivity. The monitor states can be either success or error.|  
|BizTalkMultipleDatabaseMonitor.vbs|This script generates monitoring data for availability of a group of SQL databases as a single entity based on connectivity. Monitor states can be either error (primary database not available), warning (some non-primary databases not available) or success (all databases available).|  
|BizTalkHostProbeAction.vbs|This script generates diagnostics data for BizTalk host based on the availability of all its host instances (BTSNTSvc.exe). For error and warning states it shows host instance that are not running.|  
|Microsoft.BizTalk.Server.2013.HostAction.vbs|This script is used to Start/Stop a BizTalk Host.|  
|Microsoft.BizTalk.Server.2013.OrchestrationAction.vbs|This script is used to Start/Stop an orchestration (BizTalk application artifact).|  
|Microsoft.BizTalk.Server.2013.EnableReceiveLocation.vbs|This script is used to Enable/Disable a Receive Location (BizTalk application artifact).|  
|Microsoft.BizTalk.Server.2013.SendPortAction.vbs|This script is used to Start/Stop a Send Port (BizTalk application artifact).|  
|Microsoft.BizTalk.Server.2013.SendPortGroupAction.vbs|This script is used to Start/Stop a Send Port Group (BizTalk application artifact).|