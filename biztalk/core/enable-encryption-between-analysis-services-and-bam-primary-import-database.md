---
title: "How to Enable Encryption Between Analysis Services and the BAM Primary Import Database | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server Analysis Services, enabling encryption"
  - "Primary Import database [BAM], SQL Server Analysis Services"
  - "Primary Import database [BAM], enabling encryption"
  - "SQL Server Analysis Services, Primary Import database [BAM]"
ms.assetid: 8107c557-e57c-4569-9ff7-abcb7a8e5243
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Enable Encryption Between Analysis Services and the BAM Primary Import Database
Encryption is not enabled by default during an installation or upgrade of BAM. To enable encryption, you must set the UseEncryption flag in the BAM configuration XML file to a value of 1.  
  
 You must also enable encryption in SQL Server Analysis Services. For more information about enabling encryption, see [Securing Client Communication with an Analysis Services Instance](http://go.microsoft.com/fwlink/?LinkId=190805) (http://go.microsoft.com/fwlink/?LinkId=190805).  
  
### To enable encryption between SQL Server Analysis Services and the BAM Primary Import Database  
  
1. Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.  
  
2. Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  
3. Type **bm get-config -FileName:\<output file\>**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
4. Press **ENTER**.  
  
5. Open the file configuration file that you have exported in a text editor and change the value of the UseEncryption property flag to 1.  
  
   -   Default Setting: \<Property Name="UseEncryption"\>0\</Property\>  
  
   -   New Setting: \<Property Name="UseEncryption"\>1\</Property\>  
  
6. Update the BAM configuration by typing **bm update-config -FileName:\<config file\>**.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [BAM Management Utility](../core/bam-management-utility.md)