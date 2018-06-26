---
title: "Configure a port using the WCF-custom adapter and Oracle E-Business Suite in BizTalk | Microsoft Docs"
description: Use the WCF-Custom adapter to receive or send messages from Oracle EBS in BizTalk Server
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 83d0bb00-934c-40cf-8833-354e7ce7e927
caps.latest.revision: 8
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure a port using the WCF-custom adapter and Oracle E-Business Suite
How to configure WCF-Custom send and receive ports to perform outbound and inbound operations on Oracle E-Business Suite using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
## Prerequisites  
Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group. For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).
  
## Deploy adapters to send messages to Oracle EBS  
 Perform the following steps to configure a WCF-Custom send port for sending messages to Oracle E-Business Suite using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
1. Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
3. Expand the application under which you want to deploy the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
4. Right-click **Send Ports**, point to **New**, and then point to the type of port you want to configure depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and Oracle E-Business Suite.  
  
5. In the **Send Port Properties** dialog box, on the **General** tab, type a name for the send port.  
  
6. From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
7. In the **WCF-Custom Transport Properties** dialog box, do the following:  
  
   1. Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for Oracle E-Business Suite. For more information about the connection URI, see [Create the Oracle E-Business Suite Connection URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).  
  
   2. On the **General** tab, in the **Action** text box, type the action for the operation. See [Messages and Message Schemas for Oracle EBS adapter](messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)) for a list of actions for each operation. For example, the action to invoke the Insert operation on an interface table (FA_BOOKS) under the Asset application is:  
  
      ```  
      InterfaceTables/Insert/OFA/FA/FA_BOOKS  
      ```  
  
   3. Click the **Binding** tab, and from the **Binding Type** list, select **oracleEBSBinding**. You can specify the different binding properties exposed by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
   4. Click the **Credentials** tab, and then do one of the following:  
  
      -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to Oracle E-Business Suite.  
  
          |Use this|To do this|  
          |--------------|----------------|  
          |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
          |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
          |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
          |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  
  
      -   Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.  
  
   5. To return to the **Send Port Properties** dialog box, click **OK**.  
  
8. From the **Send handler** list, select **BizTalkServerApplication**.  
  
9. If you chose **Static One-Way Send Port** in step 4, specify a send pipeline. From the **Send pipeline** list, select the pipeline that corresponds to XMLTransmit.  
  
10. If you chose **Static Solicit-Response Port** in step 4, specify send and receive pipelines.  
  
    1.  From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.  
  
    2.  From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.  
  
11. Click **OK**.  
  
## Deploy adapters to receive messages from Oracle EBS 
 Perform the following steps to configure a WCF-Custom receive port for receiving messages from Oracle E-Business Suite using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
1. Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  
  
2. In the console tree, expand **BizTalk Group**, and then expand **Applications**.  
  
3. Expand the application under which you want to deploy the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
4. Right-click **Receive Ports**, point to **New**, and click **One-way Receive Port** or **Request Response Receive Port**, depending on the mode of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and Oracle E-Business Suite.  
  
5. In the **Receive Port Properties** dialog box, on the **General** tab, type a name for the receive port.  
  
6. On the **Receive Locations** tab, click **New**. The **Receive Location Properties** dialog box appears.  
  
7. In the **Receive Location Properties** dialog box, do the following:  
  
   1.  Specify a name for the receive location.  
  
   2.  From the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  
  
8. In the **WCF-Custom Transport Properties** dialog box, do the following:  
  
   1. Click the **General** tab, and in the **Address (URI)** field, specify the connection URI for Oracle E-Business Suite. For more information about the connection URI, see [Create the Oracle E-Business Suite Connection URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).  
  
   2. Click the **Binding** tab, and from the **Binding Type** drop-down list, select **oracleEBSBinding**. You can specify the different binding properties exposed by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
   3. Click the **Behavior** tab to set the transaction isolation level. For more information about setting transaction isolation level, see [Configure Transaction Isolation Level and Transaction Timeout with E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md).  
  
   4. Click the **Others** tab, and do one of the following:  
  
      -   Select **User account** option, and specify the user name and password to connect to Oracle E-Business Suite.  
  
          |Use this|To do this|  
          |--------------|----------------|  
          |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
          |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
          |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
          |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  
  
      -   Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.  
  
   5. To return to the **Receive Location Properties** dialog box, click **OK**.  
  
9. From the **Receive handler** drop-down list, select **BizTalkServerApplication**.  
  
10. If you chose **One-way Receive Port** in step 4, specify a receive pipeline. From the **Receive pipeline** list, select the pipeline corresponding to XMLReceive.  
  
11. If you chose **Request Response Receive Port** in step 4, specify send and receive pipelines.  
  
    1.  From the **Receive pipeline** drop-down list, select the pipeline that corresponds to XMLReceive.  
  
    2.  From the **Send pipeline** drop-down list, select the pipeline that corresponds to XMLTransmit.  
  
12. In the **Receive Location Properties** dialog box, click **OK**.  
  
13. In the **Receive Port Properties** dialog box, click **OK**.  
  
## See Also  
 [Manually Configuring a Physical Port Binding to the Oracle E-Business Adapter](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md)   
 [Connecting to Oracle E-Business Suite Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)