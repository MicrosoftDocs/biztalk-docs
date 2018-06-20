---
title: "Step 2: Deploy the Web Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cb775a89-2e2d-43e5-94ae-f75c1756dbd7
caps.latest.revision: 16
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 2: Deploy the Web Project
![Step 2 of 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **Time to complete:** 5 minutes  
  
 In this step you will publish the Web project generated in [Step 1: Use the Adapter Service Development Wizard to Create the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md) to Internet Information Services (IIS).  
  
## Prerequisites  
 To complete this step, you should have completed [Step 1: Use the Adapter Service Development Wizard to Create the Web Project](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md). Your Web server must also have an SSL certificate installed to enable HTTPS communication.  
  
## Compile and deploy the Web project  
  
1. In Visual Studio, load the EchoWeb project created previously.  
  
2. Open a Visual Studio command prompt.  
  
3. At the command prompt, from the C:\tutorials\echoweb folder, type the following command, and then press ENTER:  
  
    **sn /k EchoWebKey.snk**  
  
    A confirmation message, **Key pair written to EchoWebKey.snk**, displays on the command line.  
  
4. Close the command prompt.  
  
5. In **Solution Explorer**, right click the EchoWeb project, and then select **Publish Web Site**.  
  
6. In the **Publish Web Site** dialog box, for **Target location**, enter **http://machinename/EchoWeb**. Select **Allow this precompiled site to be updatable**, **Use fixed naming and single page assemblies**, and **Enable strong naming on precompiled assemblies**. In the **Key file location** field, click the ellipsis **(…)** button, select the EchoWebKey.snk file created previously, and then click **OK**.  
  
7. To verify that the Web site was correctly created, start Internet Explorer, enter  **"<http://localhost/EchoWeb/EchoOutboundContract.svc>"** in the address bar, and then press ENTER. A Web page that describes the EchoOutboundContractClient should appear.  
  
## What did I just do?  
 You have just published your Web project to IIS.  
  
## Next Steps  
 Now that you have compiled and deployed the project, you can proceed to [Step 3: Create an Application Definition File](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)  
  
## See Also  
 [Tutorial 3: Hosting the Echo Adapter in IIS](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-3-hosting-the-echo-adapter-in-iis.md)