---
title: "How to Configure ILM for ENTSSO MA | Microsoft Docs"
ms.custom: ""
ms.date: "10/27/2016"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b4dc46-0ea6-4145-92d3-63cc6f8e5f3d
caps.latest.revision: 6
---
# How to Configure ILM for ENTSSO MA
When you install the Enterprise Single Sign-On (SSO) Administration feature (either the full version or the Admin-only version) on a computer running Microsoft Forefront Identity Manager, the ENTSSO Management Agent is automatically installed. This means that when you open FIM, nearly all of the configuration has already been done. The only part missing is the connection information.  
  
 Before starting this procedure, make sure you have the following information available:  
  
-   ENTSSO Server name.  
  
-   UserId and password of the Windows account under which the ENTSSO Management Agent will communicate with the SSO Server.  
  
### To configure the Management Agent within FIM 2007  
  
1.  Open FIM 2007, and open the **Identity Manager**.  
  
2.  Open the **Create Management Agent** dialog box.  
  
3.  Select **Enterprise Single Sign-On** in the list.  
  
     This starts the **Create Management Agent Wizard**.  
  
4.  On the **Configure Connection Information** page, in the **Connect To:** field, enter the name of the SSO Server.  
  
5.  Enter the name of the ENTSSO Management Agent. This name must match the name specified in your ENTSSO.xml file.  
  
6.  In the **User** field, specify the domain account that the ENTSSO Management Agent uses to manage mappings in the SSO Credential Database.  
  
     This account should be either a member of the SSO Affiliate Administrators or SSO Administrators accounts within the SSO System.  
  
7.  In the **Password** field, enter the password for that user.  
  
8.  Click **Next**, accepting the defaults until you reach the **Configure Extensions** page.  
  
9. Near **Connection information** for password extension, click **Settings**.  
  
     The **Connection Settings** dialog box appears.  
  
10. In the **Connect To** box, enter the appropriate account. This account must be the same as the service account for the ENTSSO service running on the computer specified.  
  
11. In the **User** and **Password** fields, enter the user name and password for the account.  
  
12. Click **OK**.  
  
13. In the  **FIM 2007 Create Management Agent**, click **Finish**.  
  
14. While still in the **Identity Manager**, click the **Tools** menu, and then click **Options**.  
  
     The **Options** dialog box appears.  
  
15. Select **Enable metaverse rules extension**.  
  
16. In the **Rules extension name field**, enter **Microsoft.EnterpriseSingleSignOn.ManagementAgent.dll**.  
  
17. Click **OK** and close FIM 2007.  
  
## Example  
 If you already have a Metaverse rules extension that you want to use, you can copy the following code example and edit it appropriately.  
  
```  
// <copyright file=”MVWrapper.cs” company=”Microsoft”>  
// Microsoft Enterprise Single Sign-On  
// Copyright © Microsoft Corporation.  All rights reserved.  
// </copyright>  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
using Microsoft.EnterpriseSingleSignOn.ManagementAgent;  
using Microsoft.MetadirectoryServices;  
using System.Diagnostics;  
  
// This sample code illustrates how to call the Enterprise   
// Single Sign-On (ENTSSO) MV rules   
// extension from your own MV rules extension.  
// A reference is required to   
// Microsoft.EnterpriseSingleSignOn.ManagementAgent.dll.  
  
namespace MVWrapper  
{  
    public class MVWrapper : IMVSynchronization  
    {  
        MVSync mvSync = null;  
  
        public void Initialize()  
        {  
            Debug.WriteLine("IMVSynchronization.Initialize");  
  
            mvSync = new MVSync();  
  
            mvSync.Initialize();  
        }  
  
        public void Provision(MVEntry mventry)  
        {  
            Debug.WriteLine("IMVSynchronization.Provision");  
  
            mvSync.Provision(mventry);  
        }  
  
        public bool ShouldDeleteFromMV(CSEntry csentry, MVEntry mventry)  
        {  
            Debug.WriteLine("IMVSynchronization.ShouldDeleteFromMV");  
  
            return mvSync.ShouldDeleteFromMV(csentry, mventry);  
        }  
  
        public void Terminate()  
        {  
            Debug.WriteLine("IMVSynchronization.Terminate");  
  
            mvSync.Terminate();  
  
            mvSync = null;  
        }  
    }  
}  
  
```  
  
## See Also  
 [How to Use the ENTSSO Management Agent](../esso/how-to-use-the-entsso-management-agent.md)