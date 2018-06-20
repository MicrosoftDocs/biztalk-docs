---
title: "Administering Password Synchronization | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5d10141-8df8-48b4-8e77-8789491f600b
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Administering Password Synchronization
You can administer Password Synchronization in Enterprise Single Sign-On (SSO) through either the Microsoft Management Console (MMC) Snap-In or the command line. This topic describes how to perform various administration tasks with adapters.  
  
 The MMC Snap-In displays a list of adapters and their properties. You can right-click an adapter and use the menu to perform the following commands:  
  
- Create adapters  
  
- Set properties  
  
- Update  
  
- Delete  
  
- Enable  
  
- Disable  
  
- Add applications to an adapter  
  
- Delete applications from an adapter  
  
- Reset notification  
  
- Add an adapter to an adapter group  
  
- Delete an adapter from an adapter group  
  
  You can also use the SSOPS command-line utility to administer your password synchronization. Most of the commands in this section are intended for use by an administrator only.  
  
  For many commands, the command output is displayed on the screen in two columns. Because certain screen settings could cause truncation of data, for best results you should change the screen buffer size/Windows size to 120 characters.  
  
  The following table lists the SSOPS commands. Procedures and additional explanation are located throughout the rest of this topic.  
  
|Command|Function|  
|-------------|--------------|  
|-list|Lists existing adapters.|  
|-display|Displays adapter information.|  
|-create|Creates new adapters.|  
|-setprops|Sets properties for adapter.|  
|-update|Updates existing adapters.|  
|-delete|Deletes an existing adapter.|  
|-enable|Enables adapter.|  
|-disable|Disables adapter.|  
|-addapp|Adds application for adapter.|  
|-deleteapp|Deletes application for adapter.|  
|-reset|Resets notification or damping queues.|  
|-addtogroup|Adds adapter to adapter group.|  
|-deletefromgroup|Deletes adapter from adapter group.|  
  
### To list existing adapters  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -list` and press ENTER.  
  
     Adapters and descriptions are listed. (E) denotes that the adapter is enabled, (D) denotes that it is disabled.  
  
