---
title: "Step 2: Create and Deploy the Sample X12 Schema | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5862168-6621-40ab-8c97-3f317530d34e
caps.latest.revision: 31
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Create and Deploy the Sample X12 Schema
![Step 2 of 11](../core/media/tut-step2-of-11.gif "Tut_Step2_of_11")  
  
 In this step, you build and deploy the project that provides a sample EDI X12 schema that is required to process the incoming EDI X12 interchange transported over AS2. For this tutorial, that schema is X12_00401_864.xsd. You do not need to change the project that is shipped with the AS2 tutorial; you just need to build it.  
  
> [!NOTE]
>  The schema file X12_00401_864.xsd that this tutorial uses is stored in the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas. It has already been added to the Schemas project that you will build and deploy in this step. This schema is different from the X12_00401_864.xsd file downloaded onto your computer by executing MicrosoftEdiXsdTemplates.exe in the folder [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI. The tutorial will only work if you use the X12_00401_864.xsd file that has been added to Schemas.btproj.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To create and deploy the sample X12 schema  
  
1. Start **Microsoft Visual Studio** as an administrator.  
  
2. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Schemas\Schemas.sln.  
  
   > [!NOTE]
   >  This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations. If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).  
  
3. Right-click the Schemas project, and then click **Properties**. Click the **Signing** tab in project designer. Check the **Sign the Assembly** checkbox, for **Choose a strong key name file**, select **\<New…\>** and enter `Schemas.snk`. Clear **Protect my key file with a password** and then click **OK**. Close the project properties dialog and save the changes.  
  
4. Build and deploy Schemas.btproj.  
  
## Next Steps  
 You configure a party and business profile for your organization (Contoso), as described in [Step 3: Configure a Party and Business Profile for Your Organization](../core/step-3-configure-a-party-and-business-profile-for-your-organization2.md).  
  
## See Also  
 [EDI Document Schemas](../core/edi-document-schemas.md)