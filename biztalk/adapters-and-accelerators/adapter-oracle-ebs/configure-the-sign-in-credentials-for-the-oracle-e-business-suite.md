---
title: "Configure the sign-in credentials for the Oracle E-Business Suite | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 743ced51-706b-4788-b5a8-e0ed8ffb3b48
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the sign-in credentials for the Oracle E-Business Suite
The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]requires the adapter clients to provide client credentials. The adapter uses these credentials to authenticate the user with the Oracle E-Business Suite and to establish a connection.  

 Adapter clients can provide the client credentials both when using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and when using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. When using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], credentials are required to generate the metadata. When using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, credentials are required to perform operations on Oracle E-Business Suite.  

> [!IMPORTANT]
>  You can specify the credentials for the Oracle E-Business Suite or the underlying Oracle database. To connect and generate metadata you can specify any credentials. However, while performing an operation to invoke an Oracle E-Business Suite artifact, you must specify the Oracle E-Business Suite credentials because they are required to set the application context for the Oracle E-Business Suite application you want to invoke. For more information about setting applications context, see [Set Application Context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  

 This section provides information about specifying client credentials in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] and the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

## Specifying Credentials from Visual Studio  
 From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the credentials using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

#### To specify credentials using Consume Adapter Service Add-in  

1.  Right-click your BizTalk project, and then select **Add Generated Items**.  

2.  In the **Add Generated Items** dialog box, do the following:  

    |Use this|To do this|  
    |--------------|----------------|  
    |**Categories**|Click **Consume Adapter Service**.|  
    |**Templates**|Click **Consume Adapter Service**.|  

3.  To start the **Consume Adapter Service** dialog box, click **Add**.  

4.  In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleEBSBinding**, and then click **Configure**.  

5.  In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** list, select **Username** and specify the user name and password to connect to the Oracle E-Business Suite.  

    |Use this|To do this|  
    |--------------|----------------|  
    |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
    |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
    |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
    |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  

6.  Click **OK**.  

#### To specify credentials using Add Adapter Metadata Wizard  

1. Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.  

2. In the **Add Generated Items** dialog box, do the following:  


   |    Use this    |           To do this            |
   |----------------|---------------------------------|
   | **Categories** |     Click **Add Adapter**.      |
   | **Templates**  | Click **Add Adapter Metadata**. |


3. Click **Add**. The [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] opens.  

4. In the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], select **WCF-OracleEBS**. Select the computer on which BizTalk Server is installed and the name of the BizTalk database.  

   > [!IMPORTANT]
   >  If you already have a WCF-OracleEBS port configured in BizTalk, select the port from the Port list.  

5. Click **Next**.  

6. In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleEBSBinding**, and then click **Configure**.  

7. In the **Configure Adapter** dialog box, click the **Security** tab, and from the **Client credential type** list, select **Username** and specify the user name and password to connect to the Oracle E-Business Suite.  


   |                                         Use this                                          |                                                                                                                                               To do this                                                                                                                                                |
   |-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                     **To connect using Oracle database credentials**                      |                                                                          Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.                                                                          |
   |                 **To connect using Oracle E-Business Suite credentials**                  | Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties. |
   | **To connect using Windows Authentication if ClientCredentialType is set to “Database”**  |                                                                                                         Specify a “/” for the **User name** text box and leave the **Password** text box blank.                                                                                                         |
   | **To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”** |                                       Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.                                       |


8. Click **OK**.  

## Specifying Credentials from the BizTalk Server Administration Console  
 From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the credentials as part of the WCF-Custom or WCF-OracleEBS port configuration.  

#### To specify credentials for the WCF-Custom port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**. In the right pane, you can choose to create a port or select an existing port.  

3. In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  

   > [!NOTE]
   >  To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.  

4. In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **oracleEBSBinding**.  

5. If you are creating a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, and do one of the following:  

   -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to Oracle E-Business Suite.  

       |Use this|To do this|  
       |--------------|----------------|  
       |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
       |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  

   -   Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.  

6. If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab, and do one of the following:  

   -   Select **User account** option, and specify the user name and password to connect to Oracle E-Business Suite.  

       |Use this|To do this|  
       |--------------|----------------|  
       |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
       |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  

   -   Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.  

7. Click **OK**.  

#### To specify credentials for the WCF-OracleEBS port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. Add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Adding the Oracle E-Business Suite Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).  

3. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**. In the right pane, you can choose to create a port or select an existing port.  

4. In the port properties dialog box, from the **Type** drop-down list, select **WCF-OracleEBS**, and then click **Configure**.  

   > [!NOTE]
   >  To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.  

5. In the port properties dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **oracleEBSBinding**.  

6. If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab, and do one of the following:  

   -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to Oracle E-Business Suite.  

       |Use this|To do this|  
       |--------------|----------------|  
       |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
       |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  

   -   Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.  

7. If you are creating a receive port, in the transport properties dialog box, click the **Other** tab, and do one of the following:  

   -   Select **User account** option, and specify the user name and password to connect to Oracle E-Business Suite.  

       |Use this|To do this|  
       |--------------|----------------|  
       |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
       |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  

   -   Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.  

8. Click **OK**.  

## See Also  
 [Building blocks to create Oracle E-Business Suite applications](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)   
 [Connecting to Oracle E-Business Suite Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)