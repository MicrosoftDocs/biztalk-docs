---
title: "How to Administer Password Synchronization | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Password Synchronization [SSO], applications"
  - "Password Synchronization [SSO], notifications"
  - "applications, Password Synchronization [SSO]"
  - "SSOPS command line utility [SSO]"
  - "administering, Password Synchronization [SSO]"
  - "Password Synchronization [SSO], adapters"
  - "Password Synchronization [SSO], administering"
  - "notifications [SSO]"
  - "Password Synchronization [SSO], SSOPS command line utility"
ms.assetid: e5568cc2-7530-452c-9902-d7ffcad66088
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Administer Password Synchronization
You can administer Password Synchronization through either the MMC Snap-In or the command line.  
  
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
  
  You can also use the SSOPS command line utility to administer your password synchronization. Most of commands in this section are intended for use by an administrator only.  
  
  For many commands, the command output is displayed on the screen in two columns. As certain screen settings may cause truncation of data, for best results you should change the screen buffer size/Windows size to 120 characters.  
  
  The SSOPS commands are listed in the following table. Procedures and further explanation are located throughout the rest of this topic.  
  
|Command|Function|  
|-------------|--------------|  
|-list|Lists existing adapters|  
|-display|Displays adapter information|  
|-create|Creates new adapter(s)|  
|-setprops|Sets properties for adapter|  
|-update|Updates existing adapter(s)|  
|-delete|Deletes an existing adapter|  
|-enable|Enables adapter|  
|-disable|Disables adapter|  
|-addapp|Adds application for adapter|  
|-deleteapp|Deletes application for adapter|  
|-reset|Resets notification or damping queues|  
|-addtogroup|Adds adapter to adapter group|  
|-deletefromgroup|Deletes adapter from adapter group|  
  
### To list existing adapters  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -list** and press Enter.  
  
     Adapters and descriptions will be listed. (E) denotes that the adapter is enabled, (D) denotes that it is disabled.  
  
### To display adapter information  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -display \<adapter name\>** and press Enter.  
  
     The screen output will display information for the specified adapter.  
  
     In addition to name, type, description, computer, and accounts, the following information is displayed.  
  
    |Adapter Flag|Details|  
    |------------------|-------------|  
    |Adapter enabled|Determines whether or not the adapter is enabled.<br /><br /> Flag: SSO_FLAG_ENABLED<br /><br /> Attribute Name: enableApp<br /><br /> Default: No|  
    |Allow local accounts|Determines whether or not the App Admin or App Users accounts can be local accounts.<br /><br /> Flag: SSO_FLAG_APP_ALLOW_LOCAL<br /><br /> Attribute Name: allowLocalAccounts<br /><br /> Default: No|  
    |Receive password changes from adapter|Determines whether or not the adapter is allowed to receive external password changes.<br /><br /> Flag: SSO_FLAG_PARTIAL_SYNC_FROM_EXTERNAL_TO_DB<br /><br /> Attribute Name: syncFromAdapter<br /><br /> Default: No|  
    |Verify old password|Determines whether the adapter will verify the old password when an external password change is received. If this flag is set then with an external password change the external adapter must supply the old external password as well as the new external password. The old external password is then compared with the existing external password in the SSO database for that external account. If they match, the password change is accepted. If they do not match, the password change is rejected.<br /><br /> Flag: SSO_FLAG_SYNC_VERIFY_EXTERNAL_CREDS<br /><br /> Attribute Name: verifyOldPassword<br /><br /> Default: Yes|  
    |Change Windows password|Determines whether or not the Windows password will also be changed when an external password change is received (full sync). ENTSSO always uses the old Windows password stored in the SSO database to change the Windows password to the new value (Windows requires both the old and new password to change a users password), so this must be initialized before the Windows password change can succeed. If password sync is configured for a particular mapping, then when the external credentials are set via administrative tools (ssomanage or ssoclient -setcredentials) the Windows password stored in the SSO database will also be set.Flag: SSO_FLAG_FULL_SYNC_FROM_EXTERNAL_TO_WINDOWS<br /><br /> Attribute Name: changeWindowsPassword<br /><br /> Default: No|  
    |Send Windows password changes to adapter|Determines whether or not Windows password changes will be sent to the external adapter.<br /><br /> Flag: SSO_FLAG_FULL_SYNC_FROM_WINDOWS_TO_EXTERNAL<br /><br /> Attribute Name: syncToAdapter<br /><br /> Default: No|  
    |Send old password to adapter|If Yes, the old password value (from the SSO database) will also be sent to the external adapter as well as the new password value. Some external systems might require both the old and new password values to change the password.<br /><br /> Flag: SSO_FLAG_SYNC_PROVIDE_OLD_EXTERNAL_CREDS<br /><br /> Attribute Name: sendOldPassword<br /><br /> Default: No|  
    |Allow mapping conflicts|Determines whether or not the adapter will allow mapping conflicts.<br /><br /> A mapping conflict occurs when mappings are not unique. In a single SSO Individual application, mappings are always one-to-one: one Windows account is mapped to exactly one external account and vice versa.<br /><br /> However, it is possible to assign more than one application to an adapter. Thus, it is possible to have a mapping in one application that conflicts with a mapping in the other.<br /><br /> This purpose of this flag is to prevent this from occurring. It is more secure to not allow mapping conflicts unless there is a specific, well understood requirement for this behavior.<br /><br /> Flag: SSO_FLAG_SYNC_ALLOW_MAPPING_CONFLICTS<br /><br /> Attribute Name: allowMappingConflicts<br /><br /> Default: No|  
  
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
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -create \<adapter file\>** and press Enter.  
  
     The screen output will display information for the newly created adapter.  
  
