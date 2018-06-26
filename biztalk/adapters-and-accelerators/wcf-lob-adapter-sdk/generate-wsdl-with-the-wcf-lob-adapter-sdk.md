---
title: "Generate WSDL with the WCF LOB Adapter SDK | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f701d78d-b3ad-4f75-b814-e5b1f1319fb9
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Generate WSDL with the WCF LOB Adapter SDK
During development of an adapter, or when the metadata that is returned from the LOB system changes, it is often useful to view the Web Services Description Language (WSDL) that is returned from the adapter to verify that the metadata for your operations is generated correctly. There are several methods to generate the WSDL. This topic provides information about using svcutil.exe and the Metadata Search Browse control.  

  
## Use svcutil.exe  
 Svcutil.exe is a command-line utility shipped with the Windows SDK that accepts a URL and optional switches, and returns WSDL. The following is an example of using svcutil.exe to return the WSDL of the Echo Adapter:  
  
 ```
 Svcutil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False” /target:metadata
 ```
  
 This saves the metadata as Microsoft.Adapters.Samples.Echov2.wsdl. If your adapter has many operations, you can choose to return only the desired operations by using ‘op=OperationName’ as part of the URI. The following is an example of using this to return only the EchoStrings information:  
  
```  
SvcUtil.exe “echov2://lobhostname/lobapplication?enableAuthentication=False&op=Echo/EchoStrings” /target:metadata  
```  
  
## Use the Metadata Search Browse Control  
 The Metadata Search Browse control is a Windows control that is used in the wizards included in [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. You can add this control to any Windows Forms project in Visual Studio, and use it to select your adapter, the desired operations, and then generate the WSDL.  
  
1. Open a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] command prompt.  
  
2. On the **File** menu, select **New**, and then click **Project**.  
  
3. In the **New Project** dialog box, select **Windows Application** from **Templates**. Enter a project name, and then click **OK**.  
  
4. Open the **Toolbox**, expand **Common Controls**, right-click the **Toolbox**, and then click **Choose Items**.  
  
5. In the **Choose Toolbox Items** dialog box, find **MetadataUserControl** on the **.NET Framework Components** tab, select the check box beside this item, and then click **OK**.  
  
6. From the Toolbox, drag the MetadataUserControl to Form1. You may need to resize the form to see the entire control. You should be able to run the project now and verify that the control is functional, allowing you to select an adapter and operations.  
  
7. To generate WSDL by using this control, you must add code to your form to call the **GetWsdl** method of this control. The following example demonstrates how to call **GetWsdl** and save the data to file:  
  
   ```csharp  
   private void button1_Click(object sender, EventArgs e)  
   {  
      ServiceDescription sd = mdUserControl.GetWsdl();  
      FileStream myFileStream = new FileStream(tbWsdlFileName.Text, FileMode.OpenOrCreate, FileAccess.Write);  
      StreamWriter myStreamWriter = new StreamWriter(myFileStream);  
      sd.Write(myStreamWriter);  
      myStreamWriter.Flush();  
      myStreamWriter.Close();  
      MessageBox.Show("WSDL file " + tbWsdlFileName.Text + " is created.");  
   }  
  
   ```  
  
## See Also  
 [Troubleshoot adapter created using the WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)