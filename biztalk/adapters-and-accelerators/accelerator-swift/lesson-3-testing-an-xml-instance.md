---
description: "Learn more about: Lesson 3: Testing an XML Instance"
title: "Lesson 3: Testing an XML Instance"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Lesson 3: Testing an XML Instance
In this lesson, you submit a valid MT103 message in XML format to the file receive ports created in the previous lessons. This action tests the send pipelines that you created in previous modules. Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] writes the output as a flat file to the output folder that you selected for the send port in the previous module.  
  
 You initiate the file receive adapter by copying a SWIFT XML-formatted file to the inbound folder. This action results in the system copying a valid SWIFT flat file to the outbound folder.  
  
### To test an XML Instance  
  
1. In Windows Explorer, open \<*drive*\>:\Labs\Outbound. Verify that this folder contains the {GUID}.xml file that you sent to this folder in [Lesson 1: Submitting a Sample Flat File](../../adapters-and-accelerators/accelerator-swift/lesson-1-submitting-a-sample-flat-file.md) of this module.  
  
2. Copy the XML file, and paste it into \<*drive*\>:\Labs\Inbound\XMLFile. Note the time that you pasted this file.  
  
3. Move to \<*drive*\>:\Labs\Outbound. Verify that there is a file called {GUID}.txt in this folder, and that the time in the Date Modified column for this file corresponds to the time that you pasted the file into \<*drive*\>:\Labs\Inbound\XMLFile.  
  
4. In Notepad, open MT103_Sample.txt in \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\SDK\Tutorial.  
  
5. In another instance of Notepad, open {GUID}.txt in \<*drive*\>:\Labs\Inbound\XMLFile.  
  
6. Verify that the two files in Notepad contain the same content.  
  
   Proceed to [Module 8: Repairing an Invalid Message](https://msdn.microsoft.com/fb531b22-ac7a-4620-b395-87aebf56077d).
