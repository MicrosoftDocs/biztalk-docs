---
title: "Creating a Well-Formed Message Instance from a PIP | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "message templates"
  - "PIPs, message templates"
ms.assetid: fed3698c-25d9-40ca-878a-60171f425bec
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a Well-Formed Message Instance from a PIP
This topic describes how to produce a well-formed message instance. You can generate a template for a message instance from the Partner Interface Process (PIP). After doing this, you have to modify that template, so that it is well formed, before adding your data.  
  
### To generate a message instance template from the PIP  
  
1. Start **Microsoft Visual Studio 2012**.  
  
2. On the **File** menu, point to **Open**, and then click **Project**.  
  
3. Locate \<*drive*\>\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNetSDK\Schemas, click **RNPIPs.btproj**, and then click **Open**.  
  
4. In Solution Explorer, expand **RNPIPs**, and then right-click the PIP for which you want to create an instance.  
  
5. Click **Generate Instance**.  
  
   > [!NOTE]
   >  This generates a file named after the PIP, with "_output" appended to the file name, and with an .xml extension. A statement in the Output pane indicates where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] generated the instance.  
  
### To modify the message instance template  
  
1. In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, locate the folder holding the XML file, and double-click the file name to open the folder.  
  
2. Add an XML header tag before all other text indicating the version of XML and the encoding. For example:  
  
   ```  
   <?xml version="1.0" encoding="UTF-8" ?>  
   ```  
  
3. After the line that you just added, add a DOCTYPE line indicating the DTD. For example, for a 3A4 Purchase Order Request instance, the line would be as follows:  
  
   ```  
   <!DOCTYPE Pip3A4PurchaseOrderRequest SYSTEM "3A4_MS_V02_02_PurchaseOrderRequest.dtd">  
   ```  
  
   > [!NOTE]
   >  Each message instance must include the DOCTYPE line to be processed.  
  
4. You may now customize this message instance to suit your business needs. Modify the XML instance so that it does not use XML namespaces or namespace prefixes.  
  
## See Also  
 [Programming Guide](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)