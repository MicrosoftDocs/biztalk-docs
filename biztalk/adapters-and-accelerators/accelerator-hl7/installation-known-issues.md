---
title: "Installation known issues"
description: See the known issues when installing the HL7 accelerator in BizTalk Server.
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: troubleshooting-known-issue
---
# Installation known issues
Useful information that may help you avoid installation problems.  
  
## Prerequisites for installing BTAHL7  
 The prerequisites for installing [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] include the following:  
  
- Basic components of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], including Enterprise Single Sign-On (SSO), Group, and Runtime, should be configured.  
  
- The user installing and configuring BTAHL7 must be a member of the BizTalk Administrators group, and a member of the Administrators group on the SQL Server where the BTAHL7 data is stored.

- The default host should be configured as a FILE receive handler.
  
## SQL Server mixed mode not supported  
The [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] does not support SQL Server in mixed mode.  
  
## Installation succeeds but the BatchControlLocation receive location does not get created. 
This indicates that the default host is not configured as a FILE receive handler.  During install popup with message "Error while creating receive location for outbound batching" will be shown.  

## Repair does not work from uninstall/change  
If user access control (UAC) is enabled, and you try to repair your installation using the control panel, the repair fails. 

Microsoft recommends you keep UAC enabled.

 **Resolution**  
  
 Run the [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] setup.exe, and then select **Repair**.  
  
## See Also  
[Install or upgrade Microsoft BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/install-or-upgrade-microsoft-biztalk-accelerator-for-hl7.md)
