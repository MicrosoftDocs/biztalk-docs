---
title: "Working in Itinerary Designer | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06742cb8-f6d6-46e2-adc0-6be9a3d6a447
caps.latest.revision: 4
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Working in Itinerary Designer
After you create a Microsoft Visual C# project, you can create new itinerary models and add existing itineraries to the project. The following steps describe how to create a new itinerary, add an existing itinerary model, or change the name of an itinerary.  
  
> [!NOTE]
>  Before working with the Itinerary Designer, you must install the Microsoft.Practices.ESB.CORE Windows Installer (.msi file) from the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] install folder. This step installs the required run-time assemblies to the global assembly cache.  
  
## Basic Operations  

#### Create an itinerary  
  
1.  In Solution Explorer, right-click the C# project name, point to **Add**, and then click **New Itinerary**.  
  
2.  In the **Name** box at the bottom of the dialog box, type the name for the itinerary, and then click **Add**.  
  
    > [!NOTE]
    >  The new itinerary is created and displayed in Itinerary Designer, and a corresponding .itinerary file is created and displayed in Solution Explorer.  
  
#### Add an existing itinerary to the project
  
1.  In Solution explorer, right click the C# project name, point to **Add**, and then click **Existing Item**.  
  
2.  In the **Add Existing Item** dialog box, navigate to the directory that contains the itinerary, click the itinerary, and then click **Add**.  
  
    > [!NOTE]
    >  The itinerary is added to the project.  
  
#### Change the name of an itinerary  
  
1.  In Solution Explorer, right-click the .itinerary file you want to rename, and then click **Rename**.  
  
2.  Type the new file name, and then press ENTER.  
  
#### Save an itinerary  
  
On the **File** menu, click **Save \<itinerary name\>**.  
  
> [!NOTE]
>  Itinerary files are saved as DSL models in corresponding XML format.  
  
#### Set itinerary export properties  
  
1. In the Properties window, type a **Name** property.  
  
2. In the Properties window, type a **Version** property.  
  
3. In the Properties window, specify the **Is Request Response** property using the drop-down list. Set this property to **true** if the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] client application communicates with an on-ramp using request-response message exchange pattern.  
  
4. In the Properties window, set the **Export Mode** property to **Default** or **Strict**.  
  
   > [!NOTE]
   >  When creating [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itineraries using the Itinerary Designer, the **Export Mode** property can be used to define where the service will execute. Setting the **Export Mode** property to **Strict** ensures that the itinerary service executes in its prescribed container; in this case, each itinerary service in the XML itinerary has a stage property that specifies the pipeline in which the service executes. If this property is set to **Default**, an itinerary compatible with Microsoft ESB is created, with no stage specified, and the itinerary service executes in the order prescribed, but not necessarily in the pipeline stage desired.  
  
#### Export an itinerary to a file  
  
1.  In the Properties window, click **XML Itinerary Exporter** in the **Model Exporter** drop-down list.  
  
2.  In the Properties window, set the **Itinerary XML file** property to a new value.  
  
#### Export an itinerary to a database  
  
1. In the Properties window, click **Database Itinerary Exporter** in the **Model Exporter** drop-down list.  
  
2. In the Properties window, set the **Itinerary Database** property connection string to point to the itinerary database.  
  
3. In the Properties window, set the **Itinerary Status** property to **Published** or **Deployed**.  
  
   > [!NOTE]
   >  When an itinerary is exported to a database with **Itinerary Status** set to **Published**, the itinerary will not become effective for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] run time until after the property is set to **Deployed**.  
  
## Security Operations  
 By using the Itinerary Designer, you can protect sensitive information, such as passwords and other credentials stored in a [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary, by encrypting this information using X.509 certificates.  
  
#### Select the X.509 certificate for an itinerary  
  
1.  In the Itinerary Designer Properties window, expand the **Encryption Certificate** property, and then click the **Store Location** drop-down list, and select the **CurrentUser** or **LocalMachine**. This associates the X.509 certificate store with the current user or the local computer.  
  
2.  In the Properties window, click the **Store Name** drop-down list and select the value which corresponds to your certificate store.  
  
3.  In the Properties window, click the ellipsis button (...) next to the Encryption Certificate property, and then select the **X.509 certificate** in the **Select Certificate** dialog box.  
  
#### Remove the X.509 certificate from an itinerary  
  
- In the Itinerary Designer Properties window, expand the **Encryption Certificate** property, and then set the **Store Location** property to a different value. This disassociates the old certificate with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary model.  
  
#### Disable the X.509 certificate validation  
  
In the Registry Editor, go to the subkey **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BizTalk ESB Toolkit\2.0\Designer**, and then set the **RequireX509Certificate** property value to **false**.  
  
> [!NOTE]
>  If you installed the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] on an operating system that has 64-bit support, the subkey is **HKEY_LOCAL_MACHINE\SOFTWARE\SysWOW64\Microsoft\BizTalk ESB Toolkit\2.0\Designer**.