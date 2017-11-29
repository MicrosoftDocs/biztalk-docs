---
title: "Managing User Mappings for Host Initiated SSO | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aadecc5b-8e66-4a39-a612-c1d2de8eab03
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
---
# Managing User Mappings for Host Initiated SSO
Use the following procedures to create mappings, set credentials (whenever the Validate Password feature is enabled for the affiliate application), and enable/disable mapping.  
  
### To manage user mappings for host initiated SSO using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  In the scope pane, click **Affiliate Applications**.  
  
4.  In the details pane, right-click the affiliate application, and then select the appropriate menu item for your action.  
  
### To create mappings in host initiated SSO using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –createmappings <mapping file>`, where *\<mapping file>* is the name of the XML file.  
  
     The following is a sample mapping file:  
  
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
  
#### To set credentials for individual type affiliate applications using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory. The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -setcredentials <Windows account name> <application name>`.  
  
#### To set credentials for host group type affiliate applications using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command line, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -setcredentials <external account name> <application name>`.  
  
#### To enable mappings for individual type affiliate applications using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -enablemapping <Windows account name> <application name>`.  
  
#### To disable mappings for individual type affiliate applications using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is <drive>:Program FilesCommon FilesEnterprise Single Sign-On.  
  
3.  Type `ssomanage -disablemapping <Windows account name> <application name>`.  
  
#### To enable mappings for host group type affiliate applications using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -enablemapping <external account name> <application name>`.  
  
#### To enable mappings for individual type affiliate applications using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -disablemapping <external account name> <application name>`.  
  
## See Also  
 [Host Initiated Single Sign-On](../esso/host-initiated-single-sign-on.md)