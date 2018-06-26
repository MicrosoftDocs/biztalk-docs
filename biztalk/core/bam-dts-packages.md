---
title: "BAM DTS Packages | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DTS packages, BAM"
  - "BAM, DTS packages"
ms.assetid: bba70d81-6ddf-4f1f-a1f7-d5a5bf453bae
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BAM DTS Packages
An administrator can update parameters for the following BAM DTS packages:  
  
- The **CubeUpdate** Data Transformation Services (DTS) package is always located on the same server as the Star Schema database.  
  
- The **DataMaintenance** DTS package is always located on the same server as the Primary Import database.  
  
  The DTS packages use the following parameters in the BAMConfiguration.xml file.  
  
|Parameter|Description|  
|---------------|-----------------|  
|ConnectionTimeOut|The DTS connection time out value (in seconds) is an integer. If you omit the ConnectionTimeOut parameter, the configuration file uses 60 seconds, the default value.|  
|Encryption|By default, the DTS packages do not encrypt data while they transform the data (Encryption value is 0). Set Encryption to 1 to encrypt the data during transformation.|  
|OwnerPassword|The password for the DTS package owner. DTS package owners can open and modify DTS packages. For information about DTS package owners, see SQL Server Books Online.|  
|UserPassword|The password for the DTS user. DTS package users can run DTS packages. For information about DTS package users, see SQL Server Books Online.|  
  
 The DTS packages use the following naming conventions in the BAMConfiguration.xml file:  
  
- **CubeUpdate** DTS package  
  
   **bam_AN_\<**
   ***CubeName* \>**, where CubeName is the name of the cube. The BAM workbook generates the cube name from the view name. If you modify the cube name in the BAM configuration XML document, the new cube name is used in the DTS package name.  
  
- **DataMaintenance** DTS package  
  
   **bam_DM_\<**
   ***ActivityName* \>**, where ActivityName is the name of the activity.  
  
  You run the CubeUpdate DTS package to aggregate the scheduled aggregation. In the next section, you can specify the time window for real-time data aggregation.  
  
## See Also  
 [BAM Configuration Schema](../core/bam-configuration-schema.md)   
 [BAM Security Recommendations](../core/bam-security-recommendations.md)   
 [Managing BAM](../core/managing-bam.md)