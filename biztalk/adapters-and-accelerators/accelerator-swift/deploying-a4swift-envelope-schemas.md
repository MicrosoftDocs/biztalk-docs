---
title: "Deploying A4SWIFT Envelope Schemas | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "deploying, envelope schemas"
  - "A4SWIFT, deploying envelope schemas"
  - "envelope schemas"
  - "schemas, envelope schemas"
ms.assetid: 6440608c-d30d-4d82-827a-8a4b2738db85
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Deploying A4SWIFT Envelope Schemas
You must include envelope schemas in schema projects whenever you set up Message Repair and New Submission. An envelope schema, such as EnvelopeMT103.xsd, is required to write to MRSR site.  
  
 **Summary**  
  
 Add envelope schemas to your project, as follows:  
  
- In Visual Studio, to the project that contains your message schemas, add an envelope schema for each message schema.  
  
- Add a reference to RuntimeSchemas.dll to any project that contains one or more envelope schemas.  
  
  > [!NOTE]
  >  Adding a reference to RuntimeSchemas.dll is required for an [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] project only when you have added an envelope schema for Message Repair and New Submission to the project.  
  
- Add the Unparsed Message envelope schema (EnvelopeUnparsedMessage.xsd) to the project.  
  
### To add a SWIFT envelope schema  
  
1.  In Solution Explorer of Visual Studio, open your schemas project.  
  
2.  Right-click **References**, and then click **Add Reference**.  
  
3.  In the Add Reference dialog box, click the **Browse** tag.  
  
4.  In the Select Component dialog box, open the **Look in** drop-down list. Move to ***\<drive\>*:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\Assemblies**. Select **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** from the list of assemblies, and then click **Add**.  
  
5.  In the **Add Reference** dialog box, click **OK**.  
  
6.  Right-click your project, point to **Add**, and then click **Add Existing Item**.  
  
7.  In the Add Existing Item dialog box, in the **Look in** drop-down box, move to **\<drive\>:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Categoryn\MTxxx**. Select the envelope schema, for example, **EnvelopeMT103.xsd**, and then click **Add**.  
  
     In the Add Existing Item dialog box, in the **Look in** drop-down box, move to. Select the envelope schema, for example, EnvelopeMT103.xsd, and then click Add.  
  
    > [!NOTE]
    >  A4SWIFT adds the envelope schema for your project, as shown in Solution Explorer.  
  
8.  In Solution Explorer, right-click your project, point to **Add**, and then click **Add Existing Item**.  
  
9. If using the Message Repair and New Submission feature, in the Add Existing Item dialog box, in the **Look in** drop-down box, move to **\<*drive*\>:\Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Unparsed Message**. Select **EnvelopeUnparsedMessage.xsd**, and then click **Add**.  
  
10. In Solution Explorer, right-click the project name, and then click **Build**.  
  
11. In Solution Explorer, right-click the project name, and then click **Deploy**.