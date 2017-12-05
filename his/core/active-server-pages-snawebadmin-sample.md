---
title: "Active Server Pages SNAWebAdmin Sample | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21a42413-e855-4513-bf1b-7893343f33be
caps.latest.revision: 4
---
# Active Server Pages SNAWebAdmin Sample
The Administration\ASP-SnaWebAdmin folder contains a collection of Active Server Pages (ASP) for use with a Web server application designed to access configuration, management, and status information from the SNA server component of [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]. These sample applications require Microsoft Internet Information Services (IIS) version 5.0 or later with ASP installed. [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] and IIS must be installed and running on the same computer.  
  
 The Windows Management Instrumentation (WMI) ASP samples must be installed into the public directories of the Web server below WWWRoot. Copy the contents of the Admin directory from the SDK\Samples\NetworkIntegration\Administration subdirectory, including SNAWebAdmin subdirectory, to your WWWROOT directory on the Web server. After these files have been copied, you should have a copy of the SNAWMI.ASP, fphover.class, and fphoverx.class files in WWWROOT and a WWWROOT\SNAWebAdmin folder with a series of subdirectories containing several ASP and Graphics Interchange Format (GIF) files.  
  
 You can then run the samples by using Microsoft Internet Explorer, or some other Web browser on the same computer, or a different computer. Type **HTTP://\<computer name>/SNAWMI.asp** in the **Address** box.  
  
 Substitute the network name of the computer hosting the Web server and HIS for the computer name in angle brackets in the URL above. This opens the main page of the SNAWebAdmin ASP application and enables you to select any of the other sample ASP pages. Information about each sample is provided on this Web page. Additional information is available at HTTP://\<*computer name*>/admin/headers/welcome.htm.  
  
 These ASP pages illustrate using WMI to retrieve SNA management and configuration from [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)].  
  
 The two Java class files, fphover.class and fphoverx.class, are redistributable files that are included with Microsoft FrontPage. These files are used in some of the WMI sample scripts instead of a **Submit** button to stop and start services.  
  
 Several subdirectories below SNAWebAdmin must have IIS security enabled (no anonymous access); otherwise the scripts in these subdirectories fail since the anonymous user account by default does not have permissions that would allow it to start or stop services on Microsoft Windows or make changes to the [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)] system. The subdirectories that must have IIS security enabled are as follows:  
  
-   SNASebAdmin\Change  
  
-   SNASebAdmin\Connections  
  
-   SNASebAdmin\Services  
  
-   SNASebAdmin\Status  
  
 It is possible to host these ASP pages on a computer running the Web server that is different from the computer running [!INCLUDE[hishostintegrationserver2009](../includes/hishostintegrationserver2009-md.md)]. However, this requires some changes to the ASP pages to handle connections to a different computer, security, and authentication issues.  
  
## See Also  
 [Administration and Management Samples](../core/administration-and-management-samples.md)