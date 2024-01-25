---
description: "Learn more about: Halt"
title: "Halt"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
---
# Halt
You can use the **Halt** function to halt the current rule engine execution. The **Halt** function takes one parameter of type `Boolean`. If you specify the value for the parameter as `true`, the rule engine also clears the agenda that contains the pending candidate rules.  
  
 The **Policy.Execute** method is basically a wrapper around the **RuleEngine.Execute** method. It has code similar to the following code:  
  
```  
RuleEngine.Assert(facts);   
RuleEngine.Execute();   
RuleEngine.Retract(facts);  
```  
  
 If you use the **Policy.Execute** method to execute a policy, the rule engine returns control to the **Policy.Execute** method when the **Halt** function is executed. The **Policy.Execute** method retracts the facts and returns control to the caller. Therefore, the halted policy execution cannot be resumed in this case. The same thing happens when you use the **Call Rules** shape to invoke the policy.  
  
 However, if you use the **RuleEngine.Execute** method directly to execute the policy, you can resume the halted policy execution with the next pending rule firing by simply calling **RuleEngine.Execute** again (provided you did not retract any objects needed between the two calls). The sample code for resuming the halted policy execution is as follows:  
  
```  
//assert facts into working memory of the rule engine instance  
RuleEngine.Assert(facts);   
//execute the policy  
RuleEngine.Execute();   
//policy invokes the Halt method when executing actions.   
//control is returned to here when the Halt method is invoked  
  
//when engine is halted do the following  
//Add your code here  
  
//To resume the halted rule engine execution  
RuleEngine.Execute();  
//retract or remove facts frm the working memory of the rule engine  
RuleEngine.Retract(facts);  
```  
  
 Note that the **Policy.Execute** method caches the rule engine instances for better performance. When you use the **RuleEngine.Execute** method directly, the rule engine instances are not cached.  
  
## See Also  
 [Engine Control Functions](../core/engine-control-functions.md)
