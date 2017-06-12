---
title: "MSBTS_SendHandler.AdapterName Property (WMI) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b88536d5-9165-498c-8c04-60f79130a461
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# MSBTS_SendHandler.AdapterName Property (WMI)
Contains the name of the adapter used.  
  
 *The syntax shown is language neutral.*  
  
## Syntax  
  
```  
  
string AdapterName;  
```  
  
## Remarks  
 This property is required for instance creation. This property is writeable at instance creation. After instance creation, this property is read-only.  
  
 This property has a **Key** qualifier. Along with **MgmtDbNameOverride** and **MgmtDbServerOverride**, this key forms a compound key for the class.  
  
 The maximum length for this property is 256 characters.  
  
## Example  
 The following example was taken from the SDK\Samples\Admin\WMI\Set Send Handler Property\VBScript\ConfigureSMTP.vbs file.  
  
```vb  
  
Sub ConfigureSMTPSendHandler()  
   'error handling is done by explicity checking the err object rather than using  
   'the VB ON ERROR construct, so set to resume next on error.  
   On Error Resume Next  
  
   'Get the command line arguments entered for the script  
   Dim objArgs: Set objArgs = WScript.Arguments  
  
   'Make sure the expected number of arguments were provided on the command line.  
   'if not, print usage text and exit.  
   If (objArgs.Count <> 2) Then  
      PrintUsage()  
      WScript.Quit 0  
   End If  
  
   Dim objInstSet, objInst, strQuery, strSMTPHostName, strFromAddress, strConfigXML, strAdapterName  
  
   strAdapterName = "SMTP"  
   strSMTPHostName = objArgs(0)  
   strFromAddress = objArgs(1)  
   strConfigXML = "<CustomProps><SMTPHost vt=""8"">" & strSMTPHostName & "</SMTPHost><SMTPAuthenticate vt=""19"">2</SMTPAuthenticate><From vt=""8"">" & strFromAddress & "</From></CustomProps>"  
  
   'set up a WMI query to acquire a list of send handlers with the given Name key value.  
   'This should be a list of zero or one send handlers.  
   strQuery = "SELECT * FROM MSBTS_SendHandler WHERE AdapterName =""" & strAdapterName & """"  
   Set objInstSet = GetObject("Winmgmts:!root\MicrosoftBizTalkServer").ExecQuery(strQuery)  
  
   'Check for error condition before continuing.  
   If Err <> 0   Then  
      PrintWMIErrorThenExit Err.Description, Err.Number  
   End If  
  
   'If send handler found, set configuration information, otherwise print error and end.  
   If objInstSet.Count > 0 then  
      For Each objInst in objInstSet  
         'Set config data for send handler  
         objInst.CustomCfg = strConfigXML  
         If Err <> 0   Then  
            PrintWMIErrorThenExit Err.Description, Err.Number  
         End If  
  
         'Commit the change to the database  
         objInst.Put_(1)  
         If Err <> 0   Then  
            PrintWMIErrorThenExit Err.Description, Err.Number  
         End If  
         WScript.Echo "The Send Handler was successfully configured."  
      Next  
   Else  
      WScript.Echo "No Send Handler was found matching that AdapterName."  
   End If  
End Sub  
  
```  
  
 No sample is provided for C#.  
  
## Requirements  
 **Header:** Declared in BTSWMISchema2K.mof or BTSWMISchemaXP.mof.  
  
 **Namespace:** Included in \root\MicrosoftBizTalkServer.