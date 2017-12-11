---
title: "Transactions2PC Sample | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 346b1221-3ca7-45a9-a485-32b6491b7da3
caps.latest.revision: 3
---
# Transactions2PC Sample
The Transactions2PC sample demonstrates the user of two-phase commit (2PC) transactional processing using .NET transactions.  
  
## Location in SDK  
 \<installation directory>:\Program Files\Microsoft Host Integration Server\SDK\Samples\ApplicationIntegration\WindowsInitiated\Transactions2PC  
  
## File Inventory  
 The following table shows the files in the sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|In the /Transactions2PC folder<br /><br /> Program.cs<br /><br /> Readme-03-VTAM-LU62-Setup.txt<br /><br /> Readme-04-CICS-LU62-Setup.txt<br /><br /> Readme-05-Configure-HIS.txt<br /><br /> Readme-06-TI-Setup.txt<br /><br /> Readme-07-Step-By-Step.txt<br /><br /> Transaction2PC.csproj<br /><br /> Transactions2PC.sln<br /><br /> Transactions2PC.suo|The source code for the samples. The Setup.txt files describe how to set up, configure, and execute the application based on different hosting environments.|  
|In the /Transactions2PC/Properties folder<br /><br /> AssemblyInfo.cs|Contains the assembly information description for the code sample.|  
|In the /Transactions2PC/TIHostApplicationDef folder<br /><br /> GetBAl62.cbl<br /><br /> GetBalance.cbl<br /><br /> TIHostApplicationDef.tiproj<br /><br /> Tx2PCBankingLink.DLL<br /><br /> Tx2PCBankingUserData.DLL<br /><br /> WIPExportedConfig|The support files that describe the remote host system for the sample application.|