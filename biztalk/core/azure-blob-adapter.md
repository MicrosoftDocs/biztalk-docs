---
title: "Use the Azure Blob adapter | Microsoft Docs"
description: Send and receive messages using the Azure Blob adapter in BizTalk Server
author: "Elvis-Shi"
ms.author: "elsh"
manager: "dougeby"
ms.date: "12/23/2019"
ms.topic: conceptual
ms.prod: biztalk-server

# optional metadata

#ROBOTS:

ms.reviewer: 
ms.suite:
ms.tgt_pltfrm:
ms.assetid: 
ms.custom: "biztalk-2020"

---

# Azure Blob storage adapter in BizTalk

## Overview
**Starting with BizTalk Server 2020**, you can send and receive messages between BizTalk Server and Azure Blob storage. 

Azure Blob storage is Microsoft's object storage solution for the cloud, which is optimized for storing massive amounts of unstructured data. [What is Azure Blob storage?](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview) provides more details.

## Prerequisites

* Create an [Azure blob storage account](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)  with a container

## Send messages to Azure Blob storage

1.  In the BizTalk Server Administration console, right-click **Send Ports**, select **New**, and select **Static One-way send port**.

    [Create a Send Port](../core/how-to-create-a-send-port2.md) provides some guidance.

2. Enter a **Name**. In **Transport**, set the **Type** to **AzureBlobStorage**, and click **Configure** button. 

3. Configure the **Azure Account** properties.
    >[!TIP]
    > Adapter configuration dialog can auto-populate the Azure resources after signing into the relevant Azure subscription. This makes the configuration easier. Signing into the Azure subscription is not mandatory. 

    |Use this|To do this|  
    |---|---|  
    | **Sign-in** | Sign into your Azure account |
    | **Subscription** | Select the subscription that has your Azure storage account |
    | **Resource group** | Select the resource group that has your Azure storage account |


