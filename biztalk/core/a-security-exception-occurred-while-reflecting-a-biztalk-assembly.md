---
title: "A security exception occurred while reflecting a BizTalk assembly | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 301b85c7-8e67-482e-8666-67a91ca5c73d
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# A security exception occurred while reflecting a BizTalk assembly
## Details  
  
|                 |                                                                                                                                                                                                                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  Product Name   |                                                                                                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                                                                 |
| Product Version |                                                                                                                                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                                                                             |
|    Event ID     |                                                                                                                                                                         0                                                                                                                                                                          |
|  Event Source   |                                                                                                                                                                         0                                                                                                                                                                          |
|    Component    |                                                                                                                                                                         0                                                                                                                                                                          |
|  Symbolic Name  |                                                                                                                                                                         0                                                                                                                                                                          |
|  Message Text   | A security exception occurred while reflecting BizTalk assembly "{0}". This problem may occur if the assembly is located in a shared network folder. To correct this problem, try one of the following: 1. Copy the assembly and its dependencies to the local machine. 2. Adjust the .NET Configuration Runtime Security policy to permit access. |
  
## Explanation  
 This error will occur when trying to publish a BizTalk assembly that is on a network share without the right .NET policy.  
  
## User Action  
 In addition to taking the specific steps outlined in the error message, copy the assembly locally. Or edit the policy to grant full trust to the local intranet.  
  
 **Using the Code Access Security Policy Tool (Caspol.exe)**  
  
 You can grant trust to a folder on your local computer at the User level with normal user permissions. To grant trust to a network location, you must have administrator privileges and change the security policy at the Machine level. The Machine policy level acts independently of the User policy level, and the machine policy level does not grant full trust to the Intranet zone even if the User policy does. The policy levels must agree.  
  
 **To grant full trust to a local folder**  
  
-   Type the following command in the Visual Studio Command Prompt:  
  
```  
caspol -u -ag All_Code -url   
C:\<FolderName>\<FolderName>\* FullTrust -n "<Name>" -d  
"<Description>"  
```  
  
 **To grant full trust to a network folder**  
  
-   Type the following command in the Visual Studio Command Prompt:  
  
```  
caspol -m -ag LocalIntranet_Zone -url   
\\<ServerName>\<FolderName>\* FullTrust -n "<Name>" -d   
"<Description>"  
```