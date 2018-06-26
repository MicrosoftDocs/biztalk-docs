---
title: "How to Configure ENTSSO for MIIS Password Sync | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 89438935-37c1-4ac9-9ca2-7af8d9bfd3ae
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Configure ENTSSO for MIIS Password Sync
After configuring the XML file and Microsoft Identity Integration Server (MIIS), the remaining configuration steps take place in the Enterprise Single Sign-On (ENTSSO) system.  
  
### To allow Password Sync from MIIS  
  
1.  In Enterprise Single Sign-On, click the **Servers** node.  
  
2.  Right-click the appropriate server, and click **Properties**.  
  
3.  Click the **Password Sync** tab.  
  
4.  Select **Allow password sync from MIIS**.  
  
5.  Click **OK**.  
  
### To enable Password Sync on the system level  
  
1. In Enterprise Single Sign-On, right-click the **System** node.  
  
2. Click **Properties**.  
  
    The **Properties** dialog box appears.  
  
3. Click the **Options** tab.  
  
4. In the **Enable Password Sync** field, select **From Windows to Adapters**.  
  
    **Additional Configuration**  
  
    Finally, you must configure one of the following:  
  
   - A Password Sync Adapter that accepts Windows Password Sync.  
  
   - Direct Password Sync enabled on at least one application.  
  
     For information about how to do this, refer to your Password Sync documentation.  
  
### To configure the EntSSO MA for MIIS Password Sync  
  
1.  On the ENTSSO Management Agent **Properties** page, click **Configure Extensions**.  
  
2.  In the **Connection information for password extension** field, click **Settings**.  
  
3.  In the **Connect To** field enter the name of the computer that will receive the password changes.  
  
     The computer name must be in the same format that was used when creating the Service Principal Name (SPN) for the ENTSSO service on the domain.  
  
     For example:  
  
     Short format - SPN = ENTSSO/ABCD1411, then enter ABCD1411  
  
4.  Long format - SPN = ENTSSO/ABCD1411.CompanyName.com then enter ABCD1411.CompanyName.com  
  
### Additional Configuration Steps  
  
1.  Click **Start**, point to **All Programs**, point to **Microsoft Identity Integration Server**, and then click **Identity Manager**.  
  
2.  On the **Tools** menu, click **Options**.  
  
3.  Select **Enable Password Synchronization**.  
  
4.  In the **Management Agents view**, select **ADMA**.  
  
5.  In the **Action** pane, select **Properties**.  
  
6.  On the **Properties** page, select **Configure Directory Partitions**, and then select **Enable this partition as a password synchronization source**.  
  
7.  Click **Targets**, and then select ENTSSOMA2 to enable it to receive password changes from MIIS. Deselect ENTSSOMA. Click **OK**, and then click **OK** again.  
  
8.  In the **Management Agent** view, select **ENTSSOMA2**. In the right-hand pane, select **Properties**. On the **Properties** page, click **Configure Extensions**.  
  
9. Confirm that **Enable password management** is selected, and then click **Settings**.  
  
10. In the **Connection Settings** dialog, specify the following:  
  
    -   Connect To: INTSVR1.fabrikam.com  
  
    -   User: fabrikam\ssosvcact  
  
    -   Password: ssosvcact  
  
        > [!NOTE]
        >  This account should match the ENTSSO service account configured on INTSVR1.fabrikam.com.  
  
11. Click **OK**, and then click **OK** again.  
  
12. You can also disable password sync for MIIS. To do this, in **Identity Manager**, click the **Tools** menu, click **Options**, and then deselect **Enable Password Synchronization**.  
  
     The following restrictions will apply:  
  
    -   For Password Sync to function properly, SPN must be configured on the ENTSSO service account that the ENTSSO Management Agent will communicate with.  
  
    -   Communication between MIIS and the ENTSSO server requires Kerberos.  
  
13. When configuring Password Extension in the MIIS connection configuration for the ENTSSO Management Agent, the account specified must match the service account for the ENTSSO server that will receive passwords from MIIS.  
  
## See Also  
 [How to Use the ENTSSO Management Agent](../core/how-to-use-the-entsso-management-agent.md)