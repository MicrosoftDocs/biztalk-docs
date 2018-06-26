---
title: "How to Install the Enterprise Single Sign-On Administration Component | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e28ca64-08a1-4b79-9e90-5073ddf4e7ab
caps.latest.revision: 5
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# How to Install the Enterprise Single Sign-On Administration Component
You can install the Enterprise Single Sign-On (SSO) Administration component as a stand-alone feature. This is useful if you need to administer the SSO system remotely. The hardware and software requirements are the same as for a typical Enterprise SSO installation.  
  
 After you install the administration component, you must use either ssomanage.exe or the SSO Administration MMC Snap-In to specify the SSO server that will be used for management. Both processes are included in the procedure that follows.  
  
 Installing the SSO administrative utility (ssomanage.exe) does not create shortcuts on the **Start** menu that let you access the command-line utilities. To run the SSO administrative utilities after installation, you must open a command prompt and navigate to the SSO directory located at Program Files\Common Files\Enterprise Single Sign-On.  
  
### To install the Enterprise Single Sign-On administrative component  
  
1. Perform a custom installation of [!INCLUDE[hisHostIntServNoVersion](../includes/hishostintservnoversion-md.md)], selecting only the Enterprise Single Sign-On administration component.  
  
2. When the installation program finishes, click **Start**, click **Run**, and then type `cmd`.  
  
3. At the command prompt, go to the Enterprise Single Sign-On installation directory.  
  
    The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
4. Do one of the following:  
  
   - Type `ssomanage –server` to specify the SSO server that you want to connect to when you perform administration operations.  
  
     OR  
  
     Type `ssomanage -serverall` to specify the SSO server that all users of this computer will connect to when performing administration operations.  
  
     OR  
  
     Open the ENTSSO Administration MMC Snap-In. The Select SSO Server dialog will appear. Enter or browse to the SSO Server desired. To specify the SSO Server for all users on the machine, select **Set SSO Server for all users**.  
  
## See Also  
 [How to Install the Enterprise Single Sign-On Client Utility](../esso/how-to-install-the-enterprise-single-sign-on-client-utility.md)   
 [Configuring Enterprise Single Sign-On](../esso/configuring-enterprise-single-sign-on1.md)   
 [Installing Enterprise Single Sign-On](../esso/installing-enterprise-single-sign-on.md)   
 [Standard Installation Options](../esso/standard-installation-options.md)