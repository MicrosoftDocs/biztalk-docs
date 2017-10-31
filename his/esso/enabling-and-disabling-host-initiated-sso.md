---
title: "Enabling and Disabling Host Initiated SSO | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c50c5f00-8e20-4e29-8432-1b33458df633
caps.latest.revision: 3
---
# Enabling and Disabling Host Initiated SSO
By default, host initiated Single Sign-On (SSO) is not enabled in the Single Sign-On system, and must be enabled by the SSO Administrator.  
  
### To enable host initiated SSO using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Properties**.  
  
4.  Click the **Options** tab.  
  
5.  Select the **Enable host initiated SSO** box, and click **OK**.  
  
### To enable host initiated SSO using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -enable hisso`.  
  
## Disabling SSO applies to the entire SSO system, and all operations related to host initiated SSO are turned off.  
  
#### To disable host initiated SSO using the MMC Snap-In  
  
1.  Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Properties**.  
  
4.  Click the **Options** tab.  
  
5.  Clear the **Enable host initiated SSO** box, and click **OK**.  
  
#### To disable host initiated SSO using the command line  
  
1.  Click **Start**, click **Run**, type `cmd`, and then click **OK**.  
  
2.  At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
     The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage -disable hisso` as appropriate.  
  
## See Also  
 [Host Initiated Single Sign-On](../esso/host-initiated-single-sign-on.md)