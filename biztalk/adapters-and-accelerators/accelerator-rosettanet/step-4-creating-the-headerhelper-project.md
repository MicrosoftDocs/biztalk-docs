---
title: "Step 4: Creating the HeaderHelper Project | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projects, helper projects"
  - "private process tutorial, creating helper projects"
ms.assetid: 82413537-032a-4368-8d77-d024a7c83b0b
caps.latest.revision: 7
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Step 4: Creating the HeaderHelper Project
In this step, you create a [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] class library. When a private process orchestration receives an incoming message, the HeaderHelper library determines whether a document conversion is required and if it is required, performs that conversion. This lets your orchestration work with different versions of RosettaNet Implementation Framework (RNIF) documents. Additionally, when a 3A2 response message is sent, the HeaderHelper library performs an additional document conversion before transmitting the message.  
  
### To create the HeaderHelper project  
  
1. In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click the Contoso solution, point to **Add**, and then click **New Project**.  
  
2. In the Add New Project dialog box, in the Project Types pane, select **Visual C#**.  
  
3. In the Templates pane, select the **Class Library** template.  
  
4. In the **Name** box, type **HeaderHelper**, and then click **OK** to create the project.  
  
5. In Solution Explorer, right click the **Class1.cs** file in the **HeaderHelper** project, click **Rename**, type **HeaderHelper.cs**, and then press **Enter**.  
  
### To create the Helper class  
  
1.  In Solution Explorer, expand the **HeaderHelper** project, and then double-click the **HeaderHelper.cs** node to open the HeaderHelper source file.  
  
2.  Type the following code into the source file, overwriting all the existing code:  
  
    ```  
    using System;  
    using System.Xml;  
  
    namespace ContosoPriceAndAvailability  
    {  
        public class Helper  
        {  
            static public XmlDocument NormalizeHeader( XmlDocument curPip )  
            {  
                string strInput = curPip.OuterXml;  
                try  
                {  
                    XmlDocument xDoc = new XmlDocument();  
  
                    strInput = strInput.Replace("<!DOCTYPE Pip3A2PriceAndAvailabilityQuery SYSTEM \"3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd\"[]>",String.Empty);  
                    strInput = strInput.Replace("<Pip3A2PriceAndAvailabilityQuery>","<Pip3A2PriceAndAvailabilityQuery xmlns=\"http://schemas.microsoft.com/biztalk/btarn/2004/3A2PriceAndAvailabilityQueryMessageGuideline_v1_3.dtd\">");  
                    strInput = strInput.Replace("xml:",String.Empty);  
                    strInput = strInput.Replace("b:",String.Empty);  
                    strInput = strInput.Replace("lang:",String.Empty);  
                    strInput = strInput.Replace("ns1:",String.Empty);  
  
                    xDoc.LoadXml(strInput);  
  
                    return xDoc;  
                }  
                catch(Exception ex)  
                {  
                    System.Diagnostics.Debug.Write( ex.Message );  
                    throw ex;  
                }  
            }  
  
            static public string ReturnSCWithDocType( XmlDocument xmlDoc )  
            {  
                try  
                {  
                    string sResponse = xmlDoc.InnerXml;  
                    sResponse=sResponse.Replace("ns0:",String.Empty);  
                    xmlDoc.LoadXml(sResponse);  
                    xmlDoc.DocumentElement.RemoveAllAttributes();  
                    sResponse = xmlDoc.InnerXml;  
  
                    sResponse = sResponse.Insert(0,"<!DOCTYPE Pip3A2PriceAndAvailabilityResponse SYSTEM \"3A2PriceAndAvailabilityResponseMessageGuideline_v1_3.dtd\">");  
                    sResponse = sResponse.Replace("ns0:",String.Empty);  
                    sResponse = sResponse.Replace("b:",String.Empty);  
                    sResponse = sResponse.Replace("lang:",String.Empty);  
                    sResponse = sResponse.Replace("ns1:",String.Empty);  
  
                    return sResponse;  
                }  
                catch(Exception ex)  
                {  
                    throw ex;  
                }  
            }  
        }  
    }  
    ```  
  
3.  On the **File** menu, click **Save All**.  
  
### To create a strong named assembly for the HeaderHelper project  
  
1.  In Solution Explorer, right-click the **HeaderHelper** project, and then click **Properties**.  
  
2.  In the HeaderHelper Property Pages dialog box, select **Signing** in the left pane of the HeaderHelp properties pane.  
  
3.  In the right pane, click **Sign the Assembly**.  
  
4.  Click the **Choose a strong name key file** text box, and then select **\<Browse\>** from the drop-down list.  
  
5.  In the Select File dialog box, move to the location of your Contoso assembly, and double-click **FabConPriceAvail.snk**.  
  
6.  On the **File** menu, click **Save All**.  
  
7.  In Solution Explorer, expand the **HeaderHelper** project, expand the **Properties** node, and then double-click the **AssemblyInfo.cs** node to open the AssemblyInfo.cs source file.  
  
8.  In the AssemblyInfo.cs source file, type the following code on the line after the AssemblyCulture attribute:  
  
    ```  
    [assembly: AssemblyKeyFile("../../../FabConPriceAvail.snk")]  
    ```  
  
9. On the **File** menu, click **Save All**.  
  
### To build and deploy the HeaderHelper project  
  
1.  In Solution Explorer, right-click the **HeaderHelper** project, and then click **Build**.  
  
2.  Start **Visual Studio 2012 Command Prompt**.  
  
3.  At the command prompt, move to the location of the **HeaderHelper** project output directory (the \Bin\Debug folder).  
  
4.  At the command prompt, type **gacutil /if HeaderHelper.dll** and press **Enter** to install the **HeaderHelper** assembly into the **Global Assembly Cache**.  
  
## See Also  
 [Step 5: Modifying the Contoso Private Process Orchestration](../../adapters-and-accelerators/accelerator-rosettanet/step-5-modifying-the-contoso-private-process-orchestration.md)