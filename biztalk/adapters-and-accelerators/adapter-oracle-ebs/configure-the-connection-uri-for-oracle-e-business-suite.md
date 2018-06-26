---
title: "Configure the Connection URI for Oracle E-Business Suite | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2bb02b4-4ad6-4b07-b48a-8f9a47967ffc
caps.latest.revision: 11
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the Connection URI for Oracle E-Business Suite
A connection URI is a connection string that contains parameters required to connect to Oracle E-Business Suite. While using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the URI to connect to Oracle E-Business Suite to generate the metadata. While configuring an orchestration using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the URI to connect to Oracle E-Business Suite to perform operations.  

## Specifying the Connection URI from Visual Studio  
 From [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], you must specify the connection URI using the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] or [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].  

#### To specify the connection URI using Consume Adapter Service Add-in  

1. Right-click your BizTalk project, point to **Add**, and then click **Add Generated Items**.  

2. In the **Add Generated Items** dialog box, do the following:  


   |    Use this    |             To do this             |
   |----------------|------------------------------------|
   | **Categories** | Click **Consume Adapter Service**. |
   | **Templates**  | Click **Consume Adapter Service**. |


3. To start the **Consume Adapter Service** dialog box, click **Add**.  

4. In the **Consume Adapter Service** dialog box, from the **Select a binding** list, select **oracleEBSBinding**, and then click **Configure**.  

5. In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** list, select **Username** and specify the user name and password to connect to the Oracle E-Business Suite.  


   |                                         Use this                                          |                                                                                                                                               To do this                                                                                                                                                |
   |-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                     **To connect using Oracle database credentials**                      |                                                                          Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.                                                                          |
   |                 **To connect using Oracle E-Business Suite credentials**                  | Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties. |
   | **To connect using Windows Authentication if ClientCredentialType is set to “Database”**  |                                                                                                         Specify a “/” for the **User name** text box and leave the **Password** text box blank.                                                                                                         |
   | **To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”** |                                       Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.                                       |


6. Click the **URI Properties** tab, and specify values for different parameters. For more information about the connection URI for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Configure the Connection URI for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).  

7. Click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema. For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  

8. Click **OK**.  

#### To specify the connection URI using Add Adapter Metadata Wizard  

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

7. In the **Configure Adapter** dialog box, click the **Security** tab. From the **Client credential type** list, select **Username** and specify the user name and password to connect to the Oracle E-Business Suite.  


   |                                         Use this                                          |                                                                                                                                               To do this                                                                                                                                                |
   |-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                     **To connect using Oracle database credentials**                      |                                                                          Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.                                                                          |
   |                 **To connect using Oracle E-Business Suite credentials**                  | Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties. |
   | **To connect using Windows Authentication if ClientCredentialType is set to “Database”**  |                                                                                                         Specify a “/” for the **User name** text box and leave the **Password** text box blank.                                                                                                         |
   | **To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”** |                                       Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.                                       |


8. Click the **URI Properties** tab, and specify values for different parameters. For more information about the connection URI for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Configure the Connection URI for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).  

9. Click the **Binding Properties** tab, and specify the binding values, if any, which are required before generating the schema. For more information about binding properties, see [Read about the BizTalk Adapter for Oracle E-Business Suite Binding Properties](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  

    > [!NOTE]
    >  If you selected an existing WCF-OracleEBS send port, you need not specify the binding properties. The binding properties are picked from the send port configuration. However, you may choose to specify the binding properties that are required at design-time, if any. In such case, the new values for binding properties will be used at design-time while generating the metadata. However, at run-time the values specified for binding properties in the send port configuration will be applicable.  

10. Click **OK**.  

## Specifying the Connection URI from the BizTalk Server Administration Console  
 From the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console, you must specify the connection URI as part of the WCF-Custom or WCF-OracleEBS port configuration.  

#### To specify the connection URI for the WCF-Custom port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**. In the right pane, you can choose to create a port or select an existing port.  

3. In the port properties dialog box, from the **Type** drop-down list, select **WCF-Custom**, and then click **Configure**.  

   > [!NOTE]
   >  To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.  

4. In the **WCF-Custom Transport Properties** dialog box, click the **General** tab.  

5. In the **Address (URI)** text box, specify the connection URI to connect to Oracle E-Business Suite. For more information about the connection URI for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Configure the Connection URI for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).  

