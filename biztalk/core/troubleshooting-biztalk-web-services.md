---
title: "Troubleshooting BizTalk Web Services | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdc86de8-e41e-4878-a66e-e242bcf3b705
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Troubleshooting BizTalk Web Services
This section offers advice on how to identify and resolve common Web service issues.  
  
## General Troubleshooting  
  
### Enabling Web Services Publishing Wizard tracing  
 You can enable tracing to debug the BizTalk Web Services Publishing Wizard by uncommenting the \<add\> node in the BTSWebSvcWiz.exe.config file. For more information about obtaining trace information from the Web Services Publishing Wizard, see [How to Modify BTSWebSvcWiz.exe.config](../core/how-to-modify-btswebsvcwiz-exe-config.md).  
  
### Enabling SOAP message tracing  
 You can enable SOAP message tracing to help you debug the Web services publishing application by using a SOAP extension. For more information about SOAP extensions, see [How to: Implement a SOAP Extension](http://go.microsoft.com/fwlink/?LinkId=62314).  
  
### Using the ThrowDetailedError switch  
 If an error occurs, the Web client receives a generic **SoapException**.  
  
 To debug your published Web service, you can add a switch to the web.config file to control the level of the exception details returned from the published Web service. The switch is **ThrowDetailedError**, and when it is set to **True** the server proxy returns inner exception information to the Web client, enabling you to debug the published Web service.  
  
 The following XML code shows the **ThrowDetailedError** switch that appears in the web.config file under the \<appSettings\> node:  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!WARNING]
>  The inner exception may contain sensitive information. After debugging, you should set the **ThrowDetailedError** switch to **False**.  
  
### Using .NET Framework tracing to capture and log errors in the Web service  
 The .NET Framework **System.Diagnostics.Trace** class can be used to capture and write errors to a text file.  
  
##### To use the System.Diagnostics.Trace class to capture and write errors to a text file  
  
