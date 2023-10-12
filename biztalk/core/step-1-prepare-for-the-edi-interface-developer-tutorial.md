---
description: "Learn more about: Step 1: Prepare for the EDI Interface Developer Tutorial"
title: "Step 1: Prepare for the EDI Interface Developer Tutorial"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Step 1: Prepare for the EDI Interface Developer Tutorial
![Step 1 of 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-1of9.gif "Step_1of9")  
  
 The EDI Interface Development tutorial is run on a single computer. To prepare for the tutorial, you must install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], as described in [BizTalk Server What's New, Install, Configuration, and Upgrade](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md). You must also add reference to the BizTalk EDI Application.
  
> [!NOTE]
>  For this tutorial to work, it must be run on a platform using IIS 7.5 or IIS 8.  
  
 The files required for the EDI Interface Developer tutorial are located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial folder. The folders and files required for the tutorial are as follows:  
  
|Folder\File|Purpose|  
|------------------|-------------|  
|\SDK\EDI Interface Developer Tutorial\EDI Inbound Processing.sln|The solution file that you use in Visual Studio to create this messaging scenario|  
|\SDK\EDI Interface Developer Tutorial\keyfile.snk|The assembly key file specified for the solution file|  
|\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\SamplePO.txt|The sample message file (version 4010 850) that you use to test the solution|  
|\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\Inbound4010850_to_OrderFile.btm|The BizTalk map that converts the 850 message data into the format required by the Order System.|  
|\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\SendOrderFilePipeline.btp|The send pipeline that processes the test message for sending the message to the order system.|  
|\SDK\EDI Interface Developer Tutorial\ Inbound_EDI\X12_00401_850.xsd|The 850 schema for the test message.|  
\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\fromTHEM|Folder where the inbound 850 message is received from Fabrikam|  
|\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\toOrderSystem|Folder where the outbound 850 message is sent to, representing your Order System back-end application|  
|\SDK\EDI Interface Developer Tutorial\ ProcessEDI_TestLocations\Scenario A\toTHEM_997|Folder where the 997 acknowledgment is sent to, representing Fabrikam|  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  

## To add reference to the BizTalk EDI Application  
  
1. In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the **Applications** node, right-click the application that you want to use for EDI, such as BizTalk Application 1. 
2. Select **Add** > **References**.
3. In the **Add Application Reference** dialog box, select **BizTalk EDI Application**, and then click **OK**.  
  
## Next Steps  
 You build and deploy the Inbound_EDI assembly, as described in [Step 2: Update and Deploy the Tutorial Solution](../core/step-2-update-and-deploy-the-tutorial-solution.md).  
  
## See Also  
 [Tutorial 2: EDI Interface Developer Tutorial](../core/tutorial-2-edi-interface-developer-tutorial.md)