6. In the **WCF-Custom Transport Properties** dialog box, click the **Binding** tab. From the **Binding Type** drop-down list, select **oracleEBSBinding**.  

7. If you are creating a send port, in the **WCF-Custom Transport Properties** dialog box, click the **Credentials** tab, and do one of the following:  

   -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to Oracle E-Business Suite.  

       |Use this|To do this|  
       |--------------|----------------|  
       |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
       |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  

   -   Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.  

8. If you are creating a receive port, in the **WCF-Custom Transport Properties** dialog box, click the **Other** tab, and do one of the following:  

   -   Select **User account** option, and specify the user name and password to connect to Oracle E-Business Suite.  

       |Use this|To do this|  
       |--------------|----------------|  
       |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
       |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  

   -   Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.  

9. Click **OK**.  

#### To specify the connection URI for the WCF-OracleEBS port  

1. Start the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.  

2. Add the WCF-OracleEBS adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For instructions, see [Adding the Oracle E-Business Suite Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-oracle-ebs/add-the-oracle-ebs-adapter-to-biztalk-server-administration-console.md).  

3. In the console tree, expand **BizTalk Group**, then expand **Applications**, and then expand the application under which you want to create a port, and click **Send Ports** or **Receive Ports**. In the right pane, you can choose to create a port or select an existing port.  

4. In the port properties dialog box, from the **Type** drop-down list, select the WCF-OracleEBS adapter you add earlier, and then click **Configure**.  

   > [!NOTE]
   >  To see the location properties dialog box for a receive port, click the **Receive Location** tab on the left pane of the port properties dialog box, and then click **New**.  

5. In the transport properties dialog box, click the **General** tab.  

6. Click the **Configure** button and provide values for the connection parameters. For more information about the connection URI for the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], see [Configure the Connection URI for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-connection-uri-for-oracle-e-business-suite.md).  

7. In the transport properties dialog box, click the **Binding** tab and specify values for binding properties.  

   > [!NOTE]
   >  The binding properties are displayed based on whether you are configuring a send port or a receive port. For example, binding properties related to notifications are not available while configuring a send port because notifications are inbound operations and require a receive port configuration.  

8. If you are creating a send port, in the transport properties dialog box, click the **Credentials** tab, and do one of the following:  

   -   Select the **Do not use Single Sign-On** option, and specify the user name and password to connect to Oracle E-Business Suite.  

       |Use this|To do this|  
       |--------------|----------------|  
       |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
       |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
       |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  

   -   Select the **Use Single Sign-On** option, and specify an affiliate Enterprise Single Sign-on (SSO) application.  

9. If you are creating a receive port, in the transport properties dialog box, click the **Other** tab, and do one of the following:  

    -   Select **User account** option, and specify the user name and password to connect to Oracle E-Business Suite.  

        |Use this|To do this|  
        |--------------|----------------|  
        |**To connect using Oracle database credentials**|Specify the **ClientCredentialType** binding property to **Database** and specify database credentials for **User name** and **Password** text boxes.|  
        |**To connect using Oracle E-Business Suite credentials**|Specify the **ClientCredentialType** binding property to **EBusiness** and specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. In this case, you must also specify Oracle database credentials for **OracleUserName** and **OraclePassword** binding properties.|  
        |**To connect using Windows Authentication if ClientCredentialType is set to “Database”**|Specify a “/” for the **User name** text box and leave the **Password** text box blank.|  
        |**To connect using Windows Authentication if ClientCredentialType is set to “EBusiness”**|Specify Oracle E-Business Suite credentials for **User name** and **Password** text boxes. You must also specify a “/” for the **OracleUserName** binding property and leave the **OraclePassword** binding property blank.|  

    -   Select **Get credentials from affiliate application** option, and specify an affiliate SSO application.  

10. Click **OK**.  

## See Also  
 [Building blocks to create Oracle E-Business Suite applications](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)   
 [Connecting to Oracle E-Business Suite Using Windows Authentication](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)