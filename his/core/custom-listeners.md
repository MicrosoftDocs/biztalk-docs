---
title: "Custom Listeners | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6cd5fffa-e5d1-4506-a9cf-fcb1dccf0212
caps.latest.revision: 2
author: "gplarsen"
ms.author: "hisdocs; plarsen"
manager: "anneta"
---
# Custom Listeners
A number of the DRDA Service listeners are replaceable with custom listeners for trace output and package bind output.  
  
## Custom Trace Listener  
 The DRDA Service can trace runtime operations and output the information to the default MsDrdaService.log file and to the standard DrdaAsTextListener. Optionally, you can replace the DrdaAsTextListener with a custom trace listener.  
  
 The DRDA Service supports trace levels to select information to write to the log file and trace listeners. For more information, see Tracing topic in the Troubleshooting book.  
  
 To use the trace listener sample, follow these steps.  
  
1. Using Microsoft Visual Studio 2010, build the sample. You may need to change the reference to the strong name key in the project properties, and the output directory path in the program code.  
  
   ```  
   using System;  
   using System.IO;  
   using Microsoft.HostIntegration.Drda.Common;  
  
   namespace CustomListeners  
   {  
       public class MyTraceListener : BaseDrdaTraceListener  
       {  
           StreamWriter sw = null;  
  
           public bool EnsureWriter()  
           {  
               if (sw == null)  
               {  
                   try  
                   {  
                       System.IO.DirectoryInfo dirInfo = new System.IO.DirectoryInfo(@"c:\temp");  
                       if (!dirInfo.Exists)  
                       {  
                           dirInfo.Create();  
                       }  
                       string fileName = @"c:\temp\MsDrdaService" + DateTime.Now.ToFileTime() + ".log";  
                       sw = new StreamWriter(fileName);  
                       sw.AutoFlush = true;  
                       sw.WriteLine("MsDrdaService custom log. Created on: " + DateTime.Now);  
  
                       return true;  
                   }  
                   catch (Exception ex)  
                   {  
                       System.Console.WriteLine("Failed to create log file. Message:" + ex.Message);  
                       return false;  
                   }  
               }  
               else  
                   return true;  
           }  
  
           #region override IDrdaTraceListener Members  
  
           public override void TraceEvent(System.Diagnostics.TraceEventType type, int id, string msg)  
           {  
               if (EnsureWriter())  
               {  
                   sw.WriteLine(string.Format("[" + type + "][" + id + "]" + msg));  
               }  
           }  
  
           #endregion  
       }  
   }  
  
   ```  
  
    Sample code for a custom trace listener.  
  
2. Using Microsoft Global Assembly Cache tool, install an assembly into the global assembly cache. In the **Visual Studio x64 Win64 Command Prompt (2010)** window, navigate to the **bin\Debug** or **bin\Retail** folder for your custom package bind listener component, type **gacutil /i “\<path>\\<component_name>.dll”**, and then press **Enter**. Using Microsoft Visual Studio 2010, edit the DRDA Service application configuration file. Update the configuration for the custom trace listener.  
  
   ```  
   C:\Windows\system32>gacutil /i <path>\CustomListeners\bin\Debug\CustomListeners.dll  
   Microsoft (R) .NET Global Assembly Cache Utility.  Version 4.0.30319.1  
   Copyright (c) Microsoft Corporation.  All rights reserved.  
   Assembly successfully added to the cache  
   ```  
  
    <em>**Figure 1.</em>* Example command to add custom listener component to GAC.*  
  
3. Using Microsoft Global Assembly Cache tool, read the assembly information from the global assembly cache. In the **Visual Studio x64 Win64 Command Prompt (2010)** window, navigate to the **bin\Debug** or **bin\Retail** folder for your custom package bind listener component, type **gacutil /l “\<path>\\<component_name>.dll”**, and then press **Enter**.  
  
   ```  
   C:\TechReady\DRDA_AS\CustomListeners\bin\Debug>gacutil -l CustomListeners  
   Microsoft (R) .NET Global Assembly Cache Utility.  Version 4.0.30319.1  
   Copyright (c) Microsoft Corporation.  All rights reserved.  
   The Global Assembly Cache contains the following assemblies:  
     CustomListeners, Version=1.0.0.0, Culture=neutral, PublicKeyToken=34013cf74da51d17, processorArchitecture=MSIL  
   Number of items = 2  
   ```  
  
    <em>**Figure 2.</em>* Example command to read custom listener component info from GAC.*  
  
4. Using Microsoft Visual Studio 2010, edit the DRDA Service application configuration file. Update the configuration for the custom trace listener.  
  
   ```  
   <drdaServiceTraceListeners>  
   <drdaServiceTraceListener type="CustomListeners.MyTraceListener, CustomListeners, Version=1.0.0.0, Culture=neutral, PublicKeyToken=34013cf74da51d17, processorArchitecture=MSIL" traceLevel="3"/>  
   </drdaServiceTraceListeners>  
   ```  
  
    <em>**Figure 3.</em>* Sample values for custom trace listener in the MsDrdaService.exe.config.*  
  
## Custom Package Bind Listener  
 To use the custom package bind listener sample, follow these steps.  
  
