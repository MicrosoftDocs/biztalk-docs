---
title: "Manage (BizTalk Server Sample) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SSO, examples"
  - "utilities, SSOMANAGE"
  - "examples, SSO"
  - "SSOMANAGE command line utility"
ms.assetid: f738e344-4d81-4557-b399-68b59c413245
caps.latest.revision: 12
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Manage (BizTalk Server Sample)
The Manage Single Sign-On (SSO) sample demonstrates how to construct .xml files that you can use with the ssomanage.exe command-line utility to perform the following types of administration operations:  
  
- Update global information at the SSO system level  
  
- Create affiliate applications  
  
- Create user mappings  
  
  For conceptual information about Enterprise Single Sign-On, see [Using SSO](../core/using-sso.md).  
  
  For a sample that shows how to programmatically configure SSO, such as creating affiliate applications and user mappings, see [HTTPSSO (BizTalk Server Sample)](../core/httpsso-biztalk-server-sample.md).  
  
## What This Sample Does  
 This sample includes pairs of XSD and sample .xml files for each of these types of operations. The values in the sample .xml files are not valid. You must make changes to the values that are appropriate to your specific requirements.  
  
## Where to Find This Sample  
 *\<Samples Path\>*\SSO\Manage\  
  
 The following table shows the files in this sample and describes their purpose.  
  
|File(s)|Description|  
|---------------|-----------------|  
|AffiliateApplication.xml, GlobalInfo.xml, UserMapping.xml|Sample .xml files that you can, after modification, pass as arguments to the command-line utility ssomanage.exe.|  
|AffiliateApplication.xsd, GlobalInfo.xsd, UserMapping.xsd|Schema files for the corresponding .xml files, providing complete descriptions of their possible elements and attributes. You can use these files to validate corresponding .xml files received from other sources.|  
  
## Building and Initializing This Sample  
 Because this sample consists of only XML Schema definition language (XSD) and .xml files, the latter of which you can modify and then pass to the command-line utility ssomanage.exe, there is nothing to build in this sample.  
  
## Running This Sample  
 This sample includes sample .xml files for running the command-line utility ssomanage.exe in the following three different modes:  
  
- **Update global information at the SSO system level.** To perform this type of operation, perform the following steps:  
  
  1. Edit the file GlobalInfo.xml as required for your specific configuration.  
  
  2. Run the ssomanage.exe command-line utility with the appropriate arguments, as follows:  
  
     ```  
     ssomanage –updatedb GlobalInfo.xml  
     ```  
  
     Ensure that you edit the values in the file GlobalInfo.xml to match your environment. For example, the SSO Admin account must be a valid Windows account. Both the SSO Admin account and SSO Affiliate Admin account must be Windows Global Domain Group accounts.  
  
- **Create affiliate applications.** To perform this type of operation, perform the following steps:  
  
- Edit the file AffiliateApplication.xml as required for your specific configuration.  
  
  - Run the command-line utility ssomanage.exe with the appropriate arguments, as follows:  
  
    ```  
    ssomanage –createapps AffiliateApplication.xml  
    ```  
  
    You can create more than one affiliate application at the same time.  
  
- **Create user mappings.** To perform this type of operation, perform the following steps:  
  
  1. Edit the file UserMapping.xmlas required for your specific configuration.  
  
  2. Run the command-line utility ssomanage.exe with the appropriate arguments, as follows:  
  
     ```  
     ssomanage –createmappings UserMapping.xml  
     ```  
  
     You can create more than one mapping for one or more affiliate applications at the same time.  
  
## Comments  
 After making changes to the sample .xml files provided with this sample, especially where such changes involve including sensitive information in the files, ensure that these files are well protected in your file system. For example, ensure that they are not inadvertently placed in a folder that is shared.  
  
## See Also  
 [SSO (BizTalk Server Samples Folder)](../core/sso-biztalk-server-samples-folder.md)