1. Update the web.config file for the Web service to set the TRACE compiler directive to **true** and add a **TraceSwitch** value:  
  
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
   >  If the TRACE compiler directive is not set to **true** then no trace output will be generated. The **TraceSwitch** value can also be set in the calling class but is set here in the web.config file for convenience. Set the **TraceSwitch** value to the appropriate level for development purposes and change the value after development is complete to reduce or inhibit trace output.  
  
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
               Trace.WriteLineIf(WebSvcTraceSwitch.Level = TraceLevel.Warning,"Exception caught: " + e.Message);  
               //Writes to the trace file if specified TraceLevel switch value (in web.config) >= 2  
               TestTracer.Dispose();  
               return "An error occurred in the Web service, please contact the web server administrator.";  
           }  
       }  
   }  
   ```  
  
   > [!NOTE]
   >  This code is a modified version of the HelloWorld Web service that is generated by default when you create a new **ASP.Net Web Service** project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
   > 
   > [!NOTE]
   >  For Windows Vista, Administrator privileges may be required to write the trace output file to the root folder.  
  
3. Rebuild the Web service project. Now, if an error occurs in the **Try** statement the exception is handled in the **Catch** statement and an error is written to the trace output file.  
  
## General Troubleshooting Questions and Answers  
 This section contains a set of questions and answers designed to help you resolve issues with Web services.  
  
### I am receiving errors when consuming a Web service; how can I avoid them?  
 There are many details to consider when consuming a Web service, including the following:  
  
- Avoid using two underscore characters in a parameter name.  
  
- Use of the **any** element or the **anyAttribute** attribute is not supported in Web methods.  
  
- Avoid using XLANG/s keywords as a Web service name or Web method name.  
  
- Avoid using Web method parameter types that are not supported by XLANG/s.  
  
- Do not use element names that are C# keywords or will be invalid as a C# identifier in your schemas.  
  
- Avoid Web Services Description Language (WSDL) files with multiple service or port type definitions.  
  
- Web method parameters must be Xml Serializable.  
  
- Avoid references to consumed Web services that contain multi-rooted schemas.  
  
- Avoid referencing Web services with Web methods expecting generic-based parameters such as nullable parameters.  
  
- The WSDL import element is not supported.  
  
  For more information about these and related considerations, see [Considerations When Consuming Web Services](../core/considerations-when-consuming-web-services.md).  
  
### Why am I getting errors publishing my schema that uses the \<include\> element?  
 Schemas cannot be published if they include circular references (the included schema has an **include** element to the including schema) or have an unresolved **schemaLocation** attribute.  
  
 For more information about the limitation of the **include** element, see [Include Element Binding Support](http://go.microsoft.com/fwlink/?LinkId=62312). The Web Services Publishing Wizard has the same limitations as XSD.exe in .NET Framework 2.0; for more information, see [Import Element Binding Support](http://go.microsoft.com/fwlink/?LinkId=119606).  
  
### Why do I receive errors when publishing my envelope schema?  
 If you have an envelope schema that you are publishing as a Web service, you need to manually modify the generated Web project.  
  
##### To modify the generated Web project for envelope schemas  
  
1.  Open the *\<myWebService\>*.asmx.cs file.  
  
2.  Edit the file and change `bodyTypeAssemblyQualifiedName = <dll.name.version>` to `bodyTypeAssemblyQualifiedName = null`  
  
> [!NOTE]
>  You may need to reset Internet Information Services (IIS) if the previous .dll file is still in the ASP.NET worker process.  
  
### Clients of published Web services may not receive server script time-out errors  
 If Web clients that use .NET Framework are calling a Web service generated with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web Services Publishing Wizard, it is possible that the client cannot receive server script time-out errors because the client request time-out occurs first by default. To resolve this problem you can do one of the following:  
  
-   Increase the client request time-out to a value greater than the server script time-out by increasing the value for the **HttpWebRequest.Timeout** property on the client.  
  
-   Reduce the server script time-out to a value less than the client request time-out by reducing the value for the **HttpServerUtility.ScriptTimeout** property on the server.  
  
## Common Errors  
  
### A Web service returns an HTTP 404 (File Not Found) error  
  
#### Problem  
 Attempts to call a Web service return an HTTP 404 (File Not Found) error.  
  
#### Cause  
 This error can occur if ASP.NET is not installed and/or enabled on the IIS server that hosts the Web service.  
  
#### Resolution  
 Ensure that ASP.NET is installed and enabled. Install the .NET Framework if it is not installed and/or run the aspnet_regiis.exe program located in the %WinDir%\Microsoft.NET\Framework\vXXX.XXX\ folder of the IIS server.  
  
### Date fields are removed from documents processed by a web service generated with the BizTalk Server Web Services Publishing Wizard  
  
#### Problem  
 When you process a document with a web service that was generated with the BizTalk Server Web Services Publishing Wizard, any data contained in a field with a **Data Type** of **xs:date** is removed from the document.  
  
#### Cause  
 This problem can occur if the published orchestration contains a schema with one or more fields that have a **Data Type** of **xs:date** and a **Nillable** property of **True**.  
  
#### Workaround  
 To workaround this problem, locate the fields in the published schema that have a **Data Type** of **xs:date** and verify that the **Nillable** property of these fields is set to **False**.  
  
### A "System.IO.FileNotFoundException" error occurs when a Web service is called  
  
#### Problem  
 When you call a Web service in a Microsoft ASP.NET Web application, you may receive the following error:  
  
 System.IO.FileNotFoundException  
  
#### Cause  
 This error can occur if either of the following conditions is true:  
  
-   The worker process does not have permissions to read to the process Temp directory, and the worker process does not have permissions to write to the process Temp directory.  
  
-   There are compilation errors in the code that XmlSerializer generated.  
  
#### Resolution  
 This error is documented in Microsoft Knowledge Base article [823196](http://support.microsoft.com/kb/823196). Follow the steps in the Resolution section of this Knowledge Base article to resolve this error.