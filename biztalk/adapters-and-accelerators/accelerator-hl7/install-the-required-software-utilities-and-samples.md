---
title: "Install the Required Software, Utilities, and Samples | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: de0cb89d-08bd-48ec-a149-8929e2608df8
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Install the Required Software, Utilities, and Samples
This tutorial requires [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Windows Server, and a custom [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] installation that includes the MLLP Test Tools. Additionally, you should be familiar with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] development in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] and [Learn the HL7 accelerator and the BizTalk tools available](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).
  
 You must have the following utilities and samples installed on your computer:  
  
- **MllpSend Tool**  
  
   This command-line utility sends a message over the Minimal Lower Layer Protocol (MLLP) protocol to an MLLP receive location. You use it to test your tutorial results. For more information, see [MllpSend Tool](../../adapters-and-accelerators/accelerator-hl7/mllpsend-tool.md).  
  
- **MllpPReceive Tool**  
  
   This command-line utility receives messages over the MLLP protocol, serving as a receive-location listener. You use it to test your tutorial results, displaying messages and acknowledgments received. For more information, see [MllpReceive Tool](../../adapters-and-accelerators/accelerator-hl7/mllpreceive-tool.md).  
  
- **Sample Application Accept ACK.txt**  
  
   This sample file contains the text of an application-accept acknowledgment message. The sample works with the MllpReceive tool, which receives and displays messages, then sends back the acknowledgment(s) in the sample file.  
  
  You need to install the two tools and the sample file by using the BTAHL7 Custom installation process. The Typical installation process does not install these tools. To install these tools, run the BTAHL7 custom installation, at the **Custom Setup** screen, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder. For more information, see [Install BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-biztalk-accelerator-for-hl7.md).  
  
## See Also  
 [Preparing to Use the Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)