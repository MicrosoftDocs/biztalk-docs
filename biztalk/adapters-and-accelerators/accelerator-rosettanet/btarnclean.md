---
title: "BtarnClean | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BtarnClean utility"
  - "assemblies, undeploying"
  - "BTARN, deleting artifacts"
  - "orchestrations, unenlisting"
  - "ports, stopping"
  - "orchestrations, stopping"
  - "ports, deleting"
  - "BTARN, BtarnClean utility"
ms.assetid: fbecbb88-9b18-4b4b-a286-0bfa783f2320
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# BtarnClean
You use the BtarnClean utility to clean [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] artifacts off a computer. This includes the following actions:  
  
- Stopping and unenlisting all the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] orchestrations  
  
- Stopping and deleting all the associated ports  
  
- Undeploying all the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.BTARN.* assemblies  
  
## Location in SDK  
 \<*drive*\>\Program Files (x86)\ Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK  
  
## Running BtarnClean  
  
#### To run BtarnClean  
  
1.  Open a command prompt.  
  
2.  Move to \<*drive*\>\ Program Files (x86)\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\\.  
  
3.  At the command prompt, type **BtarnClean**, and then press ENTER.  
  
     The utility prompts you to verify that you want to continue.  
  
## Remarks  
 If you run the BtarnClean utility on a computer that has a BizTalk artifact that depends on other artifacts, BtarnClean will indicate that it cannot remove the artifact. The utility will leave that artifact in place and continue to remove other artifacts. You can remove dependencies, and then run the utility again.  
  
 If you run the BtarnClean utility on a computer that is part of a multi-computer deployment, removing the artifacts will affect the rest of the servers in that deployment.  
  
 If you run the BtarnClean utility when multiple processes created by developers exist, the utility will not remove processes that are still in use.  
  
 The BtarnClean utility will not remove a primary receive location if a user's artifact uses that receive location. If this is the case, you must delete the receive port.  
  
 If you want to unconfigure [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] after running the utility, run Configuration.exe /u from the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] folder.  
  
## See Also  
 [Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)
