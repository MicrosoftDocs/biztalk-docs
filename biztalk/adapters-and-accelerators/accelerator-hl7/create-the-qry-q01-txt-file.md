---
title: "Create the QRY^Q01.txt File | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ac96587-264f-4743-a90b-4763d330e320
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Create the QRY^Q01.txt File
Use the following procedure to create the patient query QRY^Q01.txt message file. You will use this file later to verify the tutorial scenario.  
  
### To create the QRY^Q01.txt file  
  
1. Open an editor, such as Notepad, and copy the following text into the editor:  
  
   ```  
   MSH|^~\&|ADT||HIS||19990303||QRY^Q01|MSG00001|P|2.4  
   QRD|200307231012|D|I|4387|||20^LI|12233|RES|ALL  
   ```  
  
2. Save the file as **QRY^Q01.txt** in the \<*drive*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial folder, and then close the editor.  
  
   Proceed to [Create the DSR.txt File](../../adapters-and-accelerators/accelerator-hl7/create-the-dsr-txt-file.md).