---
description: "Learn more about: How to Execute Policies"
title: "How to Execute Policies"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# How to Execute Policies
The following sample code shows how to invoke the rule engine to execute a policy programmatically by using the **Policy** class in the **Microsoft.RuleEngine** assembly.  
  
```  
xmlDocument = IncomingXMLMessage.XMLCase;  
typedXmlDocument = new Microsoft.RuleEngine.TypedXmlDocument("Microsoft.Samples.BizTalk.LoansProcessor.Case",xmlDocument);  
policy = new Microsoft.RuleEngine.Policy("LoanProcessing");  
policy.Execute(typedXmlDocument);  
OutgoingXMLMessage.XMLCase = xmlDocument;  
policy.Dispose();  
```  
  
## Important methods of the Policy class  
 Here are the important methods of the Policy class and their descriptions.  
  
|Method in the Policy class|Description|  
|--------------------------------|-----------------|  
|Execute|Adds the specified short-term facts into the rule engine's working memory and executes the policy using Match-Conflict Resolution-Action algorithm. For more information on Match-Conflict Resolution-Action algorithm, see [Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) .|  
|Dispose|Releases the resources used by the rule engine for executing the policy.|  
|Clear|Clears or resets the working memory and the agenda of the rule engine instance created for executing the policy.|  
  
## See Also  
 [Policy.Dispose Method](../core/policy-dispose-method.md)
