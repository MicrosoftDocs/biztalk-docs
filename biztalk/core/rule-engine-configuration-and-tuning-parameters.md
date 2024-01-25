---
description: "Learn more about: Rule Engine Configuration and Tuning Parameters"
title: "Rule Engine Configuration and Tuning Parameters"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Rule Engine Configuration and Tuning Parameters
The following table contains a list of registry keys that may be useful for configuration validation and troubleshooting. These registry keys are stored under **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\BusinessRules\3.0**.  
  
 With the exception of the first three keys listed, these keys are intended to allow products—and not users—to customize the rule engine. All of them are created upon installation; however, no interface is provided to set any of these values.  
  
 The definitions for the table columns are as follows:  
  
-   **Name**. Name of the registry key.  
  
-   **Description**. A brief description about the location or use of the key.  
  
-   **Config default**. Value returned if the key does not exist.  
  
-   **Install default**. Value set by BizTalk Server when installing the rule engine.  
  
|Name|Description|Config default|Install default|  
|----------|-----------------|--------------------|---------------------|  
|InstallPath|Location of BRE files that is used at the configuration time.|(null)|C:\Program Files\Common Files\Microsoft BizTalk (or C:\Program Files (x86)\Common Files\Microsoft BizTalk on a 64-bit operating system)|  
|DatabaseServer|Database server used.|(empty string)|Name of the database server specified during configuration of BRE.|  
|DatabaseName|Name of database to be used.|(empty string)|Name of the database specified during configuration of BRE. Typically, it is BizTalkRuleEngineDb|  
|PubSubAdapterAssembly|Assembly name of pub/sub adapter.|Microsoft.RuleEngine|Microsoft.RuleEngine|  
|PubSubAdapterClass|Class name of pub/sub adapter.|Microsoft.RuleEngine.PubSubAdapter|Microsoft.RuleEngine.PubSubAdapter|  
|DeploymentDriverAssembly|Assembly name of deployment driver.|Microsoft.RuleEngine|Microsoft.BizTalk.RuleEngineExtensions|  
|DeploymentDriverClass|Class name of deployment driver.|Microsoft.RuleEngine.RuleSetDeploymentDriver|Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver|  
|TrackingInterceptorAssembly|Assembly name of tracking interceptor.|(empty string)|Microsoft.BizTalk.RuleEngineExtensions|  
|TrackingInterceptorClass|Class name of tracking interceptor.|(empty string)|Microsoft.BizTalk.RuleEngineExtensions.RuleSetTrackingInterceptor|  
|TranslationTimeout|Maximum time in milliseconds that can be used to translate a ruleset. **Note:**  This can be overridden on a per-ruleset basis by using the RuleSetConfiguration).|60000 (1 minute)|60000|  
|UpdateServiceName|Name of the Update service, used by .NET remoting to locate the service.|RemoteUpdateService|RemoteUpdateService|  
|UpdateServiceHost|Computer hosting the Update service, used by .NET remoting to locate the service. **Note:**  The service currently restricts incoming messages to same machine only.|localhost|localhost|  
|UpdateServicePort|TCP port number used by the Update service, used by .NET remoting to locate the service.|3132|3132|  
|CacheEntries|Maximum number of rulesets cached by the Update service.|32|32|  
|CacheTimeout|Time in seconds for entries to age out of the Update service cache.|3600 (1 hour)|3600|  
|PollingInterval|Time in seconds for the Update service to check SqlRuleStore for updates.|60 (1 minute)|60|  
|SqlTimeout|Timeout value for SQL commands that access the SQL rule store. The value for this key is interpreted as follows:<br /><br /> < 0 - Uses the .NET default value (30 seconds)<br /><br /> = 0 - Unlimited timeout<br /><br /> > 0 - Maximum time for a query before it times out|-1|-1|  
  
 You can also add a registry key named StaticSupport as mentioned in [Invoking Static Members of a Class](../core/invoking-static-members-of-a-class.md).  
  
 The registry settings are global for all applications that host a rule engine instance. You can override these registry settings at an application level by using the application configuration file. For [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] applications, the host application is the BTSNTSvc.exe and the configuration file is the BTSNTSvc.exe.config, which you can find in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation directory.  You need to specify the values for the configuration parameters that you want to override in the application configuration file as show below:  
  
```  
<configuration>  
    <configSections>  
        <section name="Microsoft.RuleEngine" type="System.Configuration.SingleTagSectionHandler" />  
    </configSections>  
    <Microsoft.RuleEngine  
        UpdateServiceHost="localhost"  
        UpdateServicePort="3132"  
        UpdateServiceName="RemoteUpdateService"  
        CacheEntries="32"  
        CacheTimeout="3600"  
        PollingInterval="60"  
        TranslationTimeout="3600"  
        CachePruneInterval="60"  
        DatabaseServer="(localhost)"  
        DatabaseName="BizTalkRuleEngineDb"  
        SqlTimeout="-1"  
        StaticSupport="1"  
    />  
</configuration>  
```
