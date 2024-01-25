---
description: "Learn more about: How to Restore the Certificate Store"
title: "How to Restore the Certificate Store"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Restore the Certificate Store
As a part of recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must restore the certificate store. If you are recovering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Standard Edition, you must use this procedure to restore the certificate store. You do not need to perform this procedure when recovering all other editions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] because the recovery process automatically restores the certificate store for you.  
  
## Prerequisites  
 You must be logged on as a member of the Administrators group to perform this procedure.  
  
### To restore the certificate store (BizTalk Server Standard Edition)  
  
1.  Click **Start**, click **All Programs**, and then click **Internet Explorer**.  
  
2.  On the **Tools** menu, click **Internet Options**.  
  
3.  In the **Internet Options** dialog box, click the **Content** tab, and then click **Certificates**.  
  
4.  In the **Certificates** dialog box, click the **Other People** tab, and then click **Import**.  
  
5.  In the **Certificate Import Wizard**, click **Cancel**.  
  
     This creates the **AddressBook** hive in the registry.  
  
6.  In the **Certificates** dialog box, click **Close**.  
  
7.  In the **Internet Options** dialog box, click **OK**.  
  
8.  Click **File**, and then click **Close** to exit Internet Explorer.  
  
9. Click **Start**, click **Run**, type **regedit**, and then click **OK**.  
  
10. In Registry Editor, navigate to the following registry key:  
  
     **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SystemCertificates**  
  
11. Verify that the **AddressBook** hive is present.  
  
## See Also  
 [Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)
