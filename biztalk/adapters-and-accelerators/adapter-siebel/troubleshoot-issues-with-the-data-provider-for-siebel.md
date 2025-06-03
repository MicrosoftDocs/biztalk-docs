---
description: "Learn more about: Troubleshoot Issues with the Data Provider for Siebel"
title: "Troubleshoot Issues with the Data Provider for Siebel"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: troubleshooting-general
---
# Troubleshoot Issues with the Data Provider for Siebel
This section discusses using troubleshooting techniques to resolve errors that you might encounter when using the [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]).  
  
## Known Issues  
  
### Data Provider for Siebel may give "component 'DataReader Source' (380)" error  
 **Problem**  
  
 While performing a SELECT query on a Siebel business component, the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] may give a "component 'DataReader Source' (380)" error.  
  
 **Cause**  
  
 The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] gives this error if the value received from the Siebel system for a parameter exceeds the maxLength property for the parameter.  
  
## See Also  
[Troubleshoot the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)
