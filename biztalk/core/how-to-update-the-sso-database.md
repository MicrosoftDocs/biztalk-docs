---
description: "Learn more about: How to Update the SSO Database"
title: "How to Update the SSO Database"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Update the SSO Database
You can change the global information in the SSO database, such as the master secret server identification, the account names, auditing in the database, ticket timeout, and credential cache timeout, by using either the MMC Snap-In or the command line.  
  
## Changing timeouts for the SSO System  
 You can modify two timeouts at the Enterprise Single Sign-On (SSO) system level:  
  
 **Ticket timeout.** This property specifies the length of time for which a ticket SSO issues is valid. To satisfy most of the scenarios in an enterprise that use SSO, the default ticket timeout is 2 minutes. The SSO administrator can change this based on the application requirements.  
  
 **Credential Cache timeout.** This property specifies the credential cache timeout for all SSO Servers. SSO Servers cache the credentials after the first lookup. By default, the credential cache timeout is 60 minutes. The SSO administrator can change this to a suitable value based on the security requirements.  
  
 You change both of these timeouts by updating the SSO database.  
  
 A sample XML file for updating the SSO database is:  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
<secretServer>ComputerA</secretServer>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
<ticketTimeout>2</ticketTimeout>  
<credCacheTimeout>60</credCacheTimeout>  
</globalInfo>  
</sso>  
  
```  
  
#### To change timeouts using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Properties**.  
  
4.  On the **System Properties** dialog box, click the **General** tab.  
  
5.  Enter the appropriate settings, and click **OK**.  
  
#### To update the SSO database using the MMC Snap-In  
  
1.  On the **Start** menu, click **All Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.  
  
2.  In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.  
  
3.  Right-click **System**, and then click **Upgrade Database**.  
  
#### To update the SSO database using the command line  
  
1.  Click **Start**, click **Run**, and then type **cmd**.  
  
2.  At the command line prompt, go to the Enterprise Single Sign-On installation directory. The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage –updatedb \<update file\>**, where **\<update file\>** is the path and name of the file.  
  
    > [!NOTE]
    >  On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.  
  
## See Also  
 [How to Configure the SSO Tickets](../core/how-to-configure-the-sso-tickets.md)   
 [Using SSO](../core/using-sso.md)
