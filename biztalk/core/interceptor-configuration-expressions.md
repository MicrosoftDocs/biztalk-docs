---
description: "Learn more about: Interceptor Configuration Expressions"
title: "Interceptor Configuration Expressions | Microsoft Docs"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""

ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2695f509-fece-40b8-aa00-fa3c0c0f19c5
caps.latest.revision: 10
author: "MandiOhlinger"
ms.author: "mandia"
manager: "anneta"
---
# Interceptor Configuration Expressions
The BAM interceptor configuration file uses filter expressions to identify an activity and uses data expressions to construct a data element for storage, use as a correlation ID or continuation token, or similar purpose. Regardless of the purpose, individual expressions are identified in the interceptor configuration file by the `expression` element and contain one or more operations using Reverse Polish Notation, also known as postfix notation.  
  
## About Reverse Polish Notation  
 In Reverse Polish Notation (RPN), operands precede the operator, thereby removing the need to use parentheses as precedence operators. A stack is used to hold values and all operations either push values onto the stack, pop (remove) values from the stack, or perform a combination of pushes and pops to complete an operation.  
  
 For example, if you wanted to evaluate the expression  
  
 `5 + (10 - 2)`  
  
 Converting this to the equivalent RPN results in  
  
 `5 10 2 - +`  
  
 This would be evaluated as follows:  
  
|Input|Operation|Stack|  
|-----------|---------------|-----------|  
|5|Push|5|  
|10|Push|5, 10|  
|2|Push|5, 10, 2|  
|-|Subtract|5, 8|  
|+|Add|13|  
  
 Assuming the RPN system supported the string concatenate operation, you could also evaluate the expression  
  
 `"The quick brown " + "fox " + "jumped over the lazy " + "dog."`  
  
 Converting this to the equivalent RPN notation yields:  
  
 `"The quick brown " "fox " "jumped over the lazy " "dog" + + +`  
  
 This would be evaluated as follows:  
  
|Input|Operation|Stack|  
|-----------|---------------|-----------|  
|"The quick brown"|Push|"The quick brown "|  
|"fox"|Push|"The quick brown ", "fox "|  
|"jumped over the lazy"|Push|"The quick brown ", "fox ", "jumped over the lazy "|  
|"dog."|Push|"The quick brown ", "fox ", "jumped over the lazy ", "dog."|  
|+|Concatenate|"The quick brown ", "fox ", "jumped over the lazy dog."|  
|+|Concatenate|"The quick brown ", "fox jumped over the lazy dog."|  
|+|Concatenate|"The quick brown fox jumped over the lazy dog."|  
  
 As you can see, an arbitrary number of operations can be supported, including comparison, Boolean operations, and custom operations that retrieve values appropriate for the operations in which they participate. Values accumulate on the stack and are pushed and popped according to individual operations.  
  
## Reverse Polish Notation in the Interceptor Configuration File  
 You will write two kinds of expressions in the interceptor configuration file: filter expressions and data expressions. Filter expressions expect the result of the RPN expression to be a Boolean `true` or `false` while data expressions expect a single value on the stack.  
  
### Filter Expressions  
 Filter expressions evaluate to Boolean `true` or `false` and are used to identify a specific event to track in the WF or WFC application. In WF applications, it is common to filter based on activity name and event. For example, you may want to select the **FoodAndDrinksPolicy** activity when it is **Closed**. Using WF operations, you could express the filter as:  
  
 `(GetActivityName = "FoodAndDrinksPolicy") && (GetActivityEvent = "Closed")`  
  
 Converting this to RPN yields:  
  
 `GetActivityName "FoodAndDrinksPolicy" == GetActivityEvent "Closed" == &&`  
  
 Converting this expression to the equivalent expression for the interceptor configuration file results in the following XML:  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 Finally, this expression would be evaluated as follows assuming **GetActivityName** returned "DessertPolicy" and **GetActivityEvent** returned "Closed":  
  
|Input|Operation|Stack|  
|-----------|---------------|-----------|  
||GetActivityName|"DessertPolicy"|  
|"FoodAndDrinksPolicy"|Constant|"DessertPolicy", "FoodAndDrinksPolicy"|  
|Equals|Comparison|False|  
||GetActivityEvent|False, Closed|  
|"Closed"|Constant|False, "Closed", "Closed"|  
|Equals|Comparison|False, True|  
|And|Logical And|False|  
  
 The value left on the stack is Boolean `False`. This will cause the corresponding event to not fire. If the activity name were "FoodAndDrinksPolicy" then it would have evaluated to Boolean `True`.  
  
 You can construct a similar expression (with a similar evaluation) by using the WCF operations `GetEndpointName` and `GetOperationName`.  
  
### Data Expressions  
 Data expressions are used to define a single string data value. A data expression is any expression that is not enclosed by a `Filter` element. Data expressions are used by the `OnEvent` elements `CorrelationID`, `ContinuationToken`, `Reference`, and `Update`.  
  
 It is a common requirement to update the BAM activity database with a labeled time stamp. For example, you might want to capture the time an event starts with a string formatted as "Start: \<EventTime\>". To do this, you need to use an expression similar to the following (where + represents concatenation):  
  
 `"Start: " + GetContextProperty(EventTime)`  
  
 Converting this to RPN yields:  
  
 `"Start: " GetContextProperty(EventTime) +`  
  
 Converting this expression to the equivalent expression for an `Update` element in the interceptor configuration file results in the following XML:  
  
```  
<ic:Update DataItemName="NewOrderCreateTime" Type="NVARCHAR">  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Start:</ic:Argument>  
    </ic:Operation>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:Update>  
```  
  
 The following table shows how this expression would be interpreted if the event time was "12:00 PM".  
  
|Input|Operation|Stack|  
|-----------|---------------|-----------|  
|"Start: "|Constant|"Start: "|  
|GetContextProperty(EventTime)|Push|"Start: ", "2006-09-27T12:00:34.000Z"|  
|Concatenate|Concatenate|"Start: 2006-09-27T12:00:34.000Z"|  
  
 The value used by the update command would be "Start: 2006-09-27T12:00:34.000Z".  
  
> [!NOTE]
>  Do not use the comparison operations "And" or "Equals" in data expressions. If you do, you will receive an error when deploying your interceptor configuration file.  
  
## In This Section  
 [Interceptor Operations](../core/interceptor-operations.md)  
  
## See Also  
 [Structure of an Interceptor Configuration File](../core/structure-of-an-interceptor-configuration-file.md)
