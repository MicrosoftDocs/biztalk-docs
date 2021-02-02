---
description: "Learn more about: How to Deploy Policies"
title: "How to Deploy Policies | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c4ab85a-5a6a-4153-90dc-52e099c0a62c
caps.latest.revision: 9
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# How to Deploy Policies
You can deploy policies programmatically by using the [Microsoft.RuleEngine.RuleSetDeploymentDriver](https://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) class in the **Microsoft.RuleEngine.RuleEngineExtensions** namespace. The following sample code demonstrates how to use the [Microsoft.RuleEngine.RuleSetDeploymentDriver](https://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) class to deploy a policy named **LoanProcessing**:  
  
```  
string policyName = “LoanProcessing”;  
int majorRev = Convert.ToInt16(args[1]);  
int minorRev = Convert.ToInt16(args[2]);  
RuleSetInfo rsi = new RuleSetInfo(policyName,majorRev,minorRev);  
Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
dd.Deploy(rsi);  
```  
  
> [!NOTE]
>  The overloaded constructors of the [Microsoft.RuleEngine.RuleSetDeploymentDriver](https://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) class take the names of the rule store database as a parameter. This allows you to deploy policies to a database that your BizTalk Server environment is not configured to use.  
  
## Using the GetDeploymentDriver Method  
 If you are deploying policies to the database that your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment is configured to use, you do not have to create the **RuleSetDeploymentDriver** object in the code. Instead, you can request the rule engine to create a **RuleSetDeploymentDriver** object for you by invoking the **GetDeploymentDriver** method of the **Configuration** class in the **System.RuleEngine** namespace. The following sample code demonstrates how to invoke the **GetDeploymentDriver** method:  
  
```  
Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
dd = new Microsoft.RuleEngine.Configuration.GetDeploymentDriver();  
```  
  
 The **GetDeploymentDriver** method retrieves the values of the **DeploymentDriverAssembly** and **DeploymentDriverClass** registry keys under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**, and creates an instance of **DeploymentDriverClass**. The following table shows the default values of these two registry keys.  
  
|Registry key|Value|  
|------------------|-----------|  
|DeploymentDriverAssembly|Microsoft.BizTalk.RuleEngineExtensions|  
|DeploymentDriverClass|Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver|  
  
 The **RuleSetDeploymentDriver** class implements the **IRuleSetDeploymentDriver** interface. You can develop your own policy deployment driver by creating a class that implements the **IRuleSetDeploymentDriver** interface and change the values for the registry keys described above as appropriate.
