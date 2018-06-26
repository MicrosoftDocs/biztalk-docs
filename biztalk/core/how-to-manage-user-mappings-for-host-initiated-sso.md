---
title: "How to Manage User Mappings for Host Initiated SSO | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "maps, host initiated SSO"
  - "host initiated SSO, user maps"
ms.assetid: 6b05249e-da35-475b-9c23-5eb556013d57
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Manage User Mappings for Host Initiated SSO
Use the following procedures to create mappings, set credentials, and enable or disable mapping.  
  
### To manage user mappings for host initiated SSO using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  In the scope pane, click **Affiliate Applications**.  
  
4.  In the details pane, right-click the affiliate application, and then choose the appropriate menu item for your action.  
  
### To create mappings in host initiated SSO using the command line  
  
1. On the **Start** menu, click **Run**.  
  
2. In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3. At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4. Type **ssomanage –createmappings \<mapping file\>**, where **mapping file>** is the name of the xml file.  
  
   > [!NOTE]
   >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
    A sample mapping file is shown below:  
  
   ```  
   <SSO>  
     <mapping>  
       <windowsDomain>DomainName</windowsDomain>  
       <windowsUserId>UserA</windowsUserId>  
       <externalApplication>SSOApplication</externalApplication>  
   <externalUserId>ExternalUserID that corresponds to UserA</externalUserId>  
     </mapping>  
   </SSO>  
  
   ```  
  
   When the Validate Password feature is enabled for the affiliate application, it is necessary to set credentials, as follows:  
  
#### To set credentials for individual type affiliate applications using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -setcredentials \<Windows account name\> \<application name\>**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
#### To set credentials for host group type affiliate applications using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -setcredentials \<external account name\> \<application name\>**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
#### To enable mappings for individual type affiliate applications using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -enablemapping \<Windows account name\> \<application name\>**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
#### To disable mappings for individual type affiliate applications using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -disablemapping \<Windows account name\> \<application name\>**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
#### To enable mappings for host group type affiliate applications using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -enablemapping \<external account name\> \<application name\>**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
#### To disable mappings for individual type affiliate applications using the command line  
  
1.  On the **Start** menu, click **Run**.  
  
2.  In the **Run** dialog box, type **cmd**, and then click **OK**.  
  
3.  At the command line, go to the Enterprise Single Sign-On installation directory. The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage -disablemapping \<external account name\> \<application name\>**.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [Host Initiated SSO](../core/host-initiated-sso.md)