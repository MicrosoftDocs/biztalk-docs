---
title: "WCF Adapters Security Recommendations | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF adapters, security"
  - "security, WCF adapters"
ms.assetid: bbaaca56-9ad5-4122-a8e9-6e975d308230
caps.latest.revision: 13
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# WCF Adapters Security Recommendations
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the WCF adapters to publish (receive) and consume (send) WCF services. We recommend that you follow these guidelines for securing and deploying the WCF adapters in your environment.  
  
 For more information about the WCF adapters, see [WCF Adapters](../core/wcf-adapters.md). For more information about WCF services, see [Using WCF Services](../core/using-wcf-services.md)s.  
  
## Security Recommendations for All WCF Adapters  
  
-   You can use Enterprise Single Sign-On (SSO) in scenarios where you need to map the content of the front-end user to credentials in a back-end system.  
  
-   Not all services must publish metadata. Leaving metadata publishing disabled reduces the attack surface for your service and lowers the risk of unintentional information disclosure. For more information about security issues related to metadata, see "Security Considerations with Metadata" at [http://go.microsoft.com/fwlink/?LinkId=196671](http://go.microsoft.com/fwlink/?LinkId=196671).  
  
-   Not all combinations of metadata endpoint bindings and service endpoint bindings are valid. In some cases, the binding configurations for a metadata endpoint must be in agreement with the binding configurations of its service endpoint. For example, when metadata is served from the same location as the receive location, the metadata endpoint cannot be configured with a security mode requiring the HTTP transport if the receive location uses a security mode that relies on HTTPS.  
  
    > [!NOTE]
    >  When publishing metadata through the HTTP transport for a service endpoint with the same location but requiring a security mode that relies on the HTTPS transport, in the Web.config file that the BizTalk WCF Publishing Wizard generates, you must set both of the **httpsGetEnabled** and **httpGetEnabled** attributes to **true**.  
  
-   The WCF adapters leverage the security features of Windows Communication Foundation (WCF) to communicate. It is important to understand the capabilities and limitations of WCF in terms of security. For more information about the security features of WCF, see "Windows Communication Foundation Security" at [http://go.microsoft.com/fwlink/?LinkId=87806](http://go.microsoft.com/fwlink/?LinkId=87806).  
  
## Security Recommendations for the Isolated WCF Adapters  
  
- For security recommendations for publishing Web services, see [Enabling Web Services](../core/enabling-web-services.md).  
  
- The isolated WCF adapters such as the WCF-CustomIsolated, WCF-BasicHttp, and WCF-WSHttp adapters leverage the Hypertext Transfer Protocol (HTTP) to send and receive messages to and from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Therefore, you must follow the security recommendations for securing Internet Information Services (IIS).  
  
- When you create an application pool for an isolated WCF receive location, you must configure it to run under an account that is a member of the [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] group for the isolated host running the WCF receive adapter and the Internet Information Services Worker Process group (IIS_WPG group). You must then configure the host instance for the WCF receive adapter to use this account. If you change the account for the IIS_WPG group, you must ensure that you also update the host instance to run under the new account.  
  
## Security Recommendations for the WCF-Custom Adapter  
  
-   If a WCF-Custom receive location happens to use the HTTP kernel-mode driver (HTTP.sys) such as the **httpsTransport** binding element for Secure Sockets Layer (SSL) communications, the receive location must have a certificate registered for each socket (IP address/port combination). Use the HttpCfg.exe tool to bind an SSL certificate to a port on the computer. For more information, see "How To: Configure a Port with An SSL Certificate" at [http://go.microsoft.com/fwlink/?LinkId=86384](http://go.microsoft.com/fwlink/?LinkId=86384).  
  
## Security Recommendations for the WCF-NetMsmq Adapter  
  
-   To use the WCF-NetMsmq adapter, you have to configure MSMQ security settings for the WCF-NetMsmq adapter in the same way as for the [netMsmqBinding](http://go.microsoft.com/fwlink/?LinkId=87813). For more information about how to configure MSMQ security settings for the **netMsmqBinding**, see "Troubleshooting Queued Messaging" at [http://go.microsoft.com/fwlink/?LinkId=87816](http://go.microsoft.com/fwlink/?LinkId=87816).  
  
## WCF Adapters Use the ChainTrust Mode to Validate Certificates.  
  
-   Because the standard WCF receive adapters use the [ChainTrust](http://go.microsoft.com/fwlink/?LinkId=88960) mode to validate the client and service certificates, you must install the CA certificate chain to validate the X.509 certificates. You can use the WCF-Custom or the WCF-CustomIsolated adapter to change this default behavior.  
  
## Security Auditing for the WCF Adapters  
  
- The WCF adapters do not use the WCF security auditing features by default. There are several ways to enable the WCF security auditing features for the WCF adapters. For more information about the WCF security auditing features, see "Auditing Security Events" at [http://go.microsoft.com/fwlink/?LinkId=88975](http://go.microsoft.com/fwlink/?LinkId=88975).  
  
- To use the WCF security auditing features with the WCF-Custom receive adapter, you can configure the **ServiceSecurityAuditBehavior** for the receive locations.  
  
- For the in-process WCF adapters, you can enable the performance counters through the BTSNTSvc.exe.config file. For the isolated WCF adapters, you can enable WCF tracing by modifying the Web.config file that the BizTalk WCF Service Publishing Wizard creates in the Web application folder. To modify BTSNtSvc.exe.config or Web.config, open the configuration file, and then configure WCF tracing, as indicated in the following configuration example:  
  
  > [!NOTE]
  >  The BTSNTSvc.exe.config file is always located in the same directory as the BTSNTSvc.exe file, which is usually [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].  
  > 
  > [!NOTE]
  >  After modifying the BTSNTSvc.exe.config file, you must restart the host instances running the in-process WCF receive locations.  
  
  ```  
  <configuration>  
      <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="ServiceBehaviorConfiguration">  
              <serviceSecurityAudit  
                        auditLogLocation="Application"  
                        suppressAuditFailure="true"  
                        serviceAuthorizationAuditLevel="SuccessOrFailure"  
  messageAuthenticationAuditLevel="SuccessOrFailure" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
        <services>  
          <service name="Microsoft.BizTalk.Adapter.Wcf.Runtime.BizTalkServiceInstance" behaviorConfiguration="ServiceBehaviorConfiguration">  
          </service>  
        </services>        
      </system.serviceModel>  
  </configuration>  
  ```  
  
- You can also use a security-related performance counter such as Security Calls Not Authorized to monitor the WCF adapters. For more information about how to enable the WCF performance counters, see [WCF Adapters Performance Counters](../core/wcf-adapters-performance-counters.md).  
  
## See Also  
 [Planning for Security](../core/planning-for-security.md)