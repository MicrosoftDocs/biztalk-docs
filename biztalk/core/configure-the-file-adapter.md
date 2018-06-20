---
title: "Configure the File adapter | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "File adapters, configuring"
  - "configuring [File adapters], about configuring File adapters"
  - "configuring [File adapters]"
ms.assetid: 1e0c7e20-80f8-469b-b423-34a2b90f9ec3
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configure the File adapter
How to configure the File adapter, read the security recommendations, and view the required permissions.

You can create a receive location and send port using [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], or programmatically. This topic focuses on the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] console. For the programmatic steps, go to [Create the receive location or send port programmatically](../core/create-the-receive-location-and-send-port-programmatically.md).

> [!IMPORTANT]
> **Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can connect to an Azure file share using the File adapter. The Azure storage account must be mounted on your BizTalk Server. [Get started with Azure File storage on Windows](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files#mount-the-file-share) lists the mounting steps.

## Security recommendations

The File adapter transfers files into and out of BizTalk Server from and to a directory. It is recommended you follow these guidelines for securing and deploying the File adapter in your environment:  

-   Do not open ports to connect to a file share in the perimeter network. You should use the File adapter in environments where there is a high level of trust, such as an intranet. 

-   Set strong discretionary access control lists (DACL) in the receive location's drop directories. For example, you must set read, write, delete files, and delete subfolders and files permissions to the directory from which the file receive location picks up messages, so that only authorized users can drop messages in this location.  

-   When you use the File adapter to pick up critical data, it is recommended to use Internet Protocol Security (IPSec.)  

## Required permissions

Adapter handlers run under the security context of the host instance selected for the adapter handler. The host instance uses the `Logon` property in the ***Host name* - Host Instance Properties** in BizTalk Administration. This `Logon` account must have specific permissions to any folders or shares used by the File adapter.

The host instance user account used by the handler requires the following permissions. A ✔ means the permission is required. A blank entry means the permission is not required.

| Permissions | Receive handler | Send handler |
| --- | --- | --- |
| Full control | ✔ <br/> at the share level (if accessing a file share) |  | 
| Traverse folder / execute file |  | ✔ <br/> at the file level | 
| List folder / read data | ✔ <br/> at the file level | ✔ <br/> at the file level | 
| Read attributes | | ✔ <br/> at the file level | 
| Read extended attributes | | ✔ <br/> at the file level | 
| Create files / write data | | ✔ <br/> at the file level | 
| Create folders / append data | | ✔ <br/> at the file level | 
| Delete subfolders and files | ✔ <br/> at the file level | ✔ <br/> at the file level | 
| Read permissions | | ✔ <br/> at the file level | 
| Change | | ✔ <br/> at the share level (if accessing a file share) |

> [!TIP] 
> At the file level, open the **advanced permissions** on the file or folder to see these permissions.

> [!NOTE] 
> Each host can associate with only one receive handler.  

## Configure the receive location

> [!NOTE]
>  Before completing the following procedure, you must have already added a one-way receive port. See [How to Create a Receive Port](../core/how-to-create-a-receive-port.md).  

1. In the BizTalk Server Administration console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, expand **Applications**, and then expand the application under you want to create a receive location.  

2. In the left pane, click the **Receive Ports** node. Then in the right pane, right-click the receive port that is associated with an existing receive location or that you want to associate with a new receive location, and then click **Properties**.  

3. In the left pane of the **Receive Port Properties** dialog box, select **Receive Locations**, and in the right pane double-click an existing receive location or click **New** to create a new receive location.  

4. In the **Receive Location Properties** dialog box, in the **Transport** section, select **FILE** type from the drop-down list, and then click **Configure** to configure the transport properties for the receive location.  

5. In the **General** tab, do the following:  


   |         Use this         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      To do this                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |    **Receive folder**    | Required. Enter the path to a folder on the file system, the network share, or the Azure file share where the file receive handler reads files. You can enter the path directly in the **Receive folder** text box, or select it from the file system using the **Browse** button. When browsing for the folder, you can also create a new folder using **Make New Folder**.<br /><br /> If using an Azure file storage share, enter `\\yourfilestoragename.file.core.windows.net\yourfilesharename`. <br /><br />**Type:** String <br/><br/>**Note:**  Do not set the **Receive folder** property to a folder that uses the NT Distributed File System with a symbolic link. If you are using an NT Distributed File System, you can only use folders with straight network paths in File adapter receive locations. <br /><br /> For restrictions on this property, see [Restrictions when configuring the File adapter](../core/restrictions-when-configuring-the-file-adapter.md). <br/><br/>**Note:**  The URI for a send port or receive location cannot exceed 256 characters. |
   |      **File mask**       |                                                                                                                                                                                                                                                                                                                                                                         Required. Specify the mask for the files. This mask can contain the standard wildcard value "\*".<br /><br /> **Default value:** \*.xml<br /><br /> **Type:** String<br /><br /> For restrictions on this property, see [Restrictions when configuring the File adapter](../core/restrictions-when-configuring-the-file-adapter.md).                                                                                                                                                                                                                                                                                                                                                                          |
   |    **Public address**    |                                                                                                                                                                                                                                                                                                                                Specify the public address of this location. BizTalk Server exposes this address to external partners.<br /><br /> If this property is not specified, the runtime engine replaces it as:<br /><br /> file://\<*Receive folder*\>/\<*File mask*\><br /><br /> The value for this property requires an adapter prefix.<br /><br /> **Type:** String<br /><br /> **Minimum length:** 0<br /><br /> **Maximum length:** 256                                                                                                                                                                                                                                                                                                                                |
   |     **Retry count**      |                                                                                                                                                                                                                                                                                                                                                                                                                Specify the number of attempts to access the receive location on a network share if it is temporarily unavailable.<br /><br /> **Default value:** 5<br /><br /> **Type:** Long<br /><br /> **Minimum value:** 0<br /><br /> **Maximum value:** MAX_LONG                                                                                                                                                                                                                                                                                                                                                                                                                |
   | **Retry interval (min)** |                                                                                                                                                                                                                                                                                                                                                                                           Specify the retry interval time (in minutes) between attempts to access the receive location on the network share if it is temporarily unavailable.<br /><br /> **Default value:** 5 minutes<br /><br /> **Type:** Long<br /><br /> **Minimum value:** 0<br /><br /> **Maximum value:** MAX_LONG                                                                                                                                                                                                                                                                                                                                                                                            |


6. On the **Authentication** tab, do the following:  


   |                                 Use this                                  |                                                                                                                                                                                                                                                                                   To do this                                                                                                                                                                                                                                                                                    |
   |---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Use these credentials when host does not have access to network share** |                                                                                                                                                                                                                      Required only when using a network share, or an Azure file share. <br /><br /> **Default Value:** False<br /><br /> **Type:** Boolean                                                                                                                                                                                                                      |
   |                               **User name**                               | If using a network share, enter the user name that has access to the share. <br /><br />  If using an Azure file storage share, enter the name of your storage account.<br/><br/>**Type:** String <br /><br />**Note:**  If multiple receive locations mapped to the same network share are configured with alternative credentials, then the same credentials must be used for all of the receive locations. Windows does not allow you to make multiple connections to a shared network server from the same computer if you attempt to use more than one set of credentials. |
   |                               **Password**                                |                                                                                                                                                          If using a network share, enter the password for the account that has access to the network share.<br /><br />  If using an Azure file storage share, enter the storage account access key; which is listed in the Azure portal.<br /><br /> **Type:** String                                                                                                                                                          |


7. In the **Batching** tab, do the following:  

   |Use this|To do this|  
   |--------------|----------------|  
   |**Number of messages in a batch**|Specify the maximum number of messages to be submitted in a batch.<br /><br /> **Default Value:** 5<br /><br /> **Type:** Int<br /><br /> **Minimum value:** 1<br /><br /> **Maximum value:** 256|  
   |**Maximum batch size (in bytes)**|Specify the maximum total bytes for a batch.<br /><br /> **Default Value:** 102400<br /><br /> **Type:** Int<br /><br /> **Minimum value:** 1024<br /><br /> **Maximum value:** MAX_LONG|  

    The File adapter will limit the batch to whichever value is reached first, maximum number of messages or maximum allowed bytes.  

8. Select **OK**.  

9. Enter the appropriate values in the **Receive Location Properties** dialog box to complete the configuration of the receive location, and click **OK** to save settings. For information about the **Receive Locations Properties** dialog box, see [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).  

## Configure the send port

1.  In the BizTalk Server Administration console, create a new send port or double-click an existing send port to modify it. See [How to Create a Send Port](../core/how-to-create-a-send-port2.md). Configure all of the send port options and specify **FILE** for the **Type** option in the **Transport** section of the **General** tab.  

2.  Select the **Configure** button next to **Type**.  

3.  In the **General** tab, do the following:  

    |Use this|To do this|  
    |--------------|----------------|  
    |**Destination Location**|Required. Enter the path to the location on the file system, public share, or the Azure file share to write the output messages. You can enter the path directly in the **Destination Location**, or select it from the file system using the **Browse** button. When browsing for the folder in the **Browse For Folder** dialog box, you can also create a new folder by clicking **Make New Folder**.<br /><br /> If using an Azure file storage share, enter `\\yourfilestoragename.file.core.windows.net\yourfilesharename`.<br /><br /> **Type:** String <br /><br />**Note:**  The URI for a send port or receive location cannot exceed 256 characters.|  
    |**File name**|Specify the name of the file where the File send handler writes the message.<br /><br /> For restrictions on this property, including using macros in the file name, see [Restrictions when configuring the File adapter](../core/restrictions-when-configuring-the-file-adapter.md).|  
    |**Copy mode**|Define the copy mode to use when writing a message to a file. Valid values are:<br /><br /> **Append.** The File send handler opens a file if it exists and appends a message to the end of the file. If the file does not exist, the File send handler creates a new file.<br /><br /> **Overwrite**. The File send handler opens a file if it exists and overwrites its content. If the file does not exist, the File send handler creates a new file.<br /><br /> **Create new**. If a file does not exist, the File send handler creates a new file and writes to it. If the file already exists, the File send handler reports an error and then follows common adapter retry logic for send ports. This is a default copy mode for the File send handler.|  
    |**Allow Cache on write**|Define whether to use file system caching when writing a message to a file.<br /><br /> Valid options are:<br /><br /> **False** Do not use the file system cache.<br /><br /> **True** Use the file system cache.<br /><br /> **Default Value:** False **Important:**  Setting this property to **True** can increase the performance of the File adapter at the risk of potential data loss when there is a loss of power and not all data is written to disk.|  
    |**Use temporary file while writing**|Define whether to write the output file to a temporary file first and then rename the file once the write operation has completed. If this option is enabled then the temporary file will be created with the extension **BTS-WIP**.<br /><br /> Valid options are<br /><br /> **True** The File adapter creates a temporary file when writing to the target folder.<br /><br /> **False** The File adapter does not create a temporary file when writing to the target folder.<br /><br /> **Default Value:** False **Note:**  This option is only available when the **CopyMode** property is set to a value of **Create new**|  

4.  On the **Authentication** tab, do the following:  

    |Use this|To do this|  
    |--------------|----------------|  
    |**Use these credentials when host does not have access to network share**| Required only when using a network share, or an Azure file share. <br /><br /> **Default Value:** False<br /><br /> **Type:** Boolean|  
    |**User name**|If using a network share, enter the user name that has access to the share. <br /><br />  If using an Azure file storage share, enter the name of your storage account.<br /><br /> **Type:** String|  
    |**Password**|If using a network share, enter the password for the account that has access to the network share.<br /><br />  If using an Azure file storage share, enter the storage account access key; which is listed in the Azure portal.<br /><br /> **Type:** String|  

5.  Select **OK** to save your settings.  

## Set the properties for a dynamic send port

 A dynamic send port does not provide any transport configuration options in BizTalk Server Administration console because it is expected that these properties will be provided with the context properties associated with the message. These properties can be set in a custom pipeline or in an orchestration. To set message configuration properties in an orchestration, you can do the following:  

-   Add a **Construct Message** shape to your orchestration.  

-   Configure the **Construct Message** shape to construct a new message. (for example Message_2)  

-   Add a **Message Assignment** shape to the **Construct Message** shape.  

-   Add code to the **Message Assignment** shape to initialize the message that you constructed and to set the appropriate configuration properties for the message. The following code initializes a message named Message_2 that was constructed with a **Construct Message** shape and then sets two configuration properties for the message. In this scenario, Message_1 was originally received by the orchestration:  

    ```  
    Message_2=Message_1;  
    Message_2(FILE.CopyMode)= 0; //0=Append  
    Message_2(FILE.AllowCacheOnWrite)= true;  
    Message_2(FILE.UseTempFileOnWrite)= true;  
    ```  


## Configure the receive or send handler

1.  In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Adapters**.  

2.  In the expanded list of adapters, click **FILE**, in the right pane, right-click the receive or send handler that you want to configure. Select **Properties**.  

3.  In the **Host Name** list, select the host to run the handler.  

4.  Click **OK**.  

## More topics in this section

[Create the File receive location or send port programmatically](../core/create-the-receive-location-and-send-port-programmatically.md)

[File adapter property schema and properties](../core/file-adapter-property-schema-and-properties.md)

[Restrictions when configuring the File adapter](../core/restrictions-when-configuring-the-file-adapter.md)

## See also

 [Ports for the Receive and Send Servers](../core/ports-for-the-receive-and-send-servers.md)   
 [Minimum Security User Rights](../core/minimum-security-user-rights.md)