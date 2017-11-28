---
title: "Validating a Message Instance Using the Schema XSD | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "schema XSD"
  - "validating, messages"
  - "messages, validating"
  - "schemas, XSDs"
ms.assetid: c4cbf6b4-130d-4e0f-840b-c8008fafac0b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Validating a Message Instance Using the Schema XSD
This topic describes how to validate a message instance using one of the schema XSD files that Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] has built into the RNPIPs assembly file.  
  
### To validate a message instance using the schema XSD  
  
1.  Start **Microsoft Visual Studio 2012**.  
  
2.  On the **File**, point to **Open**, and then click **Project**.  
  
3.  Locate *\<drive\>*\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\Schemas, click **RNPIPs.btproj**, and then click **Open**.  
  
4.  In Solution Explorer, expand **RNPIPs**, right-click the schema XSD that you want to use to validate a message instance, and then click **Properties**.  
  
5.  In the Property Pages dialog box, click **Input Instance Filename**, locate the folder that contains the file, select the message instance XML file, and then click **Open**.  
  
6.  Click **OK**.  
  
7.  In Solution Explorer, right-click the schema XSD that you want to use to validate a message instance, and then click **Validate Instance**.  
  
## See Also  
 [Modifying an Existing PIP in RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)   
 [Working with PIPs](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)