4. Configure the **General** properties.

    |Use this|To do this|  
    |---|---|  
    | **Storage Authentication** | Select an authentication method. <ul><li>**Shared access signature** is selected by default. You must input the Shared Access Signature connection string in the **Connection string** field.</li> <li>If you are using **Access keys** as the authentication method, a collection of storage accounts will be populated in the **Account** drop-down list. Once you select the storage account, the **Connection string** field will be automatically populated with the primary access key (also known as **key1**). </li></ul><br />The following links are good resources to help you decide which authentication method is right for your scenario:<br/><br/>[Authorizing access to data in Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-auth)<br/>[Using shared access signatures (SAS)](https://docs.microsoft.com/azure/storage/common/storage-dotnet-shared-access-signature-part-1) |
    | **Blob container name** | Select the name of your Blob container from the drop-down list. The list is auto-populated after the **Connection string** is specified. |
    | **Blob name** | Specify the name of the blob to be used by the adapter. Macros can be used in Blob name. For available Macros please refer to [Using macros in file names](restrictions-when-configuring-the-file-adapter.md#using-macros-in-file-names). |
    | **Namespace for blob metadata** | Specify namespace as a filter. Context properties of the message will be written to blob metadata if the namespace of the property matches this field. |

    When finished, your properties look similar to the following: 

    ![Send General properties](../core/media/BlobAdapter-send-General.png)

5. Configure the **Advanced** properties:

    |Use this|To do this|  
    |---|---|  
    |**Blob type**| Specify **Blob type** to be used, visit [blob types](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blobs-introduction) for more information. |
    |**Write mode**| Use this setting to specify adapter behavior when given **Blob name** already exists. 	<ul><li>**Create new**: Adapter will always try to create a new blob. In case a blob with the same name already exists, the BizTalk message will be suspended. </li><li>**Overwrite**: Adapter will overwrite if blob with given name already exists, metadata will be overwritten as well.</li><li>**Append**: Adapter will append message body to existing blob if blob already exists, metadata will not change.</li></ul>|  

6. Select **OK** to save your changes. 


### Test your send port

You can use a simple File receive port and location to send messages to your Azure Blob storage. 

1. Create a receive port named "FileReceivePort" using the File adapter. Within your receive location,  set the **Receive folder** to **C:\Temp\In\\**, and set the file mask to **\*.xml**.
2. In your Azure Blob storage send port properties, set the **Filters** to `BTS.ReceivePortName == FileReceivePort`.
3. Paste the following into a text editor, and save the file as **AzureBlobStorageMessage.xml**. This is your sample message. 

    ```xml
    <Data>
      <DataID>DataID_0</DataID>
      <DataDetails>DataDetails_0</DataDetails>
    </Data>
    ```

4. Start the File receive location and the Azure Blob storage send port.
5. Copy **AzureBlobStorageMessage.xml** sample message into the receive folder (C:\Temp\In\). The send port sends the XML file to the Azure Blob storage. You can verify that by looking into your Azure storage container and examin the new created or updated file.

## Receive messages from Azure Blob storage

1. In the BizTalk Server Administration console, right-click **Receive Ports**, select **New**, and select **One-Way receive port**. 

    [Create a receive port](../core/how-to-create-a-receive-port.md) provides some guidance.

2. Enter a name, and select **Receive Locations**. 

3. Select **New**, and **Name** the receive location. In **Transport**, select **AzureBlobStorage** from the **Type** drop-down list, and then click **Configure** button. 

4. Configure the **Azure Account** properties: 
    >[!TIP]
    > Similiar to send adapter, this is optional. 

    |Use this|To do this|  
    |---|---|  
    | **Sign-in** | Sign into your Azure account |
    | **Subscription** | Select the subscription that has your Azure storage account |
    | **Resource Group** | Select the resource group that has your Azure storage account |

5. Configure the **General** properties: 

    |Use this|To do this|  
    |---|---|  
    | **Storage Authentication** | Select an authentication method. <ul><li>**Shared access signature** is selected by default. You must input the Shared Access Signature connection string in the **Connection string** field.</li> <li>If you are using **Access keys** as the authentication method, a collection of storage accounts will be populated in the **Account** drop-down list. Once you select the storage account, the **Connection string** field will be automatically populated with the primary access key (also known as **key1**). </li></ul><br />The following links are good resources to help you decide which is right for your scenario:<br/><br/>[Authorizing access to data in Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-auth)<br/>[Using shared access signatures (SAS)](https://docs.microsoft.com/azure/storage/common/storage-dotnet-shared-access-signature-part-1) |
    | **Blob container name** | Select the name of your Blob container from the drop-down list. The list is auto-populated after the **Connection string** is specified. |
    | **Blob name prefix** | Specify a prefix where applicable. For example, if "order/" is used for **Blob name prefix**, then receive location will only pick up the files in "order" folder. |
    | **Namespace for blob metadata** | Specify a namespace for adapter to create context properties from custom blob metadata. |
    | **Promote metadata properties** | Specify whether custom blob metadata will be promoted or not. |

    >[!NOTE]
    >All standard blob properties like Blob Uri, Name, BlobType are set as context properties of the BizTalk message with namespace "http://schemas.microsoft.com/BizTalk/Adapter/AzureStorage-properties" by default.

    When finished, your properties look similar to the following: 

    ![Receive General properties](../core/media/BlobAdapter-receive-General.png)

6. Configure the **Advanced** properties: 

    |Use this|To do this|  
    |---|---|  
    | **Polling interval** | Specify the polling interval. |
    | **Maximum messages per batch** | Specify number of messages adapter will batch when submitting to BizTalk.|
    | **Parallel downloads** | Specify maximum number of blobs allowed to be downloaded in parallel.|
    | **Error threshold** | Specify the error threshold. The receive location will be disabled when the number of errors that the receive location encounters reaches this limit.|


7. Select **OK** to save your changes. 

### Test your receive settings

You can use a simple File send port to receive messages from your Azure Blob storage. 

1. Create a send port using the File adapter. Within your send port properties, set the **Destination folder** to **C:\Temp\Out\\**, and set the and **File name** to **%MessageID%.xml**.
2. In your File send port properties, set the **Filters** to  `BTS.ReceivePortName == BlobReceivePort`.
3. Create a receive port named "BlobReceivePort", and create an Azure Blob storage receive location within, then start it.
4. Upload a file to the specified blob container in Azure portal. Do pay attention to matching prefix as you have configured in the adapter. Look for messages in the destination folder (c:\temp\out).

>[!IMPORTANT]
>Azure Blob storage receive adapter will delete the blob after it is submitted into BizTalk MessageBox.

## High Availability of Azure Blob storage adapter

Azure Blob storage receive adapter supports high-availability topologies. Add multiple host instances into same Azure Blob storage adapter receive handler to receive from same blob container simultaneously. Blob leasing is used as a lock to avoid same blob being received by multiple host instances. Accordingly:
- Blobs leased by other processes won't be received by Azure Blob storage adapter.
- Blobs being received by Azure Blob storage adapter can't be updated while in a leased state.

Visit [Pessimistic concurrency for blobs
](https://docs.microsoft.com/en-us/azure/storage/common/storage-concurrency#pessimistic-concurrency-for-blobs) to understand more about Azure blob lease.

Azure Blob storage send adapter like most of other send adapters, provides high availability for the sending host by just having multiple host instances in the same sending host.