### To set properties for an adapter  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -setprops \<adapter name\>** and press Enter.  
  
     The screen output will display the properties for the specified adapter. You can edit them if necessary, but new values are not validated.  
  
### To update existing adapters  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -update \<adapter file\>** and press Enter.  
  
     Use this command to update the settings and flags for a specified adapter. Do not use this command to set properties; use instead the -setprops command.  
  
### To delete an existing adapter  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -delete \<adapter name\>** and press Enter.  
  
     The specified adapter will be deleted.  
  
### To enable an adapter  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -enable \<adapter name\>** and press Enter.  
  
     The specified adapter will be enabled.  
  
### To disable an adapter  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -disable \<adapter name\>** and press Enter.  
  
     The specified adapter will be disabled.  
  
### To add an application to an adapter  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -addapp \<adapter name\> \<application name\>** and press Enter.  
  
     The specified SSO application will be assigned to the specified adapter. This means that the passwords for the mappings in that application will now be synchronized using this adapter.  
  
     While multiple applications can be assigned to one adapter, any given application can only be assigned to one adapter.  
  
### To delete an application from an adapter  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -deleteapp \<application name\>** and press Enter.  
  
     The specified SSO application will be removed from an adapter. (Since an application can only be assigned to one adapter, it is not necessary to specify the adapter name.)  
  
### To reset notification  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -reset \<adapter name &#124; all &#124; damping\>** and press Enter.  
  
     This command clears the damping table and/or notification queues for a single adapter or all adapters, as specified. The damping table stores a 10-minute history of password changes. Before the Enterprise SSO system accepts or sends a password change, it checks the damping table to see if it has performed the same change recently. If it has, the new change is discarded.  
  
### To add an adapter to an adapter group  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -addtogroup \<adapter name\> \<adapter group\>** and press Enter.  
  
     This command adds the specified adapter to the specified adapter group. While an adapter can belong to only one adapter group, an adapter group can contain multiple adapters.  
  
### To delete an adapter from an adapter group  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssops -deletefromgroup \<adapter name\> \<adapter group\>** and press Enter.  
  
     This command deletes the specified adapter from the specified adapter group.  
  
## See Also  
 [Password Synchronization](../core/password-synchronization2.md)