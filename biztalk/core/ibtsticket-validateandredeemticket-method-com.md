---
title: "IBTSTicket.ValidateAndRedeemTicket Method (COM) | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.service: "biztalk-server"
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2df4b05-f484-434f-b785-b4ca3be26aa0
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# IBTSTicket.ValidateAndRedeemTicket Method (COM)
Retrieves the credentials associated with a BizTalk message.  
  
## Syntax  
  
```csharp  
  
HRESULT ValidateAndRedeemTicket(  
IUnknown*  
punkMessage  
,  
BSTR  
bstrApplicationName  
,  
LONG  
lFlags  
,  
BSTR*  
pbstrExternalUserName  
,  
SAFEARRAY  
BSTR  
);  
  
```  
  
```cpp  
  
HRESULT ValidateAndRedeemTicket(  
IUnknown*  
punkMessage  
,  
BSTR  
bstrApplicationName  
,  
LONG  
lFlags  
,  
BSTR*  
pbstrExternalUserName  
,  
SAFEARRAY  
BSTR  
);  
  
```  
  
```vb  
  
Function   
Ticket  
.ValidateAndRedeemTicket(  
punkMessage  
As Object,  
bstrApplicationName  
As String,  
lFlags  
As Long,  
pbstrExternalUserName  
As String  
)  
As String  
  
```  
  
#### Parameters  
 *punkMessage*  
 [in]  Specifies the BizTalk Server message.  
  
 *punkMessage*  
 [in]  Specifies the BizTalk Server message.  
  
 *bstrApplicationName*  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are case-insensitive, but case will be preserved. "ABC", "abc" and "AbC" are considered to be the same application.  
  
 *bstrApplicationName*  
 [in]  String that specifies the application name. This parameter cannot be NULL, an empty string, or contain spaces. Application names are case-insensitive, but case will be preserved. "ABC", "abc" and "AbC" are considered to be the same application.  
  
 *lFlags*  
 [in]  Long integer that specifies the flags set. Use the flag [Enterprise Single Sign-On Flags](../core/enterprise-single-sign-on-flags.md) to bypass the credential cache.  
  
 *lFlags*  
 [in]  Long that specifies the flags set. Use the flag [Enterprise Single Sign-On Flags](../core/enterprise-single-sign-on-flags.md) to bypass the credential cache  
  
 *pbstrExternalUserName*  
 [out]  Pointer to a string that specifies the external user name.  
  
 *pbstrExternalUserName*  
 [out]  String that specifies the external user name.  
  
## Return Value  
 This method returns an HRESULT indicating whether it completed successfully. See the Error Values section for more details.  
  
 String array that contains the external credentials.  
  
## Exceptions  
 This method returns an HRESULT containing one of the values in the following table.  
  
 This method indicates errors by setting the Number property of the global Err object to one of the values in the following table:  
  
|||  
|-|-|  
|Value|Description|  
|S_OK|The method succeeded.|  
|E_ACCESSDENIED|Access is denied to the caller.|  
|E_INVALIDARG|An invalid parameter was detected.|  
  
## Remarks  
 This method validates that the sender identity in the Microsoft® BizTalk® Server message matches the user identity in the ticket before redeeming the ticket.  
  
 Because the credentials are returned in clear text by this method, the caller should be careful to clear (overwrite) them as soon as possible after use.  
  
 To access this method, you must be an SSO Administrator, SSO Affiliate Administrator, or an Application Administrator.  
  
## Example  
  
```  
using System;  
using System.Runtime.InteropServices;  
  
namespace Microsoft.BizTalk.PublicInterop  
{  
   // Only include flags that apply to these interfaces  
   // See the ssoflags.idl file  
  
   internal enum BTSTicketFlags  
   {  
      SSO_FLAG_NONE      = 0,  
      SSO_FLAG_REFRESH   = 1  
   };  
  
   [ComImport]  
   [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
   [ClassInterface(ClassInterfaceType.None)]  
   [Guid("8DA848D0-E703-4043-9AF7-C569AC1F4507")]  
   internal class BTSTicket  
   {  
   }  
  
   [ComImport]  
   [InterfaceType(ComInterfaceType.InterfaceIsDual)]  
   [Guid("54596C7F-D343-4F20-BF7A-0722C5DA1F7D")]  
   [CoClass(typeof(BTSTicket))]  
   internal interface IBTSTicket  
   {  
      string[] ValidateAndRedeemTicket(  
         [In, MarshalAs(UnmanagedType.IUnknown)] object message,  
         string applicationName,  
         int flags,  
         out string externalUserName);  
   };  
}  
Imports System  
Imports System.Runtime.InteropServices  
  
Namespace Microsoft.BizTalk.PublicInterop  
  
   ' Only include flags that apply to these interfaces  
   ' See the ssoflags.idl file  
  
   Friend Enum BTSTicketFlags  
      SSO_FLAG_NONE       = 0  
      SSO_FLAG_REFRESH    = 1  
    End Enum  
  
   <ComImport(), TypeLibType(TypeLibTypeFlags.FCanCreate), ClassInterface(ClassInterfaceType.None), Guid("8DA848D0-E703-4043-9AF7-C569AC1F4507")> _  
    Friend Class BTSTicket  
    End Class  
  
   <ComImport(), InterfaceType(ComInterfaceType.InterfaceIsDual), Guid("54596C7F-D343-4F20-BF7A-0722C5DA1F7D"), CoClass(GetType(BTSTicket))> _  
   Friend Interface IBTSTicket  
      Function ValidateAndRedeemTicket( _  
         <InAttribute, MarshalAs(UnmanagedType.IUnknown)> message As Object, _  
         ByVal applicationName As String, _  
         ByVal flags As Integer, _  
         <OutAttribute> externalUserName As String) As String()  
   End Interface  
End Namespace  
```  
  
## Requirements  
 **Platforms:**  [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
## See Also  
 [IBTSTicket Interface (COM)](../core/ibtsticket-interface-com.md)   
 [IBTSTicket Members (COM)](../core/ibtsticket-members-com.md)