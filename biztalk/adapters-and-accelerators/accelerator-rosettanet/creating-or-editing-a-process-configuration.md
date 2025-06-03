---
description: "Learn more about: Creating or Editing a Process Configuration"
title: "Creating or Editing a Process Configuration"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Creating or Editing a Process Configuration
This section describes how to create or edit a process configuration to implement a Partner Interface Process (PIP) in Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. A RosettaNet PIP defines a business-process dialog between two trading partners. In [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], to create a PIP with a partner, you must first create a process configuration. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] uses this profile to store all configuration characteristics of the PIP. You can then use this configuration to create an agreement with the partner.  
  
 For information about process configuration properties, and procedures for creating or editing a process configuration, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
 In creating a new process configuration, you must base the settings on the PIP specification document maintained by the RosettaNet organization. All process configuration settings come from the PIP specifications, and [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] populates most of the settings with default values that are the most typically used values for the fields. You must verify that the settings correspond to the values in the appropriate PIP specification. For more information about how the PIP settings that you enter map to the guidance in the PIP specification, see [Using the PIP Specification to Create a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md).  
  
 The process configuration can be for either RosettaNet or CIDX (Chemical Industry Data Exchange). For information about a CIDX configuration, see [Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md).  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support changing a process configuration while there are active processes. If you do so, the active processes will complete with failures. All new processes will successfully pick up the new configuration settings.  
  
## In This Section  
  
-   [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)  
  
-   [Using the PIP Specification to Create a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)  
  
-   [Authorization and Non-Repudiation Properties](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)  
  
-   [Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)
