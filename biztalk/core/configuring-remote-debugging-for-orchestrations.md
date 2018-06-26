---
title: "Configuring Remote Debugging for Orchestrations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Microsoft.XLANGs.BizTalk.Client.dll.config, code sample"
  - "BTSNTSvc.exe.config, code sample"
  - "orchestrations, debugging"
  - "building, debugging"
  - "building, code sample"
ms.assetid: 722efaec-d160-48dc-b94b-0733c9904d98
caps.latest.revision: 6
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Configuring Remote Debugging for Orchestrations
You can completely configure remote debugging between client and server. The client configuration is specified in Microsoft.XLANGs.BizTalk.Client.dll.config. The server configuration is specified in BTSNTSvc.exe.config. The following is a listing of the default configuration for each.  
  
## Client (Microsoft.XLANGs.BizTalk.Client.dll.config)  
  
```  
<configuration>  
     <system.runtime.remoting>  
  
 <channelSinkProviders>  
       <clientProviders>  
         <provider id="sspi" type="Microsoft.BizTalk.XLANGs.Client.SecurityClientChannelSinkProvider,Microsoft.XLANGs.BizTalk.Client" securityPackage="negotiate" authenticationLevel="packetPrivacy"/>  
       </clientProviders>  
</channelSinkProviders>  
  
<application>  
<channels>  
    <channel ref="tcp" port="0" name="">  
       <clientProviders>  
             <formatter ref="binary"/>  
             <provider ref="sspi" />  
        </clientProviders>  
       <serverProviders>  
             <formatter ref="binary" typeFilterLevel="Full"/>  
       </serverProviders>  
    </channel>  
</channels>  
</application>  
  </system.runtime.remoting>  
</configuration>  
```  
  
## Server(BTSNTSvc.exe.config)  
  
```  
<?xml version="1.0" ?>  
<configuration>  
    <runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
            <probing privatePath="BizTalk Assemblies;Developer Tools;Tracking;Tracking\interop" />  
        </assemblyBinding>  
    </runtime>  
  
    <system.runtime.remoting>  
  
        <channelSinkProviders>  
            <serverProviders>  
                <provider id="sspi" type="Microsoft.BizTalk.XLANGs.BTXEngine.SecurityServerChannelSinkProvider,Microsoft.XLANGs.BizTalk.Engine" securityPackage="ntlm" authenticationLevel="packetPrivacy" />  
            </serverProviders>  
        </channelSinkProviders>  
  
        <application>  
            <channels>  
                <channel ref="tcp" port="0" name="">  
                <serverProviders>  
                    <provider ref="sspi" />  
                        <formatter ref="binary" typeFilterLevel="Full"/>  
                    </serverProviders>  
                </channel>  
            </channels>  
        </application>  
    </system.runtime.remoting>  
  
</configuration>  
```  
  
## Configurable Parameters  
 The default ensures maximum security configuration. However it is left to the user to change these defaults and these files are ACL'ed since they are in the program files folder.  
  
 The element \<provider/> is optional and if not provided will cause the channels not to be mutually authenticated using the custom sinks. However this is a dangerous option to turn off as it will open up the channels. This can be done for better performance and when security attacks are not a concern.  
  
 The channel element can have property rejectRemoteRequests = true which will enable only local calls and reject remote requests.  
  
 The securityPackage attribute in the \<serverProviders/> element can have any of the following values:  
  
- negotiate  
  
- ntlm  
  
- Kerberos  
  
  The authenticationLevel attribute in the \<serverProviders/> element can have any of the following values:  
  
- packetPrivacy  - the messages will be encrypted/decrypted  
  
- packetIntegrity – the messages will be signed/verified  
  
- call  - the messages will be sent as is  
  
  The ref attribute in the \<channel/> element can be changed to tcp or http. The port and name attribute in the \<channel/> element can be changed as well to explicit values.  
  
  For more information, see .NET Framework Developer's Guide (Channel and formatter configuration properties).  
  
## See Also  
 [Debugging Orchestrations](../core/debugging-orchestrations.md)