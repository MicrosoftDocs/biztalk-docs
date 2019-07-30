---
title: "Alignment Problems with Generated COBOL1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b757f5a0-ef53-4c89-8eb3-9311ea67506b
caps.latest.revision: 3
author: "gplarsen"
ms.author: "hisdocs"
manager: "anneta"
---
# Alignment Problems with Generated COBOL
COBOL aligns data elements at the 01 level on double-word boundaries. This practice causes a potential problem in CICS non-DPL applications that use TI-generated data declarations along with error metadata. If you code your COBOL application to receive the error metadata and the input parameters in one RECEIVE, the parameters are placed immediately adjacent to the metadata in memory. However, because the error metadata does not end on a double-word boundary, this action puts the parameters 4 bytes ahead of where the COBOL code expects them.  
  
 You can prevent this problem. When you click either the **Include method name** or the **Include all information** option under **Meta data** on the **Advanced** tab of a method's property page, verify that the mainframe program issues two RECEIVE commands to handle incoming data for the method. The first RECEIVE pulls in the metadata block, and the second RECEIVE pulls in the data for the method. When COBOL is generated for the method, an additional 01 block is generated for the metadata. When the **Include all information** option is selected, you are also expected to create an additional SEND for the metadata before sending the method data back to the Automation client application.  
  
## See Also  
 [Host and Automation Data](../core/host-and-automation-data1.md)