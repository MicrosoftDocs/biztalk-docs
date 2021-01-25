---
description: "Learn more about: Installing the Resolver Service Sample"
title: "Installing the Resolver Service Sample | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fce9bbeb-9377-41af-8ca7-740ce4d1f617
caps.latest.revision: 3
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Installing the Resolver Service Sample
This section describes the process for installing the Resolver Service sample. The Resolver Service depends on the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core solution. Installing the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core automatically copies and installs the core assemblies required by this sample to the correct locations.  
  
 **To install the Resolver Service sample from the solution project**  
  
1.  In Windows Explorer, open the \Source\Samples\ResolverService\Install\Scripts folder.  
  
2.  Double-click the Setup_bin.cmd file.  
  
3.  To confirm successful installation of the sample, or if you are encountering issues when you run applications, you can use the list provided in the following table to check for the presence of the required assemblies and other artifacts.  
  
|Location|Category|Name and version of the component|  
|--------------|--------------|---------------------------------------|  
|BizTalk application GlobalBank.ESB|Orchestrations|(none)|  
|BizTalk application GlobalBank.ESB|Send Ports|(none)|  
|BizTalk application GlobalBank.ESB|Receive Ports|(none)|  
|BizTalk application GlobalBank.ESB|Receive Locations|(none)|  
|BizTalk application GlobalBank.ESB|Schemas|(none)|  
|BizTalk application GlobalBank.ESB|Pipelines|(none)|  
|BizTalk application GlobalBank.ESB|Resources|(none)|  
|BizTalk application GlobalBank.ESB|Policies|ResolveEndpoint|  
|||ResolveMap|  
|BizTalk application GlobalBank.ESB|Maps|(none)|  
|Global assembly cache|Assemblies|(none)|  
|%Program Files%\\BizTalk Server\Pipeline Components|Pipeline components|(none)|
