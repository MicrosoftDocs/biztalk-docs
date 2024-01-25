---
description: "Learn more about: How to Configure MIIS for ENTSSO MA"
title: "How to Configure MIIS for ENTSSO MA"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Configure MIIS for ENTSSO MA
When you install the Enterprise Single Sign-On (SSO) Administration feature (either the full version or the Admin-only version) on a computer running Microsoft Identity Integration Server (MIIS), the ENTSSO Management Agent is automatically installed. This means that when you open MIIS, nearly all of the configuration has already been done. The only part missing is the connection information.  
  
 Before starting this procedure, make sure you have the following information available:  
  
-   ENTSSO Server name.  
  
-   UserId and password of the Windows account under which the ENTSSO Management Agent will communicate with the SSO Server.  
  
### To configure the Management Agent within MIIS  
  
1.  Open MIIS, and open the **Identity Manager**.  
  
2.  Open the **Create Management Agent** dialog box.  
  
3.  Select **Enterprise Single Sign-On** in the list.  
  
     This starts the **Create Management Agent Wizard**.  
  
4.  On the **Configure Connection Information** page, in the **Connect To:** field, enter the name of the SSO Server.  
  
5.  Enter the name of the ENTSSO Management Agent. This name must match the name specified in your ENTSSO.xml file.  
  
6.  In the **User** field, specify the domain account that the ENTSSO Management Agent uses to manage mappings in the SSO Database.  
  
     This account should be either a member of the SSO Affiliate Administrators or SSO Administrators accounts within the SSO System.  
  
7.  In the **Password** field, enter the password for that user.  
  
8.  Click **Next**, accepting the defaults until you reach the **Configure Extensions** page.  
  
9. Near **Connection information** for password extension, click **Settings**.  
  
     The **Connection Settings** dialog box appears.  
  
10. In the **Connect To** box, enter the appropriate account. This account must be the same as the service account for the ENTSSO service running on the computer specified.  
  
11. In the **User** and **Password** fields, enter the user name and password for the account.  
  
12. Click **OK**.  
  
13. In the **MIISCreate Management Agent**, click **Finish**.  
  
14. While still in the **Identity Manager**, click the **Tools** menu, and then click **Options**.  
  
     The **Options** dialog box appears.  
  
15. Select **Enable metaverse rules extension**.  
  
16. In the **Rules extension name field**, enter **Microsoft.EnterpriseSingleSignOn.ManagementAgent.dll**.  
  
17. Click **OK** and close MIIS.  
  
## See Also  
 [How to Use the ENTSSO Management Agent](../core/how-to-use-the-entsso-management-agent.md)
