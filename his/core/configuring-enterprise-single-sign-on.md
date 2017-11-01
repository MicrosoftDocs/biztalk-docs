---
title: "Configuring Enterprise Single Sign-On2 | Microsoft Docs"
ms.custom: ""
ms.date: "10/13/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0f0ec1d-1c11-4a02-80a5-2025c4125ee3
caps.latest.revision: 2
author: MandiOhlinger
manager: anneta
---
# Configuring Enterprise Single Sign-On
The DRDA Service can utilize Enterprise Single Sign-On (ESSO) to better secure the authentication and configuration information.  
  
### Define an ESSO Host-Initiated Affiliate Application  
 You must define an ESSO Affiliate Application, in order to use Windows-initiated SSO for use by multiple client programs and users.  
  
1.  On the **Start** menu, point to **All Programs**, point to **Microsoft Enterprise Single Sign-On**, and click **SSO Administration**. When prompted by **User Access Control**, click **Yes**.  
  
2.  In the **Enterprise Single Sign-On** scope pane, of the **ENTSSO** MMC snap-in, click the **Affiliate Applications** folder; click the **Action** menu, and then **Create Application**.  
  
3.  In the **Enterprise Single Sign-On Application Wizard Welcome** dialog, click **Next**.  
  
4.  In the **General** dialog, enter an **Application name** (e.g. “**SYS1**”), click **Allow local accounts for access accounts**, click **Use SSO Affiliate Admin Accounts for Application Admin accounts**, and then click **Next**.  
  
5.  In the **Accounts** dialog, under the **Application Users** list, click **Add**.  
  
6.  In the **Select Users or Groups** dialog, enter a user account (e.g. DOMAIN\username), click **Check Names**, and then click **OK**. Verify the account is added to the **Application Users** list, and then click **Next**.  
  
7.  In the **Options** dialog, verify the **Affiliate Application** is **Enabled**, that **Allow Windows Initiated SSO** is selected, that **Allow host initiated SSO** is selected, and that **Verify external credentials** is selected. Click **Next** to continue.  
  
8.  In the **Fields** dialog, verify the **Number of fields** is the default two (**2**). Optionally, select **Credentials are Windows credentials** (to increase the security with host-initiated SSO). Click **Create** to continue.  
  
9. In the **Completing the Application Wizard** dialog, verify that you successfully created the Application, and then click **Finish**.  
  
10. In the **Enterprise Single Sign-On** scope pane, of the **ENTSSO** MMC snap-in, click the **Affiliate Applications** folder; click the newly-created Affiliate Application (e.g. “**SYS1**”), click the **Action** menu, click **New Mapping**.  
  
11. In the **Create New Mapping** dialog, enter a **Windows user** (e.g. DOMAIN\username that is authorized to access SQL Server via the DRDA Service on behalf of the External user), enter an **External user** (e.g. “**HISDEMO**” account authorized to access “**SYS1**” DB2 server and SQL Server via the DRDA Service), click **Set credentials for new mapping**, and then click **OK**.  
  
12. In the **Set Credentials** dialog, enter a valid DB2 server password (e.g. “**HISDEMO**”) in the **Password** and **Confirm** edit boxes, and then click **OK**.  
  
13. In the **Enterprise Single Sign-On** scope pane, of the **ENTSSO** MMC snap-in, click the **Affiliate Applications** folder, verify the newly-created Affiliate Application (e.g. “**SYS1**”) is Enabled. Click the Affiliate Application (e.g. “**SYS1**”), and verify in the results pane (list of Windows users on right side of dialog) is enabled.  
  
### Set the Local Security Policy for ESSO Application Admin Account  
 You must define an ESSO Affiliate Application, in order to use Windows-initiated SSO for use by multiple client programs and users.  
  
1.  On the **Start** menu, point to **All Programs**, point to **Administrative Tools**, and click **Local Security Policy**. When prompted by **User Access Control**, and then click **Yes**.  
  
2.  In the Security settings pane, navigate to User Rights Assignment under Local Policies.  
  
3.  Click **Access Credential Manager as a trusted caller**, right-click to select **Properties**. In the **Access Credential Manager as a trusted caller** dialog, click **Add User or Group**. In the **Select Users or Groups** dialog, enter the **Application Admin accounts** user account (DOMAIN\username), click **Check Names**, and then click **OK**. Verify the account is added to the **Application Users** list, and then click **OK**.  
  
4.  Click **Enable computer and user accounts to be trusted for delegation**, right-click to select **Properties**. In the **Enable computer and user accounts to be trusted for delegation** dialog, click **Add User or Group**. In the **Select Users or Groups** dialog, enter the **Application Admin accounts** user account (DOMAIN\username), click **Check Names**, and then click **OK**. Verify the account is added to the **Application Users** list, and then click **OK**.  
  
5.  Click **Act as part of the operating system**, right-click to select **Properties**. In the **Act as part of the operating system** dialog, click **Add User or Group**. In the **Select Users or Groups** dialog, enter the **Application Admin accounts** user account (DOMAIN\username), click **Check Names**, and then click **OK**. Verify the account is added to the **Application Users** list, and then click **OK**.