### To display adapter information  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -display <adapter name>` and press ENTER.  
  
     The screen output displays information for the specified adapter.  
  
     In addition to name, type, description, computer, and accounts, the following information is displayed.  
  
    |Adapter Flag|Details|  
    |------------------|-------------|  
    |Adapter enabled|Determines whether the adapter is enabled.<br /><br /> Flag: SSO_FLAG_ENABLED<br /><br /> Attribute Name: enableApp<br /><br /> Default: No|  
    |Allow local accounts|Determines whether the App Admin or App Users accounts can be local accounts.<br /><br /> Flag: SSO_FLAG_APP_ALLOW_LOCAL<br /><br /> Attribute Name: allowLocalAccounts<br /><br /> Default: No|  
    |Receive password changes from adapter|Determines whether the adapter is allowed to receive external password changes.<br /><br /> Flag: SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB<br /><br /> Attribute Name: syncFromAdapter<br /><br /> Default: No|  
    |Verify old password|Determines whether the adapter will verify the old password when an external password change is received. If this flag is set, when an external password change is received, the external adapter must supply the old external password in addition to the new external password. The old external password is then compared with the existing external password in the SSO database for that external account. If they match, the password change is accepted. If they do not match, the password change is rejected.<br /><br /> Flag: SSO_FLAG_SYNC_VERIFY_EXTERNAL_CREDS<br /><br /> Attribute Name: verifyOldPassword<br /><br /> Default: Yes|  
    |Change Windows password|Determines whether the Windows password will also be changed when an external password change is received (full sync). ENTSSO always uses the old Windows password stored in the SSO database to change the Windows password to the new value (Windows requires both the old and new password to change a user's password). Therefore, this must be initialized before the Windows password change can succeed. If password sync is configured for a particular mapping, when the external credentials are set via administrative tools (ssomanage or ssoclient -setcredentials), the Windows password that is stored in the SSO database is also set.<br /><br /> Flag: SSO_FLAG_FULL_SYNC_FROM_EXTERNAL_TO_WINDOWS<br /><br /> Attribute Name: changeWindowsPassword<br /><br /> Default: No|  
    |Send Windows password changes to adapter|Determines whether Windows password changes are sent to the external adapter.<br /><br /> Flag: SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL<br /><br /> Attribute Name: syncToAdapter<br /><br /> Default: No|  
    |Send old password to adapter|If Yes, the old password value (from the SSO database) is also sent to the external adapter in addition to the new password value. Some external systems might require both the old and new password values to change the password.<br /><br /> Flag: SSO_FLAG_SYNC_PROVIDE_OLD_EXTERNAL_CREDS<br /><br /> Attribute Name: sendOldPassword<br /><br /> Default: No|  
    |Allow mapping conflicts|Determines whether the adapter will allow mapping conflicts.<br /><br /> A mapping conflict occurs when mappings are not unique. In a single SSO Individual application, mappings are always one-to-one: one Windows account is mapped to exactly one external account and vice versa.<br /><br /> However, it is possible to assign more than one application to an adapter. Thus, it is possible to have a mapping in one application that conflicts with a mapping in the other.<br /><br /> The purpose of this flag is to prevent this from occurring. It is more secure to not allow mapping conflicts unless there is a specific, well understood requirement for this behavior.<br /><br /> Flag: SSO_FLAG_SYNC_ALLOW_MAPPING_CONFLICTS<br /><br /> Attribute Name: allowMappingConflicts<br /><br /> Default: No|  
  
    |Adapter Description|Details|  
    |-------------------------|-------------|  
    |Notification retry count|Default is 1.|  
    |Notification retry delay (in mins)|Default is 5.|  
    |Maximum pending notifications|Default is 8.|  
    |Store notifications (when offline)|True/False.|  
    |Server name|Server name.|  
    |Port number|Port number.|  
    |Applications for this adapter|List of applications currently assigned to the adapter.|  
  
### To create new adapters  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -create <adapter file>` and press ENTER.  
  
     The screen output displays information for the newly created adapter.  
  
### To set properties for an adapter  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -setprops <adapter name>` and press ENTER.  
  
     The screen output displays the properties for the specified adapter. You can edit them if necessary, but new values are not validated.  
  
### To update existing adapters  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -update <adapter file>` and press ENTER.  
  
     Use this command to update the settings and flags for a specified adapter. Do not use this command to set properties; use the **-setprops** command instead.  
  
### To delete an existing adapter  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -delete <adapter name>` and press ENTER.  
  
     The specified adapter is deleted.  
  
### To enable an adapter  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -enable <adapter name>` and press ENTER.  
  
     The specified adapter is enabled.  
  
### To disable an adapter  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -disable <adapter name>` and press ENTER.  
  
     The specified adapter is disabled.  
  
### To add an application to an adapter  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -addapp <adapter name> <application name>` and press ENTER.  
  
     The specified SSO application is assigned to the specified adapter. This means that the passwords for the mappings in that application are now synchronized using this adapter.  
  
     Although multiple applications can be assigned to one adapter, any given application can only be assigned to one adapter.  
  
### To delete an application from an adapter  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -deleteapp <application name>` and press ENTER.  
  
     The specified SSO application is removed from an adapter. (Because an application can only be assigned to one adapter, you do not have to specify the adapter name.)  
  
### To reset notification  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -reset <adapter name | all | damping>` and press ENTER.  
  
     This command clears the damping table and/or notification queues for a single adapter or all adapters, as specified. The damping table stores a 10-minute history of password changes. Before the Enterprise SSO system accepts or sends a password change, it checks the damping table to see whether it has performed the same change recently. If it has, the new change is discarded.  
  
### To add an adapter to an adapter group  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -addtogroup <adapter name> <adapter group>` and press ENTER.  
  
     This command adds the specified adapter to the specified adapter group. Although an adapter can belong to only one adapter group, an adapter group can contain multiple adapters.  
  
### To delete an adapter from an adapter group  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssops -deletefromgroup <adapter name> <adapter group>` and press ENTER.  
  
     This command deletes the specified adapter from the specified adapter group.  
  
## See Also  
 [Password Synchronization](../esso/password-synchronization3.md)