- Using Microsoft Visual Studio 2010, build the sample. You may need to change the reference to the strong name key in the project properties, and the output directory path in the program code.  
  
  ```  
  using System;  
  using System.Collections.Generic;  
  using System.Xml;  
  using System.Text;  
  using Microsoft.HostIntegration.Drda.Common;  
  
  namespace CustomListeners  
  {  
      public class MyPackageBindListener: IPackageBindListener  
      {  
          #region IPackageBindListener Members  
  
          /// <summary>  
          /// Notify after package is bound with string representation of the xml.  
          /// </summary>  
          /// <param name="packageXMLString">package XML String</param>  
          public void OnPackageBound(string packageXMLString, string rdbNam, string collid)  
          {  
          }  
  
          /// <summary>  
          /// Notify after package is bound with xml document.  
          /// </summary>  
          /// <param name="xmldoc"></param>  
          public void OnPackageBound(XmlDocument xmldoc, string rdbNam, string collid)  
          {  
              try  
              {  
                  System.IO.DirectoryInfo dirInfo = new System.IO.DirectoryInfo(@"c:\temp");  
                  if (!dirInfo.Exists)  
                  {  
                      dirInfo.Create();  
                  }  
                  string fileName = @"c:\temp\PackageXMLFile" + DateTime.Now.ToFileTime() + ".xml";  
                  xmldoc.Save(fileName);  
  
                  //callback.ReloadPackageProcedureTable(null);  
              }  
              catch (Exception ex)  
              {  
                  System.Console.WriteLine("Failed to save xml file. Message:" + ex.Message);  
              }  
          }  
          /// <summary>  
          /// Notify after package is bound with string representation of the xml.  
          /// </summary>  
          public void OnPackageBound(string packageXMLString, string rdbNam, string collid, out List<string> sqlScripts)  
          {  
              sqlScripts = new List<string>();  
          }  
  
          /// <summary>  
          /// Notify after package is bound with xml document.  
          /// </summary>  
          public void OnPackageBound(XmlDocument xmldoc, string rdbNam, string collid, out List<string> sqlScripts)  
          {  
              sqlScripts = new List<string>();  
              string[] sqlScript1 = {  
                                      "/****** Object:  StoredProcedure [dbo].[DBOAREAS_43484152544F4B31_1]    Script Date: 01/06/2012 13:36:23 ******/",  
                                      "SET ANSI_NULLS ON",  
                                      "GO",  
                                      "SET QUOTED_IDENTIFIER ON",  
                                      "GO",  
                                      "CREATE PROCEDURE [dbo].[DBOAREAS_43484152544F4B31_1]  AS  DECLARE C1 CURSOR GLOBAL FOR SELECT * FROM DBO.AREAS",  
                                      "GO",  
                                    };  
              string[] sqlScript2 = {  
                                      "CREATE PROCEDURE [dbo].[DBOAREAS_43484152544F4B31_2]  AS  SELECT * FROM DBO.AREAS"  
                                    };  
  
              sqlScripts.AddRange(sqlScript1);  
              sqlScripts.AddRange(sqlScript2);  
          }  
  
          #endregion  
  
      }  
  }  
  
  ```  
  
   *Sample code for a custom package bind listener.*  
  
- Using Microsoft Global Assembly Cache tool, install an assembly into the global assembly cache. In the **Visual Studio x64 Win64 Command Prompt (2010)** window, navigate to the **bin\Debug** or **bin\Retail** folder for your custom package bind listener component, type **gacutil /i “\<path>\\<component_name>.dll”**, and then press **Enter**.  
  
  ```  
  C:\Windows\system32>gacutil /i <path>\CustomListeners\bin\Debug\CustomListeners.dll  
  Microsoft (R) .NET Global Assembly Cache Utility.  Version 4.0.30319.1  
  Copyright (c) Microsoft Corporation.  All rights reserved.  
  Assembly successfully added to the cache  
  ```  
  
   <em>**Figure 4.</em>* Example command to add custom listener component to GAC.*  
  
- Using Microsoft Global Assembly Cache tool, read the assembly information from the global assembly cache. In the **Visual Studio x64 Win64 Command Prompt (2010)** window, navigate to the **bin\Debug** or **bin\Retail** folder for your custom package bind listener component, type **gacutil /l “\<path>\\<component_name>.dll”**, and then press **Enter**.  
  
  ```  
  C:\TechReady\DRDA_AS\CustomListeners\bin\Debug>gacutil -l CustomListeners  
  Microsoft (R) .NET Global Assembly Cache Utility.  Version 4.0.30319.1  
  Copyright (c) Microsoft Corporation.  All rights reserved.  
  The Global Assembly Cache contains the following assemblies:  
    CustomListeners, Version=1.0.0.0, Culture=neutral, PublicKeyToken=34013cf74da51d17, processorArchitecture=MSIL  
  Number of items = 2  
  ```  
  
   <em>**Figure 5.</em>* Example command to read custom listener component info from GAC.*  
  
- Using Microsoft Visual Studio 2010, edit the DRDA Service application configuration file. Replace the default package bind listener with the custom package bind listener. The DRDA Service will return a BGNBNDRM (Begin Bind Error Reply Message) to the DRDA AR, if it does not receive a valid response to the callback interface, when the errorWhenNoCallback= value is “true”.  
  
  ```  
  <packageBindListeners>  
  <packageBindListener type="CustomListeners.MyPackageBindListener, CustomListeners, Version=1.0.0.0, Culture=neutral, PublicKeyToken=34013cf74da51d17, processorArchitecture=MSIL" errorWhenNoCallback="true"/>  
  </packageBindListeners>  
  ```  
  
   <em>**Figure 6.</em>* Example values for custom package bind listener in the DRDA Service application configuration file.*