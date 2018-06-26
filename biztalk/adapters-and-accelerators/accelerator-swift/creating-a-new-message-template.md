---
title: "Creating a New Message Template | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messages, templates"
  - "templates, creating"
  - "creating, templates"
ms.assetid: 8c601d2b-b7a5-4ac4-9d98-fd9960038340
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Creating a New Message Template
You can create a new message template from an existing template. This enables a creator to create a new message instance on a custom form, such as a copy of a standard SWIFT form that already has some data entered into it. Using the new template, the creator does not have to enter all of the data required when using an empty form.  
  
 You create a new template from a message instance that you have generated using the corresponding existing template. You add data to the fields of the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form (as though you were creating a new message instance), and then save the form as a new template.  
  
### To save a modified existing template as a new template  
  
1. In Internet Explorer, open your MRSR site at http://localhost/sites/bassite.  
  
2. Click **Documents**.  
  
3. On the Documents page, click the **New SWIFT MT Messages** document library.  
  
4. On the New SWIFT MT Messages page, click the category containing the template that you want to base your new template on.  
  
5. Point to the template that you want to base your new template on, click the arrow to the right, and then click **Edit in Microsoft Office InfoPath**.  
  
6. In the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] 2007 window, in the message form, enter message data that you want to be part of the template.  
  
7. Click **File**, and then click **Save As**.  
  
8. In the popup indicating that the form contains validation errors, click **Yes**.  
  
9. In the Save As dialog box, select the folder for the template in the **Save in** text box, and then enter a file name in the **File name** text box. Click **Save**.  
  
10. Close the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for the new template.  
  
    > [!NOTE]
    >  To create a message instance from the new template, see [Creating and Submitting a New Message](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md).