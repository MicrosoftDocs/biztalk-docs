---
title: "IIS Application Pools and Web Sites | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "application pools [IIS Manager]"
  - "IIS, application pools"
  - "IIS, Web sites"
ms.assetid: 5299c33d-fd21-4dce-a6ab-5f7e12b96527
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IIS Application Pools and Web Sites
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] includes the following Internet Information Services (IIS) Application pools and virtual applications.  
  
## Application Pools  
  
|Application Pool|Default Application Pool Identity|Description|  
|----------------------|---------------------------------------|-----------------|  
|BAMAppPool|*User-defined*|Application pool for the BAM Portal.|  
|BTSSharePointAdapterWSAppPool|*User-defined*|Application pool for the Windows SharePoint Service adapter Web service.|  
|STSWebServiceAppPool|*User-defined*|Application pool for the Trading Partner Management tools.|  
|TpmWSAppPool|*User-defined*|Application pool for the TPM Management Web service.|  
  
## Virtual Applications  
  
|Virtual Application|Default Application Pool|Description|  
|-------------------------|------------------------------|-----------------|  
|BAM|BAMAppPool|Virtual application which hosts the BAM Portal components (pages, images, precompiled code, and other resources). This virtual application calls in to the BAMManagementService application to communicate with the BAM databases. **Note:**  To brand the BAM Portal, you can modify the contents of this application.|  
|BAMManagementService|BAMAppPool|Virtual application which hosts the BAMManagementService web service. This web service is used by the BAM Portal application to communicate with the BAM Primary Import Tables (PIT). The communication with the database is done using impersonated credentials stored in the registry which is created during configuration. Methods exposed by this web service can be used by custom clients to get views and their details, related activities, and pivot table layouts for any user. They can also be used to manage alerts in the database.|  
|BTSharePointAdapterWS|BTSSharePointAdapterWSAppPool|Virtual application which hosts the Windows SharePoint Service adapter Web service.|  
  
## See Also  
 [Installation Overview for BizTalk Server 2013 and 2013 R2](../Topic/Installation%20Overview%20for%20BizTalk%20Server%202013%20and%202013%20R2.md)   
 [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)