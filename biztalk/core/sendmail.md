---
title: "SendMail | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SMTP adapters, examples"
  - "examples, SMTP adapters"
  - "SMTP adapters"
ms.assetid: a0258619-b195-4c8a-8326-77add6e6f04d
caps.latest.revision: 21
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# SendMail
The SendMail sample demonstrates how you can use the Simple Mail Transfer Protocol (SMTP) adapter to send e-mail messages from within a Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration. Dynamic information used to send the e-mail messages is retrieved from an XML message using property promotion functionality.  

## What This Sample Does  
 This sample sends an e-mail message using information obtained from properties promoted out of an incoming XML purchase order (PO) message, using the following sequence of steps:  

1. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration retrieves an input XML PO message.  

2. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration promotes the **PONumber** and **Email** properties for easier access in the future.  

3. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration uses the values of the promoted properties to set the destination address of the dynamic send port and to set the subject of the e-mail message.  

4. The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration sends the constructed e-mail message through the SMTP adapter.  

## Where to Find This Sample  
 \<*Samples Path*\>\AdaptersUsage\SendMail\  

 The following table shows the files in this sample and describes their purpose.  


|                    File(s)                     |                                                                                                         Description                                                                                                         |
|------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AssemblyInfo.cs, SendMail.btproj, SendMail.sln |                                                                         Provides project, solution, and assembly information files for this sample.                                                                         |
|                  Cleanup.bat                   |              Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.               |
|     PropertySchema.xsd, PurchaseOrder.xsd      |                                                           Provides schemas for the properties that you want to promote, and for the XML PO message, respectively.                                                           |
|                ReceiveSend.odx                 |   Provides a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that processes the incoming XML PO message and sends an e-mail message based on information in the message.   |
|               SendMailInput.xml                |                                                                                 Contains a sample input file with a PO specified using XML.                                                                                 |
|                   Setup.bat                    | Builds and initializes this sample. **Note:**  This setup file creates and binds ports, and so on, using a different mechanism than most of the setup files for the SDK samples. It does not require a companion .xml file. |

### To build and initialize this sample  

1. In a command window, navigate to the following folder:  

    \<*Samples Path*\>\AdaptersUsage\SendMail  

2. Run the file Setup.bat, which performs the following actions:  

   - Creates the following input folder for this sample:  

      \<*Samples Path*\>\AdaptersUsage\SendMail\In  

   - Compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample.  

   - Starts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.  

     > [!NOTE]
     >  You should confirm that BizTalk did not report any errors during the build and initialization process before attempting to run this sample.  

     > [!NOTE]
     >  If you choose to open and build the project in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe). Use this key pair to sign the resulting assembly.  

     > [!NOTE]
     >  To undo changes made by Setup.bat, run Cleanup.bat and delete all receive and send ports prefixed with SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail. You must run Cleanup.bat before running Setup.bat a second time.  

3. In the **BizTalk Server Administration** console, locate the receive port prefixed by SendMail_1.0.0.0_Microsoft.Samples.BizTalk.SendMail. Update the receive location for this receive port to point to a directory on your file system to use as the input location.  

4. Using a program such as Notepad, modify the file SendMailInput.xml so that the **Email** element specifies a legitimate e-mail address at which you want to receive the e-mail message generated by this sample.  

5. Click **Start**, point to **Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.  

6. In the **BizTalk Server Administration** console, expand the BizTalk Group tree.  

7. Expand the **Platform Settings** tree in the left pane.  

8. Expand the **Adapters** folder, click the **SMTP** node, and then double-click the SMTP adapter row in the right pane.  

9. In the **SMTP - Adapter Handler Properties** dialog box, click **Properties**.  

10. In the **SMTP Transport Properties** dialog box, on the **Properties** tab, provide appropriate values for the **SMTP server name** and **From (e-mail address)** properties, and then click **OK**.  

     These values will be used to construct the From e-mail address for any e-mail messages sent through this SMTP adapter.  

    > [!NOTE]
    >  If you need to authenticate with your SMTP server, you must ensure that the From e-mail address belongs to the same account that you use for authentication.  

11. Stop and then restart the BizTalk service (BizTalkServerApplication) so that the orchestration will adopt these changes.  

### To run this sample  

1.  Put a copy of the modified file SendMailInput.xml into the input folder.  

2.  Observe the arrival of an e-mail message to the e-mail address you specified in the previous procedure.  

## See Also  
 [Adapter Samples - Usage](../core/adapter-samples-usage.md)