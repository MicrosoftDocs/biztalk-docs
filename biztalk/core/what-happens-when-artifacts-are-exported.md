---
title: "What Happens When Artifacts Are Exported | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exporting, artifacts"
  - "artifacts, exporting"
ms.assetid: accc9a81-01fb-4da7-a5a5-167835d393a2
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# What Happens When Artifacts Are Exported
This topic describes what happens when you export artifacts. There are three ways to export artifacts, which are covered in this topic:  
  
-   Exporting a BizTalk application and its artifacts into a BizTalk .msi (Windows Installer) file  
  
-   Exporting a policy into an .xml file  
  
-   Exporting bindings into an .xml file  
  
## Exporting a BizTalk application  
 When you export a BizTalk application and the artifacts it contains, application configuration information and artifact data is exported into a BizTalk .msi file. Most artifact data is exported from the BizTalk Management database, with the following exceptions:  
  
- Policy data is exported from the Rule Engine database for the group.  
  
- Virtual directory data is exported from the Internet Information Services (IIS) metabase if it does not exist in the Management database. This will be the case when the virtual directory has not been explicitly added to the application (as described in [How to Add a Virtual Directory to an Application](../core/how-to-add-a-virtual-directory-to-an-application.md)) or the application has not been imported into this group from an .msi file that was exported from another BizTalk group.  
  
- Certificate data is exported from the Other People certificate store on the local computer, if it does not exist in the Management database. This will be the case when the certificate has not been explicitly added to the application (as described in [How to Add a Certificate to an Application](../core/how-to-add-a-certificate-to-an-application.md)) or the application has not been imported into this group from an .msi file that was exported from another BizTalk group. Certificates are exported when you export an application with a receive port that has a certificate associated with it. Private keys are removed from certificates on export.  
  
  You can use this .msi file to import the application's artifacts, including all of their data, into an application in another BizTalk group. You can also use this .msi file to install the application on a computer.  
  
## Exporting a policy  
 When you use the administration console to export a policy for either a BizTalk group or application, it generates an .xml policy file containing the policy information. You can import this policy file into another BizTalk group to create the policy there, so that applications in the group can use it. You can also export policy information for an application by using BTSTask. BTSTask, however, does not have a command to export a policy .xml file. Instead, you can export an application .msi file that contains only the policy. You can then import the .msi file into an application in another group.  
  
## Exporting bindings  
 You can use either the administration console or BTSTask to export bindings for a BizTalk group, application, or assembly. When you do this, BizTalk Server generates an .xml file containing the binding information for the group, application, or assembly. When you export bindings, you can also export global party information for the group. You can then either add this binding file to an application or import it into a BizTalk group or application.  
  
## See Also  
 [What Happens to Artifacts During Application Deployment](../core/what-happens-to-artifacts-during-application-deployment.md)   
 [Exporting BizTalk Applications, Bindings, and Policies](../core/exporting-biztalk-applications-bindings-and-policies.md)   
 [Importing BizTalk Applications, Bindings, and Policies](../core/importing-biztalk-applications-bindings-and-policies.md)   
 [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md)