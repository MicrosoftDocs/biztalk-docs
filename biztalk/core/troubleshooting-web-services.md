---
title: "Troubleshooting Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c32bf542-dcc6-4727-b31f-52bb19d4b89d
caps.latest.revision: 24
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting Web Services
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes extensive use of Web services for use with the SOAP adapter and when publishing orchestrations as Web services. This topic provides some steps that you can follow to troubleshoot Web services, as well as some common Web services problems and how to resolve those problems.  
  
## Use .NET Framework tracing to capture and log errors in a Web service  
 The .NET Framework **System.Diagnostics.Trace** class can be used to capture and write errors to a text file.  
  
#### To use the System.Diagnostics.Trace class to capture and write errors to a text file  
  
1. Update the web.config file for the Web service to set the **TRACE** compiler directive to **true** and add a **TraceSwitch** value:  
  
   ```  
   <?xml version="1.0"?>  
   <configuration>  
     <system.codedom>  
       <compilers>  
         <compiler language="c#;cs;csharp"   
                   extension=".cs"   
                   compilerOptions="/d:TRACE"  
                   type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.3500.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" warningLevel="1" />  
         </compilers>  
     </system.codedom>  
     <system.diagnostics>  
       <switches>  
         <add name="WebSvcTraceSwitch" value="2" />  
         <!-- Set to 0, 1, 2, 3, or 4, which corresponds   
         to TraceLevel.Off, TraceLevel.Error, TraceLevel.Warning  
         TraceLevel.Info, and TraceLevel.Verbose. -->  
       </switches>  
     </system.diagnostics>  
   </configuration>  
   ```  
  
   > [!NOTE]
   >  If the **TRACE** compiler directive is not set to **true** then no trace output will be generated. The **TraceSwitch** value can also be set in the calling class, but is set here in the web.config file for convenience. Set the **TraceSwitch** value to the appropriate level for development purposes and change the value after development is complete to reduce or inhibit trace output.  
  
2. Create an instance of the **TraceSwitch** and **TextWriterTraceListener** classes and use a **try…catch** block in the Web service [WebMethod] call to trap and write errors to a trace output file. For example, the following code traps an error that is generated when attempting to set the integer variable s2 to a null instance of the object variable o2:  
  
   ```  
   using System;  
   using System.Web;  
   using System.Web.Services;  
   using System.Web.Services.Protocols;  
   using System.Diagnostics;  
  
   [WebService(Namespace = "http://tempuri.org/")]  
   [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
   public class Service : System.Web.Services.WebService  
   {  
       TraceSwitch WebSvcTraceSwitch = new TraceSwitch("WebSvcTraceSwitch", "Web Service Trace");  
       TextWriterTraceListener TestTracer = new TextWriterTraceListener("C:\\traceout.txt");  
       // Note that by default the local ASPNET account(IIS 5.x) or the   
       // local NETWORK SERVICE account(IIS 6.0) needs write access to  
       // this directory so that the instance of the   
       // TextWriterTraceListener can write to the trace output file.  
   );  
  
       public Service () {  
       }  
  
       [WebMethod]  
       public string HelloWorld()   
       {  
       string h2 = "Hello World";  
       //object o2 = 1;  
       object o2 = null;  
           try  
           {  
               int s2 = (int)o2; //Error if o2 set to null   
               return h2;  
           }  
           catch(Exception e)  
           {  
               Trace.Listeners.Add(TestTracer);  
               Trace.WriteLineIf(WebSvcTraceSwitch.Level = TraceLevel.Warning, "Exception caught: " + e.Message);  
               //Writes to the trace file if specified TraceLevel switch value (in web.config) >= 2  
               TestTracer.Dispose();  
               return "An error occurred in the Web service, please contact the web server administrator.";  
           }  
       }  
   }  
   ```  
  
   > [!NOTE]
   >  This code is a modified version of the default HelloWorld Web service that is generated when you create a new **ASP.Net Web Service** project in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
   > 
   > [!NOTE]
   >  For Windows Vista, Administrator privileges may be required to write the trace output file to the root folder.  
  
3. Rebuild the Web service project. Now, if an error occurs in the **Try** statement the exception is handled in the **Catch** statement and an error is written to the trace output file.  
  
## Known Issues  
  
#### A Web service returns an HTTP 404 (File Not Found) error  
  
##### Problem  
 Attempts to call a Web service return an HTTP 404 (File Not Found) error.  
  
##### Cause  
 This error can occur if ASP.NET is not installed and/or enabled on the IIS server that hosts the Web service.  
  
##### Resolution  
 Ensure that ASP.NET is installed and enabled. Install the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] if it is not installed and/or run the **aspnet_regiis.exe** program located in the %WinDir%\Microsoft.NET\Framework\\*vXXX.XXX*\ folder of the IIS server.  
  
#### A "System.IO.FileNotFoundException" error occurs when a Web service is called  
  
##### Problem  
 When you call a Web service in a Microsoft ASP.NET Web application, you may receive the following error:  
  
 **System.IO.FileNotFoundException**  
  
##### Cause  
 This error can occur if either of the following conditions is true:  
  
-   The worker process does not have permissions to read to the process Temp directory, and the worker process does not have permissions to write to the process Temp directory.  
  
-   There are compilation errors in the code that XmlSerializer generated.  
  
##### Resolution  
 This error is documented in Microsoft Knowledge Base article 823196, [PRB: You Receive a "System.IO.FileNotFoundException" Error When the Client Application Calls a Web Service](http://go.microsoft.com/fwlink/?LinkID=84694)". Follow the steps in the Resolution section of this Knowledge Base article to resolve this error.  
  
#### Date fields are removed from documents processed by a web service generated with the BizTalk Server Web Services Publishing Wizard  
  
##### Problem  
 When you process a document with a web service that was generated with the BizTalk Server Web Services Publishing Wizard, any data contained in a field with a **Data Type** of **xs:date** and a **Nillable** property of **True** is removed from the document.  
  
##### Cause  
 This problem occurs because of a known issue with the XmlSerializer class that is available with the Microsoft .NET Framework Class Library namespace System.Xml.Serialization.  
  
##### Resolution  
 To resolve this issue, install the .NET Framework 2.0 hotfix documented in Microsoft Knowledge Base article 925272, "[FIX: The XML serialization may lose some optional elements in an XSD schema in the .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkId=84696)".  
  
## See Also  
 [Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md)   
 [Guidelines for Resolving Web Services Permissions Problems](../core/guidelines-for-resolving-web-services-permissions-problems.md)