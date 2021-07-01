---
description: "Learn more about: Known Issues with Installation, Configuration, and Deployment of EDI and AS2 Solutions"
title: "Known Issues with Installation, Configuration, and Deployment of EDI and AS2 Solutions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2dee03f0-2447-4cc2-90f4-e9b73caa0f39
caps.latest.revision: 26
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Known Issues with Installation, Configuration, and Deployment of EDI and AS2 Solutions
This topic describes known issues with deployment and management of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 solutions.  
  
## Blank Strings Were Imported for Party Properties  
 **Symptom**  
  
 When you imported EDI/AS2 bindings from a binding file into a BizTalk application, sensitive party properties, such as passwords or security/authentication information, were not imported. Those properties were set to blank strings.  
  
 **Possible Cause**  
  
 BizTalk Server will not import the settings of sensitive fields. Importing those settings could create a security issue.  
  
 **Resolution**  
  
 You must manually set the values for EDI sensitive fields after importing the bindings onto another computer.  
  
## FTP Adapter Is Not Supported Natively in 64-bit Mode  
 The FTP adapter cannot run in native 64-bit mode. If you use an FTP adapter in your EDI solution in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you will have to run it on WOW64 on 64-bit Windows.  
  
## Some EDI/AS2 Artifacts Are Still Active After Unconfiguring  
 After you unconfigure the Microsoft EDI/AS2 feature of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], some BizTalk Server artifacts related to EDI and AS2 processing will still be active in the context of the BizTalk group configuration. These artifacts will include EDI and AS2 pipelines and the batching orchestration. As a result, you will still be able to perform basic EDI and AS2 processing even after unconfiguring the Microsoft EDI/AS2 feature. To disable this functionality, you should disable, stop, or delete the ports associated with EDI and AS2 processing.  
  
## You Receive the Error "Failed to Configure EDI/AS2 Status Reporting Functionalities"  
 **Symptom**  
  
 When configuring EDI/AS2 Runtime Status Reporting, you receive error "Failed to Configure EDI/AS2 Status Reporting Functionalities".  
  
 **Possible Cause**  
  
 You can receive this error if BAM Tools was previously configured and then unconfigured.  
  
 **Resolution**  
  
 Configure BAM Tools prior to configuring EDI and/or AS2 status reporting.  
  
## Recovering a Deleted Artifact From the BizTalk EDI Application Requires You to Reconfigure the EDI/AS2 Runtime  
 You should avoid using the BizTalk EDI Application for your own artifacts. This application contains the EDI/AS2 artifacts that are deployed during EDI/AS2 configuration. The recommended approach is to create a separate application and add a reference to BizTalk EDI Application to your application. However, if you delete any EDI/AS2 artifact from BizTalk EDI Application, you can recover from that state by unconfiguring the BizTalk EDI/AS2 runtime from each runtime computer in the group (or by unconfiguring the EDI/AS2 runtime from the group and unconfiguring the EDI/AS2 runtime on each of the reachable runtime computers). It is recommended that you do not delete your databases or the EDI/AS2 BAM activities to prevent data loss. You can then reconfigure the EDI/AS2 runtime on all the runtime computers in the group to recover the deleted EDI/AS2 artifacts.  
  
## Numeric Transaction Set, Group Control and Interchange Control Values May be Truncated  
 The value range fields for interchange control numbers, transaction set reference numbers, and group control numbers allow you to enter values that exceed the maximum allowed value. When you save the configuration, these values will be truncated to the maximum value.  
  
 The maximum value for X12 property fields is 999999999.  
  
 The maximum value for EDIFACT property fields is 99999999999999.  
  
## Control Numbers are Reset to 1 After Upgrade  
 After upgrading, you may notice that all control numbers displayed in the EDI Properties of a party have been reset to the default minimum value of 1 and display a default maximum value of 999999999 (X12) or 99999999999999 (EDIFACT). Any prefix or suffix values will remain the same after upgrade.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] shows the minimum and maximum values to be used for the control number. The current control number will be preserved during upgrade; however it is not displayed in the EDI Properties of the party.  
  
## See Also  
 [Troubleshooting EDI and AS2 Solutions](../core/troubleshooting-edi-and-as2-solutions.md)   
 [BizTalk Server What's New, Install, Configuration, and Upgrade](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)   
 [Configure BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)   
 [Post-configuration steps to optimize your environment